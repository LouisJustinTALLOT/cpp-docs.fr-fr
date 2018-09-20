---
title: num_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27e39d7db36c121add3598387de52ecb878059b5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405266"
---
# <a name="numthreads"></a>num_threads

Définit le nombre de threads dans une équipe de thread.

## <a name="syntax"></a>Syntaxe

```
num_threads(num)
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Le nombre de threads

## <a name="remarks"></a>Notes

Le `num_threads` clause a les mêmes fonctionnalités que le [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) (fonction).

`num_threads` s’applique aux directives suivantes :

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [sections](../../../parallel/openmp/reference/sections-openmp.md)

Pour plus d’informations, consultez [2.3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

## <a name="example"></a>Exemple

Consultez [parallèles](../../../parallel/openmp/reference/parallel.md) pour obtenir un exemple d’utilisation `num_threads` clause.

## <a name="see-also"></a>Voir aussi

[Clauses](../../../parallel/openmp/reference/openmp-clauses.md)