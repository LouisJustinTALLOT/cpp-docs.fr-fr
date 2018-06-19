---
title: Importations mutuelles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b43977f86be409698d8fbdba16fc63d85acfac5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377755"
---
# <a name="mutual-imports"></a>Importations mutuelles
Exporter ou importer dans un autre fichier exécutable présente des complications quand les importations sont mutuelles (ou circulaires). Par exemple, deux DLL importent des symboles de l’autre, semblables aux fonctions mutuellement récursives.  
  
 Le problème avec importer mutuellement des fichiers exécutables (généralement des DLL) est qu’aucune des deux peuvent être générés sans générer d’autres la première. Chaque processus de génération requiert une entrée, une bibliothèque d’importation produite par les autres processus de génération.  
  
 La solution consiste à utiliser l’utilitaire LIB avec l’option /DEF, ce qui produit une bibliothèque d’importation sans générer le fichier exécutable. À l’aide de cet utilitaire, vous pouvez générer toutes les bibliothèques d’importation vous avez besoin, quel que soit le nombre de DLL impliquées et le degré de complexité des dépendances.  
  
 La solution générale pour la gestion des importations mutuelles est :  
  
1.  Traitez chaque DLL à son tour. (N’importe quel ordre est possible, bien que certaines commandes sont plus optimales). Si toutes les bibliothèques d’importation nécessaires existent et sont en cours, exécutez LINK pour générer le fichier exécutable (DLL). Cela génère une bibliothèque d’importation. Sinon, exécutez LIB pour produire une bibliothèque d’importation.  
  
     Exécution de LIB avec l’option /DEF génère un fichier supplémentaire avec un. Extension EXP. La barre d’outils. Exp correspondant doit être utilisée ultérieurement pour générer le fichier exécutable.  
  
2.  Après avoir utilisé LINK ou LIB pour générer toutes les bibliothèques d’importation, revenez en arrière et exécutez LINK pour générer les fichiers exécutables qui n’ont pas été générés à l’étape précédente. Notez que le fichier .exp correspondant doit être spécifié sur la ligne de liaison.  
  
     Si vous aviez exécuté l’utilitaire LIB plus tôt pour générer une bibliothèque d’importation pour DLL1, LIB aurait également généré le fichier DLL1.exp. Vous devez utiliser DLL1.exp comme entrée de LINK lors de la génération de DLL1.exp.  
  
 L’illustration suivante montre une solution pour deux DLL importent mutuellement, DLL1 et DLL2. Étape 1 consiste à exécuter LIB, avec l’option /DEF définie, sur DLL1. Étape 1 génère DLL1.lib, une bibliothèque d’importation et DLL1.exp. À l’étape 2, la bibliothèque d’importation est utilisée pour générer DLL2, laquelle à son tour produit une bibliothèque d’importation pour les symboles de DLL2. Étape 3 génère DLL1, en utilisant DLL1.exp et DLL2.lib comme entrée. Notez qu’un fichier .exp pour DLL2 n’est pas nécessaire car LIB n’a pas été utilisé pour générer la bibliothèque d’importation de DLL2.  
  
 ![Utilisation d’importations mutuelles pour lier deux DLL](../build/media/vc37yj1.gif "vc37YJ1")  
Liaison de deux DLL avec des importations mutuelles  
  
## <a name="limitations-of-afxext"></a>Limitations de _AFXEXT  
 Vous pouvez utiliser la `_AFXEXT` symbole de préprocesseur pour votre tant que vous n’avez pas plusieurs couches de DLL d’extension MFC des DLL d’extension MFC. Si vous avez qui appellent ou dérivent des classes dans votre propre MFC DLL d’extension, lesquelles dérivent ensuite les classes MFC, les DLL d’extension MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter toute ambiguïté.  
  
 Le problème est que dans Win32, vous devez déclarer explicitement toutes les données en tant que **__declspec (dllexport)** s’il doit être exporté à partir d’une DLL, et **__declspec (dllimport)** s’il doit être importé à partir d’une DLL. Lorsque vous définissez `_AFXEXT`, les en-têtes MFC vous assurer que **AFX_EXT_CLASS** est correctement défini.  
  
 Lorsque vous avez plusieurs couches, un symbole comme **AFX_EXT_CLASS** n’est pas suffisant, car une DLL d’extension MFC peut exporter de nouvelles classes, ainsi que l’importation d’autres classes à partir d’une autre DLL d’extension MFC. Pour résoudre ce problème, utilisez un symbole de préprocesseur spécial qui indique que vous générez la DLL mais plutôt à l’aide de la DLL. Par exemple, imaginez deux DLL d’extension MFC,.dll et B.dll. Elles exportent certaines classes dans A.h et B.h, respectivement. B.dll utilise les classes de.dll. Les fichiers d’en-tête ressemblerait à ceci :  
  
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
  
 Lorsque.dll est généré, il est généré avec `/D A_IMPL` et lorsque B.dll est générée, elle est générée avec `/D B_IMPL`. À l’aide de symboles distincts pour chaque DLL, `CExampleB` est exporté et `CExampleA` est importé lors de la génération de B.dll. `CExampleA` est exporté lors de la génération.dll et importés lorsqu’il est utilisé par B.dll (ou un autre client).  
  
 Ce type de superposition ne peut pas être effectué lors de l’utilisation de la fonction intégrée **AFX_EXT_CLASS** et `_AFXEXT` symboles de préprocesseur. La technique décrite ci-dessus résout ce problème de manière à la différence pas que le mécanisme d’application MFC elle-même utilise lors de la génération de sa technologies Active, la base de données et la DLL d’extension MFC de réseau.  
  
## <a name="not-exporting-the-entire-class"></a>Exportez ne pas la classe entière  
 Lorsque vous n’exportez pas une classe entière, vous devez vous assurer que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Cela est possible en redéfinissant `AFX_DATA` macro de votre classe spécifique. Cela doit être effectuée à tout moment, que vous n’exportez pas la classe entière.  
  
 Par exemple :  
  
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
  
### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL](../build/exporting-from-a-dll.md)  
  
-   [Exporter à partir d’une DLL à l’aide. Fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [L’utilitaire LIB et option /DEF](../build/reference/lib-reference.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Importation et exportation](../build/importing-and-exporting.md)