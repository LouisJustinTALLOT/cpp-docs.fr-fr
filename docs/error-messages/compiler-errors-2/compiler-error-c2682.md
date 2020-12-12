---
description: 'En savoir plus sur : erreur du compilateur C2682'
title: Erreur du compilateur C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 962debb0227347abe97e290db724fdb227212914
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177430"
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
