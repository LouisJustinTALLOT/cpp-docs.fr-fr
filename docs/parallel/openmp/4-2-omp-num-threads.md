---
title: 4.2 OMP_NUM_THREADS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c2b766d0e3be9b4f1d272a6e3fa205cfcb87039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS
Le **OMP_NUM_THREADS** variable d’environnement définit le nombre de threads à utiliser pendant l’exécution, par défaut, sauf si ce nombre est modifié explicitement en appelant le **omp_set_num_threads** routine de bibliothèque ou par explicite **num_threads** clause sur une **parallèles** directive.  
  
 La valeur de la **OMP_NUM_THREADS** variable d’environnement doit être un entier positif. Son effet dépend de si l’ajustement dynamique du nombre de threads est activé. Pour un ensemble de règles sur l’interaction entre le **OMP_NUM_THREADS** environnement ajustement variable et dynamique de threads, consultez la Section 2.3 page 8.  
  
 Si aucune valeur n’est spécifiée pour le **OMP_NUM_THREADS** variable d’environnement, ou si la valeur spécifiée n’est pas un entier positif, ou si la valeur est supérieure au nombre maximal de threads du système peut prendre en charge, le nombre de threads à utiliser est défini par l’implémentation.  
  
 Exemple :  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## <a name="cross-references"></a>Références externes :  
  
-   **num_threads** clause, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.  
  
-   **omp_set_num_threads** , consultez [Section 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) sur la page 36.  
  
-   **omp_set_dynamic** , consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.