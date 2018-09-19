---
title: Erreur du compilateur C3040 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3040
dev_langs:
- C++
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 419178a7ff71817c418aa791ae1f6cce116cd986
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057689"
---
# <a name="compiler-error-c3040"></a>Erreur du compilateur C3040

'var' : le type de la variable de la clause 'reduction' est incompatible avec l’opérateur de réduction 'operator'

Une variable dans une clause [reduction](../../parallel/openmp/reference/reduction.md) ne peut pas être utilisée avec l’opérateur de réduction.

L’exemple suivant génère l’erreur C3040 :

```
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