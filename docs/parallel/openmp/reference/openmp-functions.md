---
title: Fonctions OpenMP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39fe44ff053a2e49a1067d0af071353e0a50ece
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693274"
---
# <a name="openmp-functions"></a>Fonctions OpenMP
Fournit des liens vers les fonctions utilisées dans l’API OpenMP.  
  
 L’implémentation Visual C++ de l’OpenMP standard inclut les fonctions suivantes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|N’initialise pas un verrou.|  
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|N’initialise pas un verrou pouvant.|  
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Retourne une valeur qui indique si le nombre de threads disponibles dans une région parallèle suivante peut être ajusté par le temps d’exécution.|  
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Retourne un entier qui est égale ou supérieure au nombre de threads qui serait disponible si une région parallèle sans [num_threads](../../../parallel/openmp/reference/num-threads.md) ont été définies à ce stade dans le code.|  
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Retourne une valeur qui indique si le parallélisme imbriquée est activée.|  
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Retourne le nombre de processeurs qui sont disponibles lorsque la fonction est appelée.|  
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Retourne le nombre de threads dans la région parallèle.|  
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Retourne le nombre de threads d’exécution du thread au sein de son équipe de thread.|  
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Retourne le nombre de secondes entre les battements d’horloge de processeur.|  
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Retourne qu'une valeur en secondes du temps écoulé à partir d’un moment donné.|  
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Retourne zéro si appelée à partir d’une région parallèle.|  
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Initialise un verrou simple.|  
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Initialise un verrou.|  
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Indique que le nombre de threads disponibles dans une région parallèle suivante peut être ajusté par le temps d’exécution.|  
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Blocs d’exécution du thread jusqu'à ce qu’un verrou n’est disponible.|  
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Blocs d’exécution du thread jusqu'à ce qu’un verrou n’est disponible.|  
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Active le parallélisme imbriqué.|  
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Définit le nombre de threads dans les régions parallèles suivantes, sauf si un [num_threads](../../../parallel/openmp/reference/num-threads.md) clause.|  
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Tente de définir un verrou, mais ne bloque pas l’exécution du thread.|  
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Tente de définir un verrou pouvant mais ne bloque pas l’exécution du thread.|  
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Libère un verrou.|  
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Libère un verrou pouvant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)