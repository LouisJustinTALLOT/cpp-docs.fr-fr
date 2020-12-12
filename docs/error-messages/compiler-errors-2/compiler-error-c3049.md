---
description: 'En savoir plus sur : erreur du compilateur C3049'
title: Erreur du compilateur C3049
ms.date: 11/04/2016
f1_keywords:
- C3049
helpviewer_keywords:
- C3049
ms.assetid: 6ddf54f6-2c30-4d04-b637-98c6c922c533
ms.openlocfilehash: dc2409fccc8938bb4344afe04ad0fcb120e28a7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269677"
---
# <a name="compiler-error-c3049"></a>Erreur du compilateur C3049

'arg' : argument non valide dans la clause 'default' OpenMP

Une valeur incorrecte a été passée à une clause [default](../../parallel/openmp/reference/openmp-clauses.md#default-openmp) .

L’exemple suivant génère l’erreur C3049 :

```cpp
// C3049.cpp
// compile with: /openmp /c
int main() {
   int n1 = 1;

   #pragma omp parallel default(private)   // C3049
   // try the following line instead
   // #pragma omp parallel default(shared)
   {
      ++n1;
   }
}
```
