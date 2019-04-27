---
title: Erreur du compilateur C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 3e2d583efa2b634cf49d8588fa398bd81f24c607
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208757"
---
# <a name="compiler-error-c2452"></a>Erreur du compilateur C2452

'type' : type de source non valide pour safe_cast

Le type de source pour [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) n’était pas valide.  Par exemple, tous les types dans un `safe_cast` opération doivent être des types CLR.

L’exemple suivant génère l’erreur C2452 :

```
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