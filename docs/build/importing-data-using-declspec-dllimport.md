---
title: Importation de données à l'aide de __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- dllimport
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: bc1b21bad1f7d4515774dbe76c2567280cdbf1f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620569"
---
# <a name="importing-data-using-declspecdllimport"></a>Importation de données à l'aide de __declspec(dllimport)

Dans le cas des données, à l’aide **__declspec (dllimport)** est pratique car qui supprime une couche d’indirection. Lorsque vous importez des données à partir d’une DLL, vous devez toujours passer par la table d’adresses importation. Avant de **__declspec (dllimport)**, cela signifiait que vous deviez n’oubliez pas d’effectuer un niveau supplémentaire d’indirection lors de l’accès aux données exportées à partir de la DLL :

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Vous devez exporter les données dans votre. Fichier DEF :

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

Lorsque vous marquez les données en tant que **__declspec (dllimport)**, le compilateur génère automatiquement le code d’indirection pour vous. Vous n’avez plus à vous soucier de la procédure ci-dessus. Comme indiqué précédemment, n’utilisez pas **__declspec (dllimport)** déclaration sur les données lors de la génération de la DLL. Fonctions de la DLL n’utilisent pas la table d’importation adresse pour accéder à l’objet de données ; Par conséquent, vous n’aura pas le niveau supplémentaire d’indirection présents.

Pour exporter les données automatiquement à partir de la DLL, utilisez cette déclaration :

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Voir aussi

[Importation dans une application](../build/importing-into-an-application.md)