---
title: Erreur du compilateur C3002
ms.date: 11/04/2016
f1_keywords:
- C3002
helpviewer_keywords:
- C3002
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
ms.openlocfilehash: 9f48021f5a32006c6a78a69500b0701cb7612d96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451127"
---
# <a name="compiler-error-c3002"></a>Erreur du compilateur C3002

'name1 name2' : plusieurs noms de directive OpenMP

Plusieurs noms de directive ne sont pas autorisés.

L’exemple suivant génère l’erreur C3002 :

```
// C3002.c
// compile with: /openmp
int main()
{
   #pragma omp parallel single   // C3002
}
```