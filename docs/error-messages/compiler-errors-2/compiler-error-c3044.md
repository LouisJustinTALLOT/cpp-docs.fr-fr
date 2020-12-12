---
description: 'En savoir plus sur : erreur du compilateur C3044'
title: Erreur du compilateur C3044
ms.date: 11/04/2016
f1_keywords:
- C3044
helpviewer_keywords:
- C3044
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
ms.openlocfilehash: e206a30457e5ef31d4d17886f30b928ceb42816f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269872"
---
# <a name="compiler-error-c3044"></a>Erreur du compilateur C3044

'section' : uniquement autorisé lors d’une imbrication directe sous une directive 'sections' OpenMP

Le compilateur a rencontré une directive `section` qui n’a pas été utilisée correctement. Pour plus d’informations, consultez la [section sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp).

L’exemple suivant génère l’erreur C3044 :

```cpp
// C3044.cpp
// compile with: /openmp /c
#include "omp.h"
int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         ++n2;
      }

      #pragma omp section   // C3044
      {
         ++n3;
      }
   }

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         #pragma omp section   // OK
         {
            ++n3;
         }
      }
   }
}
```
