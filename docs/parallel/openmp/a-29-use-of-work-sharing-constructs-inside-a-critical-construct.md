---
title: A.29 partage de l’utilisation de travail construit à l’intérieur d’une construction critical | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccbb39a9067adf545339d02fe0c05e24fbcdb0a4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691350"
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29   Utilisation des constructions de partage de travail à l'intérieur d'une construction critical
L’exemple suivant montre à l’aide d’une construction de partage de travail à l’intérieur d’un `critical` construire. Cet exemple est conforme, car le partage de travail construire et `critical` construction ne liez pas à la même région parallèle.  
  
```  
void f()  
{  
  int i = 1;  
  #pragma omp parallel sections  
  {  
    #pragma omp section  
    {  
      #pragma omp critical (name)  
      {  
        #pragma omp parallel  
        {  
          #pragma omp single  
          {  
            i++;  
          }  
        }  
      }  
    }  
  }  
}  
```