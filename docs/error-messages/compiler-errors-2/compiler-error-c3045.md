---
description: 'En savoir plus sur : erreur du compilateur C3045'
title: Erreur du compilateur C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: 0d39399d656a482d401eafb51f53c177c8c3bb2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269846"
---
# <a name="compiler-error-c3045"></a>Erreur du compilateur C3045

Instruction composée attendue à la suite de la directive 'sections' OpenMP. Accolade '{' manquante

Un bloc de code délimité par des accolades doit suivre une directive [sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) .

L’exemple suivant génère l’erreur C3045 :

```cpp
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```
