---
description: 'En savoir plus sur : erreur du compilateur C3004'
title: Erreur du compilateur C3004
ms.date: 11/04/2016
f1_keywords:
- C3004
helpviewer_keywords:
- C3004
ms.assetid: 819c2b57-8366-4ca7-9135-1f0c5e5b6bb6
ms.openlocfilehash: 30737aca11b52fb8eaecc376c38211772442abf5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326026"
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
