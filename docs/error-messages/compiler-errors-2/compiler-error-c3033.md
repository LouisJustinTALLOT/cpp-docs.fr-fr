---
title: Erreur du compilateur C3033
ms.date: 11/04/2016
f1_keywords:
- C3033
helpviewer_keywords:
- C3033
ms.assetid: 8628b6bb-a650-4ed2-af13-57acd2f7ddbb
ms.openlocfilehash: df3e3f8472d1c274049e686de93488d556ff6f1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232012"
---
# <a name="compiler-error-c3033"></a>Erreur du compilateur C3033

'var' : la variable de la clause 'clause' ne peut pas avoir un type qualifié const

Les valeurs passées à certaines clauses ne peuvent pas être des **`const`** variables.

L’exemple suivant génère l’erreur C3033 :

```cpp
// C3033.cpp
// compile with: /openmp /link vcomps.lib
int main() {
   const int val = 1;
   int val2 = 1;

   #pragma omp parallel reduction(+ : val)   // C3033
   ;

   #pragma omp parallel reduction(+ : val2)   // OK
   ;
}
```
