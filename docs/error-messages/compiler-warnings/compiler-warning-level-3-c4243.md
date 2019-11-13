---
title: Avertissement du compilateur (niveau 3) C4243
ms.date: 11/04/2016
f1_keywords:
- C4243
helpviewer_keywords:
- C4243
ms.assetid: ca72f9ad-ce0b-43a9-a68c-106e1f8b90ef
ms.openlocfilehash: ed5cc87f1bc376526f5129aa157c38a3f034b20b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051744"
---
# <a name="compiler-warning-level-3-c4243"></a>Avertissement du compilateur (niveau 3) C4243

la conversion’type de conversion’existe de’type1 'en’type2 ', mais n’est pas accessible

Un pointeur vers une classe dérivée est converti en pointeur vers une classe de base, mais la classe dérivée hérite de la classe de base avec un accès privé ou protégé.

L’exemple suivant génère l’C4243 :

```cpp
// C4243.cpp
// compile with: /W3
// C4243 expected
struct B {
   int f() {
      return 0;
   };
};

struct D : private B {};
struct E : public B {};

int main() {
   // Delete the following 2 lines to resolve.
   int (D::* d)() = (int(D::*)()) &B::f;
   d;

   int (E::* e)() = (int(E::*)()) &B::f; // OK
   e;
}
```