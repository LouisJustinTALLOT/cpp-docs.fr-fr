---
title: Erreur du compilateur C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 8cd27f492a72277c383afa5ca335a073b1a0519c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506391"
---
# <a name="compiler-error-c3042"></a>Erreur du compilateur C3042

les clauses 'copyprivate' et 'nowait' ne peuvent pas figurer en même temps dans la directive 'directive' OpenMP

Les clauses [copyprivate](../../parallel/openmp/reference/openmp-clauses.md#copyprivate) et [nowait](../../parallel/openmp/reference/openmp-clauses.md#nowait) s’excluent mutuellement sur la directive spécifiée. Pour corriger cette erreur, supprimez l’une des clauses `copyprivate` ou `nowait` ou les deux.

L’exemple suivant génère l’erreur C3042 :

```cpp
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```
