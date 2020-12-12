---
description: 'En savoir plus sur : erreur du compilateur C3055'
title: Erreur du compilateur C3055
ms.date: 11/04/2016
f1_keywords:
- C3055
helpviewer_keywords:
- C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
ms.openlocfilehash: 6c75d476abf7535499c74705e4a0ec77d80dc772
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269573"
---
# <a name="compiler-error-c3055"></a>Erreur du compilateur C3055

'symbole' : impossible de référencer le symbole avant qu’il ne soit utilisé dans la directive 'threadprivate'

Un symbole a été référencé puis utilisé dans une clause [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) , ce qui n’est pas autorisé.

L’exemple suivant génère l’erreur C3055 :

```cpp
// C3055.cpp
// compile with: /openmp
int x, y;
int z = x;
#pragma omp threadprivate(x, y)   // C3055

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Solution possible :

```cpp
// C3055b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
