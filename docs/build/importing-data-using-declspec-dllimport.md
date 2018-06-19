---
title: L’importation de données à l’aide de __declspec (dllimport) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9877c5a229c3cabcb7703dd2617d1d57e3512f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368510"
---
# <a name="importing-data-using-declspecdllimport"></a>Importation de données à l'aide de __declspec(dllimport)
Dans le cas des données, à l’aide de **__declspec (dllimport)** est un élément de commodité qui supprime une couche d’indirection. Lorsque vous importez des données à partir d’une DLL, vous devez toujours passer par la table d’adresses importation. Avant de **__declspec (dllimport)**, cela signifie que vous deviez n’oubliez pas d’effectuer un niveau supplémentaire d’indirection lors de l’accès aux données exportées à partir de la DLL :  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 Puis exporter les données de votre. Fichier de définition :  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 et y accéder à l’extérieur de la DLL :  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 Lorsque vous marquez les données en tant que **__declspec (dllimport)**, le compilateur génère automatiquement le code d’indirection pour vous. Vous n’avez plus à vous soucier de la procédure ci-dessus. Comme indiqué précédemment, n’utilisez pas **__declspec (dllimport)** déclaration sur les données lors de la génération de la DLL. Fonctions de la DLL n’utilisent pas la table d’adresses importation pour accéder à l’objet de données ; Par conséquent, vous n’aura pas le niveau supplémentaire d’indirection présent.  
  
 Pour exporter les données automatiquement à partir de la DLL, utilisez cette déclaration :  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Importation dans une application](../build/importing-into-an-application.md)