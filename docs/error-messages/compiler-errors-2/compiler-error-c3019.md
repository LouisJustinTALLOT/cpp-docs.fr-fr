---
title: Erreur du compilateur C3019
ms.date: 11/04/2016
f1_keywords:
- C3019
helpviewer_keywords:
- C3019
ms.assetid: 31a6d9b6-d29f-4499-9ad8-48dd751e87c7
ms.openlocfilehash: 15b2dbf55b18c50020140eae25a71b18ceb10b10
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742130"
---
# <a name="compiler-error-c3019"></a>Erreur du compilateur C3019

forme incorrecte de l’incrément dans l’instruction’for’OpenMP

La partie incrément d’une boucle `for` OpenMP doit utiliser la variable d’index à la fois à gauche et à droite de l’opérateur.

L’exemple suivant génère l’C3019 :

```cpp
// C3019.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 1, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i = j + n)   // C3019
      // Try the following line instead:
      // for (i = 0; i < 10; i++)
         j *= 2;
   }
}
```
