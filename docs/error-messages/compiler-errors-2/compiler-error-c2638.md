---
title: Erreur du compilateur C2638
ms.date: 11/04/2016
f1_keywords:
- C2638
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
ms.openlocfilehash: 0c4c1e73c97f51bb0e52a618829ffb0bed417a45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582774"
---
# <a name="compiler-error-c2638"></a>Erreur du compilateur C2638

'identificateur' : modificateur __based non conforme sur pointeur vers membre

Le `__based` modificateur ne peut pas être utilisé pour les pointeurs vers des membres.

L’exemple suivant génère l’erreur C2638 :

```
// C2638.cpp
void *a;

class C {
public:
   int i;
   int j;
   int func();
};
int __based (a) C::* cpi = &C::i;  // C2638
int (__based (a) C::* cpf)() = &C::func; // c2638
```