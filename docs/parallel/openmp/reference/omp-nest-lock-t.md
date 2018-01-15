---
title: omp_nest_lock_t | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_nest_lock_t
dev_langs: C++
helpviewer_keywords: omp_nest_lock_t OpenMP data type
ms.assetid: fceac9fb-96d2-42b0-af19-c9b078380618
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bbf62ae43ed1ebd0d28157b03fabace9b2b9d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ompnestlockt"></a>omp_nest_lock_t
Un type qui contient les éléments suivants d’informations sur un verrou : si le verrou est disponible, et que l’identité du thread qui détient le verrou ainsi que le nombre d’imbrication.  
  
 Ces fonctions utilisent **omp_nest_lock_t**:  
  
-   [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)  
  
-   [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)  
  
-   [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)  
  
-   [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)  
  
-   [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)  
  
 Pour plus d’informations, consultez [3.2 fonctions de verrouillage](../../../parallel/openmp/3-2-lock-functions.md).  
  
## <a name="example"></a>Exemple  
 Consultez [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) pour obtenir un exemple d’utilisation de **omp_nest_lock_t**.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../parallel/openmp/reference/openmp-data-types.md)