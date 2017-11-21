---
title: Utilisation A.30 de Reprivatization | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 26529090-6c39-40f2-b806-e12374d6b5f8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8ab359fdc63d90494b686684d26cc73e0135c886
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="a30---use-of-reprivatization"></a>A.30   Utilisation de la reprivatisation
L’exemple suivant montre la reprivatization des variables. Variables privées peuvent être marqués `private` dans une directive imbriquée. Ils n’ont pas à être partagées dans la région parallèle englobante.  
  
```  
int i, a;  
...  
#pragma omp parallel private(a)  
{  
  ...  
  #pragma omp parallel for private(a)  
  for (i=0; i<10; i++)  
     {  
       ...  
     }  
}  
```