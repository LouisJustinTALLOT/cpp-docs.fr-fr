---
title: Si (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4aaad878040534fd198bcdf4a93d7820fd89adc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404811"
---
# <a name="if-openmp"></a>if (OpenMP)

Spécifie si une boucle doit être exécutée en parallèle ou en série.

## <a name="syntax"></a>Syntaxe

```
if(expression)
```

### <a name="parameters"></a>Paramètres

*Expression*<br/>
Une expression intégrale lequel, si elle a la valeur true (différent de zéro), le code dans la région parallèle pour exécuter en parallèle. Si l’expression prend la valeur false (zéro), la région parallèle est exécutée en série (par un seul thread).

## <a name="remarks"></a>Notes

`if` s’applique aux directives suivantes :

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [sections](../../../parallel/openmp/reference/sections-openmp.md)

Pour plus d’informations, consultez [2.3 construction parallèle](../../../parallel/openmp/2-3-parallel-construct.md).

## <a name="example"></a>Exemple

```
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="see-also"></a>Voir aussi

[Clauses](../../../parallel/openmp/reference/openmp-clauses.md)