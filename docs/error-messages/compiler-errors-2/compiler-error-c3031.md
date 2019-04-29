---
title: Erreur du compilateur C3031
ms.date: 11/04/2016
f1_keywords:
- C3031
helpviewer_keywords:
- C3031
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
ms.openlocfilehash: 848577239d24df3f6af38438fb42c372ef34b1ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265853"
---
# <a name="compiler-error-c3031"></a>Erreur du compilateur C3031

'variable' : la variable de la clause 'reduction' doit avoir un type arithmétique scalaire

Une variable du mauvais type a été passée à une clause reduction.

L’exemple suivant génère l’erreur C3031 :

```
// C3031.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

typedef struct {
   int n;
} Incomplete;

extern Incomplete inc;
int i = 9;

int main() {
   #pragma omp parallel reduction(+: inc)   // C3031
      ;

   #pragma omp parallel reduction(+: i)     // OK
      ;
}
```