---
title: Erreur du compilateur C3020 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3020
dev_langs:
- C++
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7f86d116c1a830db54490f3e5231d837d4246c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060640"
---
# <a name="compiler-error-c3020"></a>Erreur du compilateur C3020

'var' : variable d’index OpenMP 'boucle for' ne peut pas être modifié dans le corps de la boucle

Une OpenMP `for` boucle ne peut pas modifier l’index (compteur de boucle) dans le corps de la `for` boucle.

L’exemple suivant génère l’erreur C3020 :

```
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

Une variable déclarée avec [lastprivate](../../parallel/openmp/reference/lastprivate.md) ne peut pas être utilisé en tant que l’index à l’intérieur d’une boucle parallélisée.

L’exemple suivant sera C3020 pour la deuxième lastprivate, car celle-ci déclenche une écriture dans idx_a au sein de l’extérieur de la boucle. La première lastprivate n’entraîne pas une erreur, car elle déclenche une écriture idx_a plus à l’extérieur de la boucle (techniquement, tout en bas de la dernière itération). L’exemple suivant génère l’erreur C3020.

```
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

```
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