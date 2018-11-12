---
title: A.22   Utilisation de la clause default(none)
ms.date: 11/04/2016
ms.assetid: a3fa4e62-1e92-4896-ae3f-be268067d917
ms.openlocfilehash: 55440f9bcce09878a497ea4ee39a6b5478703cd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523913"
---
# <a name="a22---using-the-defaultnone-clause"></a>A.22   Utilisation de la clause default(none)

L’exemple suivant permet de distinguer les variables qui sont affectés par la `default(none)` clause de celles qui ne sont pas :

```
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

Pour plus d’informations sur la `default` clause, consultez [Section 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) sur la page 28.