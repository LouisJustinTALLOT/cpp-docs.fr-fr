---
description: 'En savoir plus sur : erreur du compilateur C2452'
title: Erreur du compilateur C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 8d3915e9b249b53ca1cd193247ca1cf742fa7ffe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332399"
---
# <a name="compiler-error-c2452"></a>Erreur du compilateur C2452

'type' : type de source non valide pour safe_cast

Le type de source de [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) n’est pas valide.  Par exemple, tous les types dans une `safe_cast` opération doivent être des types CLR.

L’exemple suivant génère l’C2452 :

```cpp
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```
