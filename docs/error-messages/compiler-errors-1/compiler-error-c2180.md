---
title: Erreur du compilateur C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 16fcf15eb29743f74bbf2edcb1016f2e15228e5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553316"
---
# <a name="compiler-error-c2180"></a>Erreur du compilateur C2180

l'expression de contrôle a le type 'type'

L'expression de contrôle dans une instruction `if`, `while`, `for` ou `do` est une expression convertie vers `void`. Pour résoudre ce problème, remplacez l'expression de contrôle par une expression qui génère un `bool` ou un type pouvant être converti en `bool`.

L'exemple suivant génère l'erreur C2180 :

```
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```