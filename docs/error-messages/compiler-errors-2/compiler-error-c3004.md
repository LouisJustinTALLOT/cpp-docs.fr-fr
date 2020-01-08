---
title: Erreur du compilateur C3004
ms.date: 11/04/2016
f1_keywords:
- C3004
helpviewer_keywords:
- C3004
ms.assetid: 819c2b57-8366-4ca7-9135-1f0c5e5b6bb6
ms.openlocfilehash: cb5fe5572774c77d4f9f982e271dce8c2d986300
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302287"
---
# <a name="compiler-error-c3004"></a>Erreur du compilateur C3004

'clause' : clause non valide sur la directive 'directive' OpenMP

Une clause OpenMP a été utilisée sur une directive pour laquelle elle n’est pas activée.

L’exemple suivant génère l’erreur C3004 :

```c
// C3004.c
// compile with: /openmp
int main()
{
   int x, y, z;

   // Shared clause not allowed for 'single' directive.
   #pragma omp single shared(x, y)   // C3004

   x = y;
}
```
