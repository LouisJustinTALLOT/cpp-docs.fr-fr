---
description: 'En savoir plus sur : erreur du compilateur C3023'
title: Erreur du compilateur C3023
ms.date: 11/04/2016
f1_keywords:
- C3023
helpviewer_keywords:
- C3023
ms.assetid: 89dcce98-3cd7-4931-a50f-87df1d2ebc9b
ms.openlocfilehash: e9cd560610327afe1dabc2b6899d1e0290779ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174336"
---
# <a name="compiler-error-c3023"></a>Erreur du compilateur C3023

'valeur' : jeton inattendu rencontré dans l’argument de la clause 'clause' OpenMP

Les valeurs passées à une clause ne sont pas valides.

L’exemple suivant génère l’erreur C3023 :

```cpp
// C3023.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(dynamic 10)   // C3023
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(dynamic;10)   // C3023
   for (i = 0; i < 10; ++i) ;

   // OK
   #pragma omp parallel for schedule(dynamic, 10)
   for (i = 0; i < 10; ++i)
   ;
}
```
