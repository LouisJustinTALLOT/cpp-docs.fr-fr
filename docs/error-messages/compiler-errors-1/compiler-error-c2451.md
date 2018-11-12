---
title: Erreur du compilateur C2451
ms.date: 11/04/2016
f1_keywords:
- C2451
helpviewer_keywords:
- C2451
ms.assetid: a64c93a5-ab8d-4d39-ae57-9ee7ef803036
ms.openlocfilehash: bd69861b42e14ae30b4d57658719e7a2ce3617ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487189"
---
# <a name="compiler-error-c2451"></a>Erreur du compilateur C2451

expression conditionnelle de type 'type' n’est pas conforme

L’expression conditionnelle correspond à un type entier.

L’exemple suivant génère l’erreur C2451 :

```
// C2451.cpp
class B {};

int main () {
   B b1;
   int i = 0;
   if (b1)   // C2451
   // try the following line instead
   // if (i)
      ;
}
```