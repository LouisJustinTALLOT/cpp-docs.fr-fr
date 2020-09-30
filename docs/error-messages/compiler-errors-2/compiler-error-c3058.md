---
title: Erreur du compilateur C3058
ms.date: 11/04/2016
f1_keywords:
- C3058
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
ms.openlocfilehash: 2c0615f78bf9068311ec691f70c4c1a60ef728b0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501473"
---
# <a name="compiler-error-c3058"></a>Erreur du compilateur C3058

'symbol' : symbole non déclaré en tant que 'threadprivate' avant d’être utilisé dans la clause 'copyin'

Un symbole doit d’abord être déclaré en tant que [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) avant de pouvoir être utilisé dans une clause [copyin](../../parallel/openmp/reference/openmp-clauses.md#copyin) .

L’exemple suivant génère l’erreur C3058 :

```cpp
// C3058.cpp
// compile with: /openmp
int x, y, z;
#pragma omp threadprivate(x, z)

void test() {
   #pragma omp parallel copyin(x, y)   // C3058
   {
   }
}
```

Solution possible :

```cpp
// C3058b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
   }
}
```
