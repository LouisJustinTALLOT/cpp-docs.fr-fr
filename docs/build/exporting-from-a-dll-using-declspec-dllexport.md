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
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328592"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Exportation à partir d'une DLL à l'aide de __declspec(dllexport)

Vous pouvez exporter des données, des fonctions, des classes ou des fonctions de membre de la classe à partir d’un mot clé DLL à l’aide du mot clé **__declspec (dllexport).** **__declspec (dllexport)** ajoute la directive d’exportation au fichier objet de sorte que vous n’avez pas besoin d’utiliser un fichier .def.

Cette commodité est plus évidente lorsque vous essayez d’exporter des noms de fonctionS décorés de C. Parce qu’il n’y a pas de spécification standard pour la décoration de nom, le nom d’une fonction exportée pourrait changer entre les versions de compilateur. Si vous utilisez **__declspec (dllexport),** la récompatation des fichiers DLL et dependent .exe est nécessaire uniquement pour tenir compte de tout changement de convention de nommage.

De nombreuses directives d’exportation, telles que les ordinaux, NONAME et PRIVATE, ne peuvent être faites que dans un fichier .def, et il n’y a aucun moyen de spécifier ces attributs sans fichier .def. Cependant, l’utilisation **de __declspec (dllexport)** en plus d’utiliser un fichier .def ne provoque pas d’erreurs de construction.

Pour les fonctions d’exportation, le mot clé **__declspec (dllexport)** doit apparaître à gauche du mot clé de la convention d’appel, si un mot clé est spécifié. Par exemple :

```
__declspec(dllexport) void __cdecl Function1(void);
```

Pour exporter toutes les fonctions des membres des données publiques et des membres dans une classe, le mot clé doit apparaître à gauche du nom de classe comme suit :

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`ne peuvent pas être `__clrcall` appliqués à une fonction avec la convention d’appel.

Lors de la construction de votre DLL, vous créez généralement un fichier d’en-tête qui contient les prototypes de fonction et / ou des classes que vous exportez et ajouter **__declspec (dllexport)** aux déclarations dans le fichier d’en-tête. Pour rendre votre code plus lisible, définissez une macro pour **__declspec (dllexport)** et utilisez la macro avec chaque symbole que vous exportez :

```
#define DllExport   __declspec( dllexport )
```

**__declspec (dllexport)** stocke les noms de fonction dans la table d’exportation de la DLL. Si vous souhaitez optimiser la taille de la table, voir [fonctions d’exportation à partir d’un DLL par Ordinal Plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exportation à partir d’un DLL à l’aide de fichiers .def](exporting-from-a-dll-using-def-files.md)

- [Exportation et importation à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Fonctions d’exportation CMD pour une utilisation dans les exécutables en langue C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Fonctions d’exportation C pour une utilisation dans les exécutables en langue C ou en langue C](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer quelle méthode d’exportation utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l'aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser un DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Le mot clé __declspec](../cpp/declspec.md)

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
