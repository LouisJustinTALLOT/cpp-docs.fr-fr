---
title: Erreur du compilateur C3016 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3016
dev_langs:
- C++
helpviewer_keywords:
- C3016
ms.assetid: 3423467e-e8bb-4f35-b4db-7925cafa74c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d77686f669dcd767a1d79c0ac60360f1bb2aa81b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047549"
---
# <a name="compiler-error-c3016"></a>Erreur du compilateur C3016

'var' : la variable d’index de l’instruction 'for' OpenMP doit disposer d’un type intégral signé

La variable d’index dans une instruction `for` OpenMP doit être un type intégral signé.

L’exemple suivant génère l’erreur C3016 :

```
// C3016.cpp
// compile with: /openmp
int main()
{
   #pragma omp parallel
   {
      unsigned int i = 0;
      // Try the following line instead:
      // int i = 0;

      #pragma omp for
      for (i = 0; i <= 10; ++i)   // C3016
      {
      }
   }
}
```