---
title: Importation de données à l'aide de __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 341912b53301c3a11df4285167d66c8c1493d2fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223991"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importation de données à l'aide de __declspec(dllimport)

Dans le cas de données, l’utilisation de **`__declspec(dllimport)`** est un élément pratique qui supprime une couche d’indirection. Lorsque vous importez des données à partir d’une DLL, vous devez toujours passer par la table d’adresses d’importation. Avant **`__declspec(dllimport)`** , cela signifiait qu’il fallait se souvenir d’effectuer un niveau supplémentaire d’indirection lors de l’accès aux données exportées à partir de la dll :

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Vous exportez ensuite les données dans votre. Fichier DEF :

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

et y accéder en dehors de la DLL :

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Quand vous marquez les données en tant que **`__declspec(dllimport)`** , le compilateur génère automatiquement le code d’indirection pour vous. Vous n’avez plus à vous soucier des étapes ci-dessus. Comme indiqué précédemment, n’utilisez pas **`__declspec(dllimport)`** de déclaration sur les données lors de la génération de la dll. Les fonctions de la DLL n’utilisent pas la table d’adresses d’importation pour accéder à l’objet de données ; par conséquent, vous n’aurez pas le niveau supplémentaire d’indirection.

Pour exporter les données automatiquement à partir de la DLL, utilisez la déclaration suivante :

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
