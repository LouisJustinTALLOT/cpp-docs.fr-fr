---
title: omp_set_nested | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d66c71bdd897471527ead5cc896471bec61193c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409218"
---
# <a name="ompsetnested"></a>omp_set_nested

Active le parallélisme imbriqué.

## <a name="syntax"></a>Syntaxe

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
Si elle est différente de zéro, permet de parallélisme imbriqué. Si zéro, désactive le parallélisme imbriqué.

## <a name="remarks"></a>Notes

OMP imbriqué parallélisme peut être activé avec `omp_set_nested`, ou en définissant le [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) variable d’environnement.

Le paramètre pour `omp_set_nested` remplace le paramètre de la `OMP_NESTED` variable d’environnement.

Lorsque l’option est activée, la variable d’environnement peut interrompre un programme opérationnels dans le cas contraire, car le nombre de threads augmente de façon exponentielle lors de l’imbrication de régions parallèles.  Par exemple, une fonction que récursivement 6 fois avec le nombre de threads OMP défini sur 4 requiert 4 096 (4 à la puissance de 6) les threads en général, les performances de votre application se dégradera si le nombre de threads dépasse le nombre de processeurs. Une exception à cela serait qu'applications liées aux e/s.

Utilisez [omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md) pour afficher le paramètre actuel de `omp_set_nested`.

Pour plus d’informations, consultez [3.1.9 fonction omp_set_nested](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

## <a name="example"></a>Exemple

```
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="see-also"></a>Voir aussi

[Fonctions](../../../parallel/openmp/reference/openmp-functions.md)