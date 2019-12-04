---
title: Erreur du compilateur C3059
ms.date: 11/04/2016
f1_keywords:
- C3059
helpviewer_keywords:
- C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
ms.openlocfilehash: 897ed2beb7634cec787f0776616d9a60596a979f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756459"
---
# <a name="compiler-error-c3059"></a>Erreur du compilateur C3059

'var' : le symbole 'threadprivate' ne peut pas être utilisé dans la clause 'clause'

Un symbole [threadprivate](../../parallel/openmp/reference/threadprivate.md) a été utilisé dans une clause.

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
