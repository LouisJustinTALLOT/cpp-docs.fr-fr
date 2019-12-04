---
title: Erreur du compilateur C2819
ms.date: 11/04/2016
f1_keywords:
- C2819
helpviewer_keywords:
- C2819
ms.assetid: fcc7762d-cb82-4bb1-a715-0d82da832edf
ms.openlocfilehash: 9a3768cb23c65eb3e2d818f81ff7c6a561c8d7ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750648"
---
# <a name="compiler-error-c2819"></a>Erreur du compilateur C2819

le type’type’n’a pas de membre surchargé’operator-> '

Vous devez définir `operator->()` pour utiliser cette opération de pointeur.

L’exemple suivant génère l’C2819 :

```cpp
// C2819.cpp
// compile with: /c
class A {
   public:
      int i;
};

class B {};

void C(B j) {
   j->i;   // C2819
}

class D {
   A* pA;

   public:
      A* operator->() {
         return pA;
      }
};

void F(D j) {
   j->i;
}
```

C2819 peut également se produire lors [ C++ de l’utilisation de la sémantique de pile pour les types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md). L’exemple suivant génère l’C2819 :

```cpp
// C2819_b.cpp
// compile with: /clr
ref struct R {
   void Test() {}
};

int main() {
   R r;
   r->Test();   // C2819
   r.Test();   // OK
}
```
