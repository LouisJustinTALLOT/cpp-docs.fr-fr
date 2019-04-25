---
title: Erreur du compilateur C3008
ms.date: 11/04/2016
f1_keywords:
- C3008
helpviewer_keywords:
- C3008
ms.assetid: 04d93201-28e5-4be0-945c-aad616376f4b
ms.openlocfilehash: 4f3b0e8ec935a4425977ea89993677704681a9e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165148"
---
# <a name="compiler-error-c3008"></a>Erreur du compilateur C3008

'arg' : une parenthèse fermante ')' est manquante dans une directive 'directive' OpenMP

Une directive OpenMP qui prend un argument n’avait pas de parenthèse fermante.

L’exemple suivant génère l’erreur C3008 :

```
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