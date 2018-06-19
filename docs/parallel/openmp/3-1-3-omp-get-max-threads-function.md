---
title: 3.1.3 fonction omp_get_max_threads | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2afa797cc74a50041f2ea24f76fa07ffe109072b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687509"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 Fonction omp_get_max_threads
Le **omp_get_max_threads** fonction retourne un entier qui est garanti être au moins aussi grande que le nombre de threads qui seront utilisés pour former une équipe si une région parallèle sans un **num_threads** clause devait être rencontré à ce stade dans le code. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 Les éléments suivants exprimant une limite inférieure de la valeur de **omp_get_max_threads**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 Notez que si une région parallèle suivante utilise le **num_threads** pour demander un certain nombre de threads, la garantie sur la limite inférieure du résultat de la clause **omp_get_max_threads** aucun blocage long.  
  
 Le **omp_get_max_threads** valeur de retour de la fonction peut servir à allouer dynamiquement de stockage suffisant pour tous les threads de l’équipe formé à la région parallèle suivante.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **omp_get_num_threads** , consultez [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) à la page 37.  
  
-   **omp_set_num_threads** , consultez [Section 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) sur la page 36.  
  
-   **omp_set_dynamic** , consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.  
  
-   **num_threads** clause, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.