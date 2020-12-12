---
description: 'En savoir plus sur : erreur du compilateur C3008'
title: Erreur du compilateur C3008
ms.date: 11/04/2016
f1_keywords:
- C3008
helpviewer_keywords:
- C3008
ms.assetid: 04d93201-28e5-4be0-945c-aad616376f4b
ms.openlocfilehash: 30ec8602ba9759eded7edc642931109216a68967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305336"
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
