---
description: 'En savoir plus sur : erreur du compilateur C3033'
title: Erreur du compilateur C3033
ms.date: 11/04/2016
f1_keywords:
- C3033
helpviewer_keywords:
- C3033
ms.assetid: 8628b6bb-a650-4ed2-af13-57acd2f7ddbb
ms.openlocfilehash: 999cedd270470bde27a57be0159eedda61297092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270236"
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
