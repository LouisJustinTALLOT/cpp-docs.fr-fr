---
title: Erreur du compilateur C3017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3017
dev_langs:
- C++
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 694c4f57df22184c1a6981953d1057252c94030a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061680"
---
# <a name="compiler-error-c3017"></a>Erreur du compilateur C3017

forme incorrecte du test de fin dans l'instruction 'for' OpenMP

Une boucle `for` dans une instruction OpenMP doit être spécifiée complètement et explicitement.

L’exemple suivant génère l’erreur C3017 :

```
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```