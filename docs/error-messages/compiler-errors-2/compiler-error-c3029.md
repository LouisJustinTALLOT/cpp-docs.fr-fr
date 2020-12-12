---
description: 'En savoir plus sur : erreur du compilateur C3029'
title: Erreur du compilateur C3029
ms.date: 11/04/2016
f1_keywords:
- C3029
helpviewer_keywords:
- C3029
ms.assetid: 655eb04d-504a-468d-8c0c-bda1e5f297b7
ms.openlocfilehash: ec9164c43dd44e4fe69273c2cad7c3e6beead394
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174180"
---
# <a name="compiler-error-c3029"></a>Erreur du compilateur C3029

'symbol' : ne peut figurer qu’une seule fois dans les clauses de partage de données d’une directive OpenMP

Un symbole a été utilisé plusieurs fois dans une ou plusieurs clauses d’une directive. Le symbole ne peut être utilisé qu’une seule fois dans la directive.

L’exemple suivant génère l’erreur C3029 :

```cpp
// C3029.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

int g_i;

int main() {
   int i, x;

   #pragma omp parallel reduction(+ : x, x)   // C3029
      ;

   #pragma omp parallel reduction(+ : x)   // OK
      ;

   #pragma omp parallel private(x) reduction(+ : x)   // C3029
      ;

   #pragma omp parallel reduction(+ : x)   // OK
      ;
}
```
