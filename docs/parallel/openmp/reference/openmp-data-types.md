---
title: Types de données OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 254dffebc258867088f738b10a11bf48d31bd0a4
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990061"
---
# <a name="openmp-data-types"></a>Types de données OpenMP

Fournit des liens vers les types de données utilisés dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les types de données suivants.

Type de données                           | Description
----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[omp_lock_t](#omp-lock-t)           | Un type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread détient un verrou.
[omp_nest_lock_t](#omp-nest-lock-t) | Un type qui conserve l’un des éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.

## <a name="omp-lock-t"></a>omp_lock_t

Un type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread détient un verrou.

Ces fonctions utilisent `omp_lock_t`:

- [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)
- [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)
- [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)
- [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)
- [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)

Pour plus d’informations, consultez [3.2 fonctions de verrouillage](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [fonctions omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) pour obtenir un exemple d’utilisation de `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>imbriqué omp_nest_lock_t

Un type qui contient les éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.

Ces fonctions utilisent `omp_nest_lock_t`:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)
- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)
- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)
- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)
- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

Pour plus d’informations, consultez [3.2 fonctions de verrouillage](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Exemple

Consultez [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) pour obtenir un exemple d’utilisation de `omp_nest_lock_t`.
