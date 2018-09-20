---
title: 3.1.3 fonction omp_get_max_threads | Microsoft Docs
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
ms.openlocfilehash: c439dc0203fa3435c62e9669da40b5b092556492
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400820"
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