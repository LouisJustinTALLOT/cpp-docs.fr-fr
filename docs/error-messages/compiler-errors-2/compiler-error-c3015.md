---
description: 'En savoir plus sur : erreur du compilateur C3015'
title: Erreur du compilateur C3015
ms.date: 11/04/2016
f1_keywords:
- C3015
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
ms.openlocfilehash: 84d1431ef04b16631ba6f32aa9b41dc08cef8f2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285875"
---
# <a name="compiler-error-c3015"></a>Erreur du compilateur C3015

forme incorrecte de l'initialisation dans l'instruction 'for' OpenMP

Une **`for`** boucle dans une instruction OpenMP doit être spécifiée de manière explicite et complète.

L’exemple suivant génère l’erreur C3015 :

```cpp
// C3015.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (; i < 0; i += j)   // C3015
      // Try the following line instead:
      // for (i = 0; i < 0; i++)
         --j;
   }
}
```
