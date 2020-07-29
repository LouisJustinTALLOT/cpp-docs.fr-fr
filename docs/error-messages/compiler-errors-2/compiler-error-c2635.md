---
title: Erreur du compilateur C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 7d3fc71a331d13416f65d841502fdd1d908653bd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225447"
---
# <a name="compiler-error-c2635"></a>Erreur du compilateur C2635

Impossible de convertir’identificateur1 * 'en’identificateur2 \* '; la conversion à partir d’une classe de base virtuelle est implicite

La conversion nécessite un cast d’une **`virtual`** classe de base vers une classe dérivée, ce qui n’est pas autorisé.

L’exemple suivant génère l’C2635 :

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
