---
description: 'En savoir plus sur : erreur du compilateur C3018'
title: Erreur du compilateur C3018
ms.date: 11/04/2016
f1_keywords:
- C3018
helpviewer_keywords:
- C3018
ms.assetid: 685be45f-f116-43a8-a88d-05ab6616e2f1
ms.openlocfilehash: cb2b144a09edc4dbe64f4940e476cca0f73c585b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285823"
---
# <a name="compiler-error-c3018"></a>Erreur du compilateur C3018

'var1' : le test ou l’incrément de l’instruction 'for' OpenMP doivent utiliser la variable d’index 'var2'

Une **`for`** boucle dans une instruction OpenMP doit utiliser la même variable pour son test et l’incrémentation que celle qu’elle utilise pour son index.

L’exemple suivant génère l’erreur C3018 :

```cpp
// C3018.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 5;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; j < 10; ++i)   // C3018
      // try the following line instead
      // for (i = 0; i < 10; ++i)
         j *= 2;

      #pragma omp for
      for (i = 0; i < 10; j = j + i)   // C3018
      // try the following line instead
      // for (i = 0; i < 10; i = j + i)
         j *= 2;
   }
}
```
