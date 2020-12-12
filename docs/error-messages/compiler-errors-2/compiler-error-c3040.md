---
description: 'En savoir plus sur : erreur du compilateur C3040'
title: Erreur du compilateur C3040
ms.date: 11/04/2016
f1_keywords:
- C3040
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
ms.openlocfilehash: e43f7e6e63d7ec2462247a9846febd4c0b4eab4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269930"
---
# <a name="compiler-error-c3040"></a>Erreur du compilateur C3040

'var' : le type de la variable de la clause 'reduction' est incompatible avec l’opérateur de réduction 'operator'

Une variable dans une clause [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) ne peut pas être utilisée avec l’opérateur de réduction.

L’exemple suivant génère l’erreur C3040 :

```cpp
// C3040.cpp
// compile with: /openmp /c
#include "omp.h"
double d;

int main() {
   #pragma omp parallel reduction(&:d)   // C3040
      ;

   #pragma omp parallel reduction(-:d)  // OK
      ;
}
```
