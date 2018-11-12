---
title: A.29   Utilisation des constructions de partage de travail à l'intérieur d'une construction critical
ms.date: 11/04/2016
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
ms.openlocfilehash: fac5576f859f63298d658b51c4307bb238e301c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643584"
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