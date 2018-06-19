---
title: 3.1.2 fonction omp_get_num_threads | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df01d571b67ff6d252d85128fcc8c1d26a6e94a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687437"
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 Fonction omp_get_num_threads
Le **omp_get_num_threads** fonction retourne le nombre de threads actuellement dans l’équipe de l’exécution de la région parallèle à partir de laquelle elle est appelée. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 Le **num_threads** clause, le **omp_set_num_threads** (fonction) et le **OMP_NUM_THREADS** variable d’environnement contrôlent le nombre de threads dans une équipe.  
  
 Si le nombre de threads n’a pas été explicitement défini par l’utilisateur, la valeur par défaut est défini par l’implémentation. Cette fonction est liée à la forme le plus proche **parallèles** directive. Si elle est appelée à partir d’une série partie d’un programme ou une région parallèle imbriquée qui est sérialisée, cette fonction retourne 1.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **OMP_NUM_THREADS** voir variable d’environnement [Section 4.2](../../parallel/openmp/4-2-omp-num-threads.md) page 48.  
  
-   **num_threads** clause, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.  
  
-   **parallèle** construire, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.