---
title: Erreur du compilateur C2819 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2819
dev_langs:
- C++
helpviewer_keywords:
- C2819
ms.assetid: fcc7762d-cb82-4bb1-a715-0d82da832edf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e535b47828a70a7a2e52606bc5c9de6ceb62ee48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095429"
---
# <a name="compiler-error-c2819"></a>Erreur du compilateur C2819

le type 'type' n’a pas un membre surchargé 'opérateur de' ->

Vous devez définir `operator->()` à utiliser cette opération de pointeur.

L’exemple suivant génère l’erreur C2819 :

```
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

C2819 peut également se produire lorsque vous utilisez [sémantique de pile C++ pour les Types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md). L’exemple suivant génère l’erreur C2819 :

```
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