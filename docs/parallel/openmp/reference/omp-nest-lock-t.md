---
title: imbriqué omp_nest_lock_t | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- omp_nest_lock_t OpenMP data type
ms.assetid: fceac9fb-96d2-42b0-af19-c9b078380618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b25a76332325247987751d8e9c41914da51f4a70
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390134"
---
# <a name="ompnestlockt"></a>omp_nest_lock_t

Un type qui contient les éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.

Ces fonctions utilisent **imbriqué omp_nest_lock_t**:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)

- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)

- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)

- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)

- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

Pour plus d’informations, consultez [3.2 fonctions de verrouillage](../../../parallel/openmp/3-2-lock-functions.md).

## <a name="example"></a>Exemple

Consultez [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) pour obtenir un exemple d’utilisation de **imbriqué omp_nest_lock_t**.

## <a name="see-also"></a>Voir aussi

[Types de données](../../../parallel/openmp/reference/openmp-data-types.md)