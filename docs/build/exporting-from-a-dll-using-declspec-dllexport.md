---
title: Exportation à partir d'une DLL à l'aide de __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 77dc6dc14efe2a7ccf46c41477ed4fd6d1956856
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224030"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportation à partir d'une DLL à l'aide de __declspec(dllexport)

Vous pouvez exporter des données, des fonctions, des classes ou des fonctions membres de classe à partir d’une DLL à l’aide du **`__declspec(dllexport)`** mot clé. **`__declspec(dllexport)`** Ajoute la directive d’exportation au fichier objet. vous n’avez donc pas besoin d’utiliser un fichier. def.

Cette pratique est plus évidente quand vous tentez d’exporter des noms de fonctions décorés en C++. Étant donné qu’il n’existe pas de spécification standard pour la décoration de nom, le nom d’une fonction exportée peut changer entre les versions du compilateur. Si vous utilisez **`__declspec(dllexport)`** , la recompilation de la dll et des fichiers. exe dépendants est nécessaire uniquement pour tenir compte des modifications de convention d’affectation de noms.

De nombreuses directives d’exportation, telles que les ordinaux, NONAME et PRIVATE, ne peuvent être effectuées que dans un fichier. def, et il n’existe aucun moyen de spécifier ces attributs sans un fichier. def. Toutefois, l’utilisation **`__declspec(dllexport)`** de en plus de l’utilisation d’un fichier. def ne provoque pas d’erreur de Build.

Pour exporter des fonctions, le **`__declspec(dllexport)`** mot clé doit apparaître à gauche du mot clé de la Convention d’appel, si un mot clé est spécifié. Par exemple :

```
__declspec(dllexport) void __cdecl Function1(void);
```

Pour exporter l’ensemble des membres de données publics et des fonctions membres dans une classe, le mot clé doit apparaître à gauche du nom de la classe, comme suit :

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`ne peut pas être appliqué à une fonction avec la `__clrcall` Convention d’appel.

Lors de la génération de votre DLL, vous créez généralement un fichier d’en-tête qui contient les prototypes de fonction et/ou les classes que vous exportez et ajoutez **`__declspec(dllexport)`** aux déclarations dans le fichier d’en-tête. Pour rendre votre code plus lisible, définissez une macro pour **`__declspec(dllexport)`** et utilisez la macro avec chaque symbole que vous exportez :

```
#define DllExport   __declspec( dllexport )
```

**`__declspec(dllexport)`** stocke les noms de fonctions dans la table d’exportation de la DLL. Si vous souhaitez optimiser la taille de la table, consultez [exportation de fonctions à partir d’une dll par ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers. def](exporting-from-a-dll-using-def-files.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Mot clé __declspec](../cpp/declspec.md)

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d'une DLL](exporting-from-a-dll.md)
