---
title: Erreur du compilateur C2682 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2682
dev_langs:
- C++
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72dc19170729d7203b57e305ef2c8a0d2b2d6de1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049200"
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