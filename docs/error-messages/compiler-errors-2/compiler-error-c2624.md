---
title: Erreur du compilateur C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: 407629ad2eecd0d3ca6081fefa59ddd60702f913
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456717"
---
# <a name="compiler-error-c2624"></a>Erreur du compilateur C2624

les classes locales ne peut pas être utilisés pour déclarer des variables 'extern'

Une classe locale ou une structure ne peut pas être utilisé pour déclarer `extern` variables.

L’exemple suivant génère l’erreur C2624 :

```
// C2624.cpp
int main() {
   struct C {};
   extern C ac;   // C2624
}
```