---
title: omp_get_max_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_max_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_get_max_threads OpenMP function
ms.assetid: f47c3725-3e40-469f-8bc8-a1e47f264cc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5c677b56d27038405237deb8c9bda2aeee87e7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446684"
---
# <a name="ompgetmaxthreads"></a>omp_get_max_threads

Retourne un entier qui est égal à ou supérieur au nombre de threads qui serait disponible si une région parallèle sans [num_threads](../../../parallel/openmp/reference/num-threads.md) ont été définies à ce stade dans le code.

## <a name="syntax"></a>Syntaxe

```
int omp_get_max_threads( )
```

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.1.3 fonction omp_get_max_threads](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

## <a name="example"></a>Exemple

```
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="see-also"></a>Voir aussi

[Fonctions](../../../parallel/openmp/reference/openmp-functions.md)