---
title: Erreur du compilateur C3036 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3036
dev_langs:
- C++
helpviewer_keywords:
- C3036
ms.assetid: 10c6993e-bc42-4a07-85c7-cdc34ac30906
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecf2b17b7b7db96f4ce8756ec9248a4c6cb9ef78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068069"
---
# <a name="compiler-error-c3036"></a>Erreur du compilateur C3036

'opérateur' : jeton d’opérateur non valide dans la clause 'reduction' OpenMP

Une clause [reduction](../../parallel/openmp/reference/reduction.md) n’a pas été spécifiée correctement.

L’exemple suivant génère l’erreur C3036 :

```
// C3036.cpp
// compile with: /openmp
static float a[1000], b[1000], c[1000];
void test1(int first, int last) {
   static float dp = 0.0f;
   #pragma omp for nowait reduction(.:dp)   // C3036
   // try the following line instead
   // #pragma omp for nowait reduction(+: dp)
   for (int i = first ; i <= last ; ++i)
      dp += a[i] * b[i];
}
```