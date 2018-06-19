---
title: Variables d’environnement OpenMP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02248b7725f2a4312f26984c798e7248463d2615
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692306"
---
# <a name="openmp-environment-variables"></a>Variables d'environnement OpenMP
Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.  
  
 L’implémentation Visual C++ de l’OpenMP standard inclut les variables d’environnement. Ces variables d’environnement sont en lecture au démarrage du programme et les modifications apportées à leurs valeurs sont ignorées lors de l’exécution (par exemple, à l’aide de [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).  
  
|Variable d’environnement|Description|  
|--------------------------|-----------------|  
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.|  
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Spécifie si parallélisme imbriquée est activée, sauf si le parallélisme imbriquée est activée ou désactivée avec `omp_set_nested`.|  
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Définit le nombre maximal de threads dans la région parallèle, sauf si [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) ou [num_threads](../../../parallel/openmp/reference/num-threads.md).|  
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Modifie le comportement de la [planification](../../../parallel/openmp/reference/schedule.md) clause lorsque `schedule(runtime)` est spécifié dans un `for` ou `parallel for` la directive.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)