---
title: 4.2 OMP_NUM_THREADS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9996a09661d962eb5e936fdb484c9dd534e46904
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445189"
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

Le **OMP_NUM_THREADS** variable d’environnement définit le nombre de threads à utiliser pendant l’exécution, par défaut, sauf si ce nombre est modifié explicitement en appelant le **omp_set_num_threads** routine de bibliothèque ou par explicite **num_threads** clause sur une **parallèles** directive.

La valeur de la **OMP_NUM_THREADS** variable d’environnement doit être un entier positif. Son effet dépend de si l’ajustement dynamique du nombre de threads est activé. Pour un ensemble complet de règles sur l’interaction entre le **OMP_NUM_THREADS** environnement ajustement variable et dynamique de threads, consultez la Section 2.3 page 8.

Si aucune valeur n’est spécifiée pour le **OMP_NUM_THREADS** variable d’environnement, ou si la valeur spécifiée n’est pas un entier positif, ou si la valeur est supérieure au nombre maximal de threads du système peut prendre en charge, le nombre de threads à utiliser est défini par l’implémentation.

Exemple :

```
setenv OMP_NUM_THREADS 16
```

## <a name="cross-references"></a>Références externes :

- **num_threads** clause, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.

- **omp_set_num_threads** de fonction, consultez [Section 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) sur page 36.

- **omp_set_dynamic** de fonction, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.