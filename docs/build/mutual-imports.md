---
title: Importations mutuelles
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: 771ce7506359178c1b8346598e93c30a20329fe8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229790"
---
# <a name="mutual-imports"></a>Importations mutuelles

L’exportation ou l’importation vers un autre fichier exécutable présente des complications lorsque les importations sont mutuelles (ou circulaires). Par exemple, deux dll importent des symboles les uns des autres, comme les fonctions mutuellement récursives.

Le problème avec l’importation mutuelle des fichiers exécutables (généralement des dll) est qu’aucun ne peut être généré sans créer l’autre en premier. Chaque processus de génération requiert, en entrée, une bibliothèque d’importation produite par l’autre processus de génération.

La solution consiste à utiliser l’utilitaire LIB avec l’option/DEF, qui produit une bibliothèque d’importation sans générer le fichier exécutable. À l’aide de cet utilitaire, vous pouvez créer toutes les bibliothèques d’importation dont vous avez besoin, quel que soit le nombre de dll impliquées ou la complexité des dépendances.

La solution générale pour gérer les importations mutuelles est la suivante :

1. Prenez chaque DLL à son tour. (N’importe quel ordre est faisable, bien que certaines commandes soient plus optimales.) Si toutes les bibliothèques d’importation nécessaires existent et sont à jour, exécutez LINK pour générer le fichier exécutable (DLL). Cela génère une bibliothèque d’importation. Dans le cas contraire, exécutez LIB pour générer une bibliothèque d’importation.

   L’exécution de LIB avec l’option/DEF produit un fichier supplémentaire avec un. Extension EXP. La. Le fichier EXP doit être utilisé ultérieurement pour générer le fichier exécutable.

1. Après avoir utilisé LINK ou LIB pour générer toutes les bibliothèques d’importation, revenez en arrière et exécutez LINK pour générer tous les fichiers exécutables qui n’ont pas été générés à l’étape précédente. Notez que le fichier. exp correspondant doit être spécifié sur la ligne de liaison.

   Si vous aviez exécuté l’utilitaire LIB plus tôt pour générer une bibliothèque d’importation pour DLL1, LIB aurait également produit le fichier DLL1. exp. Vous devez utiliser DLL1. exp comme entrée pour la liaison lors de la génération de DLL1.dlll.

L’illustration suivante montre une solution pour deux dll mutuellement importées, DLL1 et DLL2. L’étape 1 consiste à exécuter LIB, avec l’option/DEF définie, sur DLL1. L’étape 1 produit DLL1. lib, une bibliothèque d’importation et DLL1. exp. À l’étape 2, la bibliothèque d’importation est utilisée pour générer DLL2, qui à son tour produit une bibliothèque d’importation pour les symboles DLL2's. L’étape 3 génère DLL1, en utilisant DLL1. exp et DLL2. lib comme entrée. Notez qu’un fichier. exp pour DLL2 n’est pas nécessaire, car LIB n’a pas été utilisé pour générer la bibliothèque d’importation DLL2's.

![Utilisation d'importations mutuelles pour lier deux DLL](media/vc37yj1.gif "Utilisation d'importations mutuelles pour lier deux DLL")<br/>
Liaison de deux dll avec des importations mutuelles

## <a name="limitations-of-_afxext"></a>Limitations de _AFXEXT

Vous pouvez utiliser le `_AFXEXT` symbole de préprocesseur pour vos dll d’extension MFC tant que vous n’avez pas plusieurs couches de DLL d’extension MFC. Si vous avez des dll d’extension MFC qui appellent ou dérivent de classes dans vos propres DLL d’extension MFC, qui dérivent ensuite des classes MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter toute ambiguïté.

Le problème est que dans Win32, vous devez déclarer explicitement toutes les données comme **`__declspec(dllexport)`** si elles étaient exportées à partir d’une dll, et **`__declspec(dllimport)`** si elles doivent être importées à partir d’une dll. Lorsque vous définissez `_AFXEXT` , les en-têtes MFC s’assurent que **AFX_EXT_CLASS** est défini correctement.

Lorsque vous avez plusieurs couches, un symbole tel que **AFX_EXT_CLASS** n’est pas suffisant, car une DLL d’extension MFC peut exporter de nouvelles classes et importer d’autres classes à partir d’une autre DLL d’extension MFC. Pour résoudre ce problème, utilisez un symbole de préprocesseur spécial qui indique que vous générez la DLL elle-même plutôt qu’à l’aide de la DLL. Par exemple, Imaginez deux DLL d’extension MFC, A.dll et B.dll. Chacun exporte des classes dans A. h et B. h, respectivement. B.dll utilise les classes de A.dll. Les fichiers d’en-tête ressemblent à ceci :

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

Lorsque A.dll est créé, il est généré avec `/D A_IMPL` et lorsque B.dll est généré, il est généré avec `/D B_IMPL` . En utilisant des symboles distincts pour chaque DLL, `CExampleB` est exporté et `CExampleA` est importé lors de la génération de B.dll. `CExampleA`est exporté lors de la génération de A.dll et importé en cas d’utilisation par B.dll (ou un autre client).

Ce type de superposition ne peut pas être effectué lors de l’utilisation de la **AFX_EXT_CLASS** et des `_AFXEXT` symboles de préprocesseur intégrés. La technique décrite ci-dessus résout ce problème d’une manière qui ne diffère pas du mécanisme utilisé par la bibliothèque MFC elle-même lors de la création de ses dll d’extension MFC, de base de données et de réseau active.

## <a name="not-exporting-the-entire-class"></a>Non-exportation de la classe entière

Lorsque vous n’exportez pas une classe entière, vous devez vous assurer que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Pour ce faire, vous pouvez redéfinir `AFX_DATA` la macro de votre classe spécifique. Cela doit être fait à chaque fois que vous n’exportez pas la classe entière.

Par exemple :

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

- [Exportez à partir d’une DLL à l’aide de. Fichiers DEF](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide d' __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [L’utilitaire LIB et l’option/DEF](reference/lib-reference.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](importing-and-exporting.md)
