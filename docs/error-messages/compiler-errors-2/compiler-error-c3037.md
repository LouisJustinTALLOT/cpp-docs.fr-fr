---
description: 'En savoir plus sur : erreur du compilateur C3037'
title: Erreur du compilateur C3037
ms.date: 11/04/2016
f1_keywords:
- C3037
helpviewer_keywords:
- C3037
ms.assetid: 9ba8a890-d3c7-4cce-93c5-d358e2bfad28
ms.openlocfilehash: f8ccf87ca09aaf90fb07b197279e994eeb27f249
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270054"
---
# <a name="compiler-error-c3037"></a>Erreur du compilateur C3037

'var' : la variable de la clause 'reduction' doit être partagée dans un contexte englobant

Une variable spécifiée dans une clause [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) ne peut pas être privée pour chaque thread dans le contexte.

L’exemple suivant génère l’erreur C3037 :

```cpp
// C3037.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel private(g_i)
   // try the following line instead
   // #pragma omp parallel
   {
      #pragma omp for reduction(+:g_i)   // C3037
      for (i = 0 ; i < 10 ; ++i) {
         g_i += i;
      }
   }
}
```
