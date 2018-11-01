---
title: Erreur du compilateur C3044
ms.date: 11/04/2016
f1_keywords:
- C3044
helpviewer_keywords:
- C3044
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
ms.openlocfilehash: 0fb63d63ce9bdf0979382887164056dcdb288bd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648160"
---
# <a name="compiler-error-c3044"></a>Erreur du compilateur C3044

'section' : uniquement autorisé lors d’une imbrication directe sous une directive 'sections' OpenMP

Le compilateur a rencontré une directive `section` qui n’a pas été utilisée correctement. Pour plus d’informations, consultez [sections](../../parallel/openmp/reference/sections-openmp.md).

L’exemple suivant génère l’erreur C3044 :

```
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