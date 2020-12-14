---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4938'
title: Avertissement du compilateur (niveau 4) C4938
ms.date: 11/04/2016
f1_keywords:
- C4938
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
ms.openlocfilehash: 3b327581b0eb790e74d6fddc2bca1e027f40d89e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234590"
---
# <a name="compiler-warning-level-4-c4938"></a>Avertissement du compilateur (niveau 4) C4938

'var' : la variable de réduction à virgule flottante peut générer des résultats incohérents sous /fp:strict ou #pragma fenv_access

Vous ne devez pas utiliser [/fp:strict](../../build/reference/fp-specify-floating-point-behavior.md) ou [fenv_access](../../preprocessor/fenv-access.md) avec des réductions à virgule flottante OpenMP, car la somme est calculée dans un ordre différent. Par conséquent, les résultats peuvent différer des résultats obtenus sans /openmp.

L’exemple suivant génère l’avertissement C4938 :

```cpp
// C4938.cpp
// compile with: /openmp /W4 /fp:strict /c
// #pragma fenv_access(on)
extern double *a;

double test(int first, int last) {
   double sum = 0.0;
   #pragma omp parallel for reduction(+: sum)   // C4938
   for (int i = first ; i <= last ; ++i)
      sum += a[i];
   return sum;
}
```

Sans une parallélisation explicite, la somme est calculée comme suit :

```
sum = a[first] + a[first + 1] + ... + a[last];
```

Avec une parallélisation explicite (et deux threads), la somme est calculée comme suit :

```
sum1 = a[first] + ... a[first + last / 2];
sum2 = a[(first + last / 2) + 1] + ... a[last];
sum = sum1 + sum2;
```
