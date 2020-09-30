---
title: Erreur du compilateur C3059
ms.date: 11/04/2016
f1_keywords:
- C3059
helpviewer_keywords:
- C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
ms.openlocfilehash: 9b1efc0969373b6a91b0800ae71477b2371814bb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501434"
---
# <a name="compiler-error-c3059"></a>Erreur du compilateur C3059

'var' : le symbole 'threadprivate' ne peut pas être utilisé dans la clause 'clause'

Un symbole [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) a été utilisé dans une clause.

L’exemple suivant génère l’erreur C3059 :

```cpp
// C3059.cpp
// compile with: /openmp
#include "omp.h"
int x, y;
#pragma omp threadprivate(x, y)

int main() {
   #pragma omp parallel private(x, y)   // C3059
   {
      x = y;
   }
}
```

Solution possible :

```cpp
// C3059b.cpp
// compile with: /openmp
#include "omp.h"
int x = 0, y = 0;

int main() {
   #pragma omp parallel firstprivate(y) private(x)
   {
      x = y;
   }
}
```
