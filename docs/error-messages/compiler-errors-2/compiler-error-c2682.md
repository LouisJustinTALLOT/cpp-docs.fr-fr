---
title: Erreur du compilateur C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 8a9ec2f59f362df284e9bd5cd8df6ae986d59d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266268"
---
# <a name="compiler-error-c2682"></a>Erreur du compilateur C2682

Impossible d’utiliser ' opérateur_casting ' pour convertir de 'type1' en 'type2'

Un opérateur de cast a essayé d’effectuer une conversion entre des types incompatibles. Par exemple, vous ne pouvez pas utiliser le [dynamic_cast](../../cpp/dynamic-cast-operator.md) pour convertir un pointeur vers une référence. Le `dynamic_cast` opérateur ne peut pas être utilisé pour modifier le cast des qualificateurs. Tous les qualificateurs sur les types doivent correspondre.

Vous pouvez utiliser la `const_cast` opérateur à supprimer des attributs tels que `const`, `volatile`, ou `__unaligned`.

L’exemple suivant génère l’erreur C2682 :

```
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

L’exemple suivant génère l’erreur C2682 :

```
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