---
title: Erreur du compilateur C3010
ms.date: 11/04/2016
f1_keywords:
- C3010
helpviewer_keywords:
- C3010
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
ms.openlocfilehash: c5f0d33632cb155b8365c8de421fa5eaf91421c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455495"
---
# <a name="compiler-error-c3010"></a>Erreur du compilateur C3010

'étiquette' : saut hors du bloc structuré OpenMP non autorisé

Le code ne peut pas sauter dans ou hors d’un bloc OpenMP.

L’exemple suivant génère l’erreur C3010 :

```
// C3010.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
      #pragma omp parallel
      {
         goto lbl3;
      }
   }
   lbl3:;   // C3010
}
```