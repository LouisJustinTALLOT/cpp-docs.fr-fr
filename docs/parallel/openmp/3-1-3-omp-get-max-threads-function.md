---
title: 3.1.3 Fonction omp_get_max_threads
ms.date: 11/04/2016
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
ms.openlocfilehash: 3f954b5ad75b4bdb4a74323f2ab4e819850269ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546579"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 Fonction omp_get_max_threads

Le **omp_get_max_threads** fonction retourne un entier qui est garanti au moins aussi grand que le nombre de threads qui serait utilisée pour former une équipe si une région parallèle sans un **num_threads** clause ont été rencontrées à ce stade dans le code. Le format est le suivant :

```
#include <omp.h>
int omp_get_max_threads(void);
```

Les éléments suivants exprimant une limite inférieure de la valeur de **omp_get_max_threads**:

```

threads-used-for-next-team
<= omp_get_max_threads

```

Notez que si une région parallèle suivante utilise le **num_threads** clause pour demander un certain nombre de threads, la garantie de la limite inférieure du résultat de **omp_get_max_threads** aucun blocage long.

Le **omp_get_max_threads** valeur de retour de la fonction peut être utilisé pour allouer dynamiquement de stockage suffisant pour tous les threads dans l’équipe formée dans la région parallèle suivante.

## <a name="cross-references"></a>Références externes :

- **omp_get_num_threads** de fonction, consultez [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) sur la page 37.

- **omp_set_num_threads** de fonction, consultez [Section 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) sur page 36.

- **omp_set_dynamic** de fonction, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.

- **num_threads** clause, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.