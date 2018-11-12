---
title: Types de données OpenMP
ms.date: 10/23/2018
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
ms.openlocfilehash: bacb48194015f8fd6c80a9868af06702deceab6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533768"
---
# <a name="openmp-data-types"></a>Types de données OpenMP

Fournit des liens vers les types de données utilisés dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les types de données suivants.

|Type de données|Description|
|---------|-----------|
|[omp_lock_t](#omp-lock-t)|Un type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread détient un verrou.|
|[omp_nest_lock_t](#omp-nest-lock-t)|Un type qui conserve l’un des éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.|

## <a name="omp-lock-t"></a>omp_lock_t

Un type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread détient un verrou.

Ces fonctions utilisent `omp_lock_t`:

- [omp_init_lock](openmp-functions.md#omp-init-lock)
- [omp_destroy_lock](openmp-functions.md#omp-destroy-lock)
- [omp_set_lock](openmp-functions.md#omp-set-lock)
- [omp_unset_lock](openmp-functions.md#omp-unset-lock)
- [omp_test_lock](openmp-functions.md#omp-test-lock)

Pour plus d’informations, consultez [3.2 fonctions de verrouillage](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [fonctions omp_init_lock](openmp-functions.md#omp-init-lock) pour obtenir un exemple d’utilisation de `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>imbriqué omp_nest_lock_t

Un type qui contient les éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.

Ces fonctions utilisent `omp_nest_lock_t`:

- [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)
- [omp_destroy_nest_lock](openmp-functions.md#omp-destroy-nest-lock)
- [omp_set_nest_lock](openmp-functions.md#omp-set-nest-lock)
- [omp_unset_nest_lock](openmp-functions.md#omp-unset-nest-lock)
- [omp_test_nest_lock](openmp-functions.md#omp-test-nest-lock)

Pour plus d’informations, consultez [3.2 fonctions de verrouillage](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock) pour obtenir un exemple d’utilisation de `omp_nest_lock_t`.
