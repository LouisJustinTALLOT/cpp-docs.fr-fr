---
title: Compilateur avertissement (niveau 4) C4938 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4938
dev_langs:
- C++
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e140f3885aec66d01d5f7e28245c10e952bedde3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107440"
---
# <a name="compiler-warning-level-4-c4938"></a>Avertissement du compilateur (niveau 4) C4938

'var' : la variable de réduction à virgule flottante peut générer des résultats incohérents sous /fp:strict ou #pragma fenv_access

Vous ne devez pas utiliser [/fp:strict](../../build/reference/fp-specify-floating-point-behavior.md) ou [fenv_access](../../preprocessor/fenv-access.md) avec des réductions à virgule flottante OpenMP, car la somme est calculée dans un ordre différent. Par conséquent, les résultats peuvent différer des résultats obtenus sans /openmp.

L’exemple suivant génère l’avertissement C4938 :

```
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