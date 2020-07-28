---
title: Erreur du compilateur C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 2697ce5a790fffe762d97ca3380853514de6d437
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220260"
---
# <a name="compiler-error-c2682"></a>Erreur du compilateur C2682

Impossible d’utiliser casting_operator pour convertir de’type1 'en’type2 '

Un opérateur de cast a essayé de convertir les types incompatibles. Par exemple, vous ne pouvez pas utiliser l’opérateur [dynamic_cast](../../cpp/dynamic-cast-operator.md) pour convertir un pointeur en référence. L' **`dynamic_cast`** opérateur ne peut pas être utilisé pour effectuer un cast de qualificateurs. Tous les qualificateurs sur les types doivent correspondre.

Vous pouvez utiliser l' **`const_cast`** opérateur pour supprimer des attributs tels que **`const`** , **`volatile`** ou **`__unaligned`** .

L’exemple suivant génère l’C2682 :

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

L’exemple suivant génère l’C2682 :

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
