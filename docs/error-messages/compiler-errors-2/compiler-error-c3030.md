---
title: Erreur du compilateur C3030
ms.date: 11/04/2016
f1_keywords:
- C3030
helpviewer_keywords:
- C3030
ms.assetid: de92fd7e-29ba-46e8-b43b-f4b985cd74de
ms.openlocfilehash: 31ae3f55cd0bf7a15dbea2cf941b00dc048d825d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598378"
---
# <a name="compiler-error-c3030"></a>Erreur du compilateur C3030

'variable' : la variable de la clause/directive 'reduction' ne peut pas avoir un type référence

Vous pouvez uniquement passer des paramètres de valeur à certaines clauses, telles que la clause reduction.

L’exemple suivant génère l’erreur C3030 :

```
// C3030.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

void test(int &r) {
   #pragma omp parallel reduction(+ : r)   // C3030
      ;
}

void test2(int r) {
   #pragma omp parallel reduction(+ : r)   // OK
      ;
}

int main(int argc, char** argv) {
   int& r = *((int*)argv);
   int s = *((int*)argv);

   #pragma omp parallel reduction(+ : r)   // C3030
      ;

   #pragma omp parallel reduction(+ : s)   // OK
      ;
}
```