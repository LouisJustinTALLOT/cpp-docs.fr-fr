---
title: Erreur du compilateur C3041
ms.date: 11/04/2016
f1_keywords:
- C3041
helpviewer_keywords:
- C3041
ms.assetid: 9df1ae44-3ac7-4c6c-899f-f35ffe7ccf0d
ms.openlocfilehash: 43f75e9d054f574eb121d20eb35d302cef849566
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182572"
---
# <a name="compiler-error-c3041"></a>Erreur du compilateur C3041

'variable' : la variable de la clause 'copyprivate' doit être privée dans un contexte englobant

Une variable passée à [copyprivate](../../parallel/openmp/reference/copyprivate.md) ne peut pas être partagée dans le contexte englobant.

L’exemple suivant génère l’erreur C3041 :

```
// C3041.cpp
// compile with: /openmp /c
#include "omp.h"
double d;
int main() {
   #pragma omp parallel shared(d)
   // try the following line instead
   // #pragma omp parallel private(d)
   {
      // or don't make d copyprivate
      #pragma omp single copyprivate(d)   // C3041
      {
      }
   }
}
```