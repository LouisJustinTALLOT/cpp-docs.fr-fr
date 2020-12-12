---
description: 'En savoir plus sur : erreur du compilateur C3021'
title: Erreur du compilateur C3021
ms.date: 11/04/2016
f1_keywords:
- C3021
helpviewer_keywords:
- C3021
ms.assetid: 0cef6d97-e267-438a-ac8b-0daf5bbbc2cf
ms.openlocfilehash: c615dcb476aef5e3c9de0e705ca35d696e2af6a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285719"
---
# <a name="compiler-error-c3021"></a>Erreur du compilateur C3021

'arg' : argument vide dans la directive OpenMP 'directive'

Un argument est requis pour une directive OpenMP.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3021 :

```cpp
// C3021.cpp
// compile with: /openmp
#include <stdio.h>
#include "omp.h"

int g = 0;

int main()
{
    int x, y, i;

    #pragma omp parallel for schedule(static,)   // C3021
    for (i = 0; i < 10; ++i) ;

    #pragma omp parallel for schedule()   // C3021
    for (i = 0; i < 10; ++i)
        printf_s("Hello world, thread %d, iteration %d\n",
                 omp_get_thread_num(), i);

    #pragma omp parallel reduction()   // C3021
      ;

    #pragma omp parallel reduction(+ :)   // C3021
      ;

    //
    // The following shows correct syntax examples.
    //
    #pragma omp parallel reduction(+ : x, y)
      ;

    #pragma omp parallel reduction(* : x, y)
      ;

    #pragma omp parallel reduction(- : x, y)
      ;

    #pragma omp parallel reduction(& : x, y)
      ;

    #pragma omp parallel reduction(^ : x, y)
      ;

    #pragma omp parallel reduction(| : x, y)
      ;

    #pragma omp parallel reduction(&& : x, y)
      ;

    #pragma omp parallel reduction(|| : x, y)
      ;
}
```
