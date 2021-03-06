---
description: 'En savoir plus sur : erreur du compilateur C2387'
title: Erreur du compilateur C2387
ms.date: 11/04/2016
f1_keywords:
- C2387
helpviewer_keywords:
- C2387
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
ms.openlocfilehash: 70c876c999ec7d40b93ac94ffe111d105981ceeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124005"
---
# <a name="compiler-error-c2387"></a>Erreur du compilateur C2387

'type' : classe de base ambiguë

Le compilateur n’a pas pu résoudre de manière non ambiguë un appel de fonction, car la fonction existe dans plusieurs classes de base.

Pour résoudre cette erreur, supprimez l’une des classes de base de l’héritage ou qualifiez explicitement l’appel de fonction.

L’exemple suivant génère l’C2387 :

```cpp
// C2387.cpp
namespace N1 {
   struct B {
      virtual void f() {
      }
   };
}

namespace N2 {
   struct B {
      virtual void f() {
      }
   };
}

struct D : N1::B, N2::B {
   virtual void f() {
      B::f();   // C2387
      // try the following line instead
      // N1::B::f();
   }
};

int main() {
   D aD;
   aD.f();
}
```
