---
description: 'En savoir plus sur : erreur du compilateur C2638'
title: Erreur du compilateur C2638
ms.date: 11/04/2016
f1_keywords:
- C2638
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
ms.openlocfilehash: 82921314b8861239e1686c95f8a0c3bc4eb41082
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272446"
---
# <a name="compiler-error-c2638"></a>Erreur du compilateur C2638

'identificateur' : modificateur de __based non conforme sur un pointeur vers un membre

Le **`__based`** modificateur ne peut pas être utilisé pour les pointeurs vers des membres.

L’exemple suivant génère l’C2638 :

```cpp
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
