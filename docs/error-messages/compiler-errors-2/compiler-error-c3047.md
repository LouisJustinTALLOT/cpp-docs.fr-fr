---
title: Erreur du compilateur C3047
ms.date: 11/04/2016
f1_keywords:
- C3047
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
ms.openlocfilehash: c6b8530aa1a1d5b8a0bfa735a9cc759a698ae841
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761323"
---
# <a name="compiler-error-c3047"></a>Erreur du compilateur C3047

Le bloc structuré d'une région 'sections' OpenMP doit être précédé de '#pragma omp section'

Tout code contenu dans un bloc de code introduit par une directive [sections](../../parallel/openmp/reference/sections-openmp.md) doit se trouver dans un bloc de code introduit par une directive `section` .

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
