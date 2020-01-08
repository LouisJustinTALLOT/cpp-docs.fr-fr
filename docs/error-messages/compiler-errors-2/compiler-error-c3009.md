---
title: Erreur du compilateur C3009
ms.date: 11/04/2016
f1_keywords:
- C3009
helpviewer_keywords:
- C3009
ms.assetid: aded5985-f5fd-4c3e-a157-16be55ec1313
ms.openlocfilehash: 9d68a1c7568aefcd101ef48082c1c66f5b8627da
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302261"
---
# <a name="compiler-error-c3009"></a>Erreur du compilateur C3009

'étiquette' : saut dans le bloc structuré OpenMP non autorisé

Le code ne peut pas sauter dans ou hors d’un bloc OpenMP.

L’exemple suivant génère l’erreur C3009 :

```c
// C3009.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
   lbl2:;
   }
   goto lbl2;   // C3009
}
```
