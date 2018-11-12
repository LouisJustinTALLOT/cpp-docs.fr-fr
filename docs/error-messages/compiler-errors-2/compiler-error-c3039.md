---
title: Erreur du compilateur C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: 69be1b25254119108e517cee2f1e14368e0163f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511616"
---
# <a name="compiler-error-c3039"></a>Erreur du compilateur C3039

'var' : la variable d’index de l’instruction 'for' OpenMP ne peut pas être une variable de réduction

Une variable d’index est implicitement privée. Elle ne peut donc pas être utilisée dans une clause [reduction](../../parallel/openmp/reference/reduction.md) dans la directive [parallel](../../parallel/openmp/reference/parallel.md) englobante.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3039 :

```
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```