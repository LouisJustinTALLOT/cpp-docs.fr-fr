---
description: 'En savoir plus sur : erreur du compilateur C3038'
title: Erreur du compilateur C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: bcc038ac21807b7d98ec98fa76004d658ef0216d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270067"
---
# <a name="compiler-error-c3038"></a>Erreur du compilateur C3038

'var' : la variable de la clause 'private' ne peut pas être une variable de réduction dans un contexte englobant

Les variables qui apparaissent dans la clause [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) d’une directive parallèle ne peuvent pas être spécifiées dans une clause [private](../../parallel/openmp/reference/openmp-clauses.md#private-openmp) d’une directive de partage de travail qui est liée à la construction parallèle.

L’exemple suivant génère l’erreur C3038 :

```cpp
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```
