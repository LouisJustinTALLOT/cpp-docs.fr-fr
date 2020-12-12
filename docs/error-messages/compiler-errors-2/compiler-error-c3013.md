---
description: 'En savoir plus sur : erreur du compilateur C3013'
title: Erreur du compilateur C3013
ms.date: 11/04/2016
f1_keywords:
- C3013
helpviewer_keywords:
- C3013
ms.assetid: f896777d-27e6-4b6d-baab-1567317f3374
ms.openlocfilehash: 4c84cce635516ee62533c83716708b9075077eb8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285966"
---
# <a name="compiler-error-c3013"></a>Erreur du compilateur C3013

'clause' : la clause ne peut apparaître qu’une seule fois dans la directive 'directive' OpenMP

Une clause apparaît deux fois dans la même directive. Supprimez une occurrence de la clause.

L’exemple suivant génère l’erreur C3013 :

```cpp
// C3013.cpp
// compile with: /openmp
int main() {
   int a, b, c, x, y, z;

   #pragma omp parallel shared(a,b,c) private(x)

   #pragma omp for nowait private(x) nowait   // C3013
   // The previous line generates C3013, with two nowait clauses
   // try the following line instead:
   // #pragma omp for nowait private(x)
   for (a = 0 ; a < 10 ; ++a) {
   }
}
```
