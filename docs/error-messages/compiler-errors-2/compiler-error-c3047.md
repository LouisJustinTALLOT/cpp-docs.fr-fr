---
description: 'En savoir plus sur : erreur du compilateur C3047'
title: Erreur du compilateur C3047
ms.date: 11/04/2016
f1_keywords:
- C3047
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
ms.openlocfilehash: 471f85f6a73e911ea9c308a3de9d2afbe800f750
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269781"
---
# <a name="compiler-error-c3047"></a>Erreur du compilateur C3047

Le bloc structuré d'une région 'sections' OpenMP doit être précédé de '#pragma omp section'

Tout code contenu dans un bloc de code introduit par une directive [sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) doit se trouver dans un bloc de code introduit par une directive `section` .

L’exemple suivant génère l’erreur C3047 :

```cpp
// C3047.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {

         #pragma omp section
         {
            ++n3;
         }

         ++n2;   // C3047 not enclosed in #pragma omp section
      }
   }
}
```
