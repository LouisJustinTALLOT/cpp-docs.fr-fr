---
title: A.12 à l’aide de la Directive atomique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719d7a9843a0759b5a5bd558e07a2004f9ef1543
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691406"
---
# <a name="a12---using-the-atomic-directive"></a>A.12   Utilisation de la directive atomic
L’exemple suivant permet d’éviter des conditions de concurrence (mises à jour simultanées d’un élément de *x* par plusieurs threads) à l’aide de la `atomic` directive ([Section 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) à la page 19) :  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 L’avantage d’utiliser le `atomic` directive dans cet exemple est qu’il permet des mises à jour de deux éléments de x pour être exécutées en parallèle. Si un `critical` directive ([Section 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) page 18) ont été utilisés à la place, puis toutes les mises à jour à des éléments de *x* sont exécutées en série (mais pas dans les garanties ordre).  
  
 Notez que la `atomic` directive s’applique uniquement à l’instruction C ou C++ qui la suit immédiatement.  Par conséquent, les éléments de *y* ne sont pas mises à jour de manière atomique dans cet exemple.