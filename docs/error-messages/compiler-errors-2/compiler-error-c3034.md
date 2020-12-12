---
description: 'En savoir plus sur : erreur du compilateur C3034'
title: Erreur du compilateur C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: 379fedfe3af65b2def83d737daeccac670838c2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270171"
---
# <a name="compiler-error-c3034"></a>Erreur du compilateur C3034

La directive OpenMP 'directive1' ne peut pas être directement imbriquée dans la directive 'directive2'

Certaines directives ne peuvent pas être imbriquées. Pour corriger cette erreur, vous pouvez fusionner les instructions des deux directives dans le bloc d'une directive ou construire des directives consécutives.

L’exemple suivant génère l’erreur C3034 :

```cpp
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```
