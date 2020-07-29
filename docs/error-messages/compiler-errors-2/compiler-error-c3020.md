---
title: Erreur du compilateur C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: 89b28ae396322859596b99ba56a28375e9c9d6d5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232025"
---
# <a name="compiler-error-c3020"></a>Erreur du compilateur C3020

'var' : la variable d’index de la boucle’for’OpenMP ne peut pas être modifiée dans le corps de la boucle

Une **`for`** boucle OpenMP ne peut pas modifier l’index (compteur de boucle) dans le corps de la **`for`** boucle.

L’exemple suivant génère l’C3020 :

```cpp
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

Une variable déclarée avec [lastprivate](../../parallel/openmp/reference/lastprivate.md) ne peut pas être utilisée en tant qu’index à l’intérieur d’une boucle parallélisée.

L’exemple suivant donnera C3020 pour le deuxième lastprivate, car ce lastprivate déclenchera une écriture sur idx_a dans la boucle for la plus extérieure. Le premier lastprivate ne génère pas d’erreur, car ce lastprivate déclenche une écriture sur idx_a en dehors de la boucle for la plus externe (techniquement, à la fin de la dernière itération). L’exemple suivant génère l’C3020.

```cpp
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

L’exemple suivant illustre une résolution possible :

```cpp
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```
