---
title: Utilisation A.28 de num_threads Clause | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 26238da1-902c-49b4-9559-0fbc9eaf7f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12289192d056acac684f28712ccf2aa1423b6c3e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689114"
---
# <a name="a28---use-of-numthreads-clause"></a>A.28   Utilisation de la clause num_threads
L’exemple suivant illustre la `num_threads` clause ([Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8). La région parallèle est exécutée avec un maximum de 10 threads.  
  
```  
#include <omp.h>  
main()  
{  
    omp_set_dynamic(1);  
    ...  
    #pragma omp parallel num_threads(10)  
    {  
        ... parallel region ...  
    }  
}  
```