---
title: Erreur du compilateur C3022 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3022
dev_langs:
- C++
helpviewer_keywords:
- C3022
ms.assetid: 9f1d444c-6c6e-48d9-9346-69128390aa33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ce4a6cbc0a6cb90cf022c7bfc18295694b4d5e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065229"
---
# <a name="compiler-error-c3022"></a>Erreur du compilateur C3022

'clause' : genre de planification de 'value' non valide dans la directive 'directive' OpenMP

Une valeur non prise en charge a été passée à une clause.

L’exemple suivant génère l’erreur C3022 :

```
// C3022.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(10)   // C3022
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(x)   // C3022
   for (i = 0; i < 10; ++i) ;

   // OK
   #pragma omp parallel for schedule(runtime)
   for (i = 0; i < 10; ++i)
   ;
}
```