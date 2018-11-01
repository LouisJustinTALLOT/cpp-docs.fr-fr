---
title: 3.1.4 Fonction omp_get_thread_num
ms.date: 11/04/2016
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
ms.openlocfilehash: eca8522aeab4702be390d98faaf8920f2d732244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480928"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 Fonction omp_get_thread_num

Le `omp_get_thread_num` fonction retourne le nombre de threads au sein de son équipe, du thread exécutant la fonction. Le se trouve de thread nombre compris entre 0 et **omp_get_num_threads()**-1, inclus. Le thread principal de l’équipe est 0.

Le format est le suivant :

```
#include <omp.h>
int omp_get_thread_num(void);
```

Si elle est appelée à partir d’une région de série, `omp_get_thread_num` retourne 0. Si elle est appelée à partir de dans une région parallèle imbriquée qui est sérialisée, cette fonction retourne 0.

## <a name="cross-references"></a>Références externes :

- `omp_get_num_threads` fonction, consultez [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) sur la page 37.