---
title: 3.1.1 fonction omp_set_num_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85f7ff733583e531b449caf2039817b71165da52
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426794"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 Fonction omp_set_num_threads

Le `omp_set_num_threads` fonction définit le nombre par défaut de threads à utiliser pour des régions parallèles suivantes qui ne spécifient pas une `num_threads` clause. Le format est le suivant :

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

La valeur du paramètre *num_threads* doit être un entier positif. Son effet dépend de si l’ajustement dynamique du nombre de threads est activé. Pour un ensemble complet de règles sur l’interaction entre le `omp_set_num_threads` (fonction) et l’ajustement dynamique de threads, consultez la Section 2.3 page 8.

Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Cet appel est prioritaire sur la `OMP_NUM_THREADS` variable d’environnement. La valeur par défaut pour le nombre de threads, ce qui peut être établie en appelant `omp_set_num_threads` ou en définissant le `OMP_NUM_THREADS` variable d’environnement, peuvent être substituées explicitement sur un seul **parallèles** directive en spécifiant le `num_threads` clause.

## <a name="cross-references"></a>Références externes :

- `omp_set_dynamic` fonction, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.

- `omp_get_dynamic` fonction, consultez [Section 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) sur la page 40.

- `OMP_NUM_THREADS` voir variable d’environnement [Section 4.2](../../parallel/openmp/4-2-omp-num-threads.md) sur page 48 et Section 2.3 page 8.

- `num_threads` clause, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8