---
title: Erreur du compilateur C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: 407629ad2eecd0d3ca6081fefa59ddd60702f913
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395480"
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