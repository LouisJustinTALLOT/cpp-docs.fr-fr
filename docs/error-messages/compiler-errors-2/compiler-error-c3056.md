---
description: 'En savoir plus sur : erreur du compilateur C3056'
title: Erreur du compilateur C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: d934221c4501256eb4bfd604bcc04534268de3fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269534"
---
# <a name="compiler-error-c3056"></a>Erreur du compilateur C3056

'symbol' : le symbole n’est pas dans la même portée avec la directive 'threadprivate'

Un symbole utilisé dans une clause [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) doit être dans la même portée que la clause `threadprivate` .

L’exemple suivant génère l’erreur C3056 :

```cpp
// C3056.cpp
// compile with: /openmp
int x, y;
void test() {
   #pragma omp threadprivate(x, y)   // C3056
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Solution possible :

```cpp
// C3056b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)
void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
