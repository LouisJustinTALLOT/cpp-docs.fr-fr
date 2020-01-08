---
title: Erreur du compilateur C3008
ms.date: 11/04/2016
f1_keywords:
- C3008
helpviewer_keywords:
- C3008
ms.assetid: 04d93201-28e5-4be0-945c-aad616376f4b
ms.openlocfilehash: 6af62620fcc25abbe69062256938656781437252
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298868"
---
# <a name="compiler-error-c3008"></a>Erreur du compilateur C3008

'arg' : une parenthèse fermante ')' est manquante dans une directive 'directive' OpenMP

Une directive OpenMP qui prend un argument n’avait pas de parenthèse fermante.

L’exemple suivant génère l’erreur C3008 :

```c
// C3008.c
// compile with: /openmp
int main()
{
   int x, y, z;
   #pragma omp parallel shared(x   // C3008
   // Try the following line instead:
   #pragma omp parallel shared(x)
   {
   }
}
```
