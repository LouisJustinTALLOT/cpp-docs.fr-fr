---
description: 'En savoir plus sur : erreur du compilateur C3016'
title: Erreur du compilateur C3016
ms.date: 11/04/2016
f1_keywords:
- C3016
helpviewer_keywords:
- C3016
ms.assetid: 3423467e-e8bb-4f35-b4db-7925cafa74c1
ms.openlocfilehash: e45425946993caa43cfaf1a19730ef5414a6f2d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285862"
---
# <a name="compiler-error-c3016"></a>Erreur du compilateur C3016

'var' : la variable d’index de l’instruction 'for' OpenMP doit disposer d’un type intégral signé

La variable d’index dans une **`for`** instruction OpenMP doit être un type intégral signé.

L’exemple suivant génère l’erreur C3016 :

```cpp
// C3016.cpp
// compile with: /openmp
int main()
{
   #pragma omp parallel
   {
      unsigned int i = 0;
      // Try the following line instead:
      // int i = 0;

      #pragma omp for
      for (i = 0; i <= 10; ++i)   // C3016
      {
      }
   }
}
```
