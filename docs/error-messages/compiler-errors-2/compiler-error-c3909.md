---
title: Erreur du compilateur C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 69613a1058bd5178ea4c03931664dd00bad7a101
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748994"
---
# <a name="compiler-error-c3909"></a>Erreur du compilateur C3909

une déclaration d’événement aWinRT ou managé doit se produire dans un type WinRT ou managé

Un événement Windows Runtime ou managé a été déclaré dans un type natif. Pour corriger cette erreur, déclarez les événements dans des types Windows Runtime ou managés.

Pour plus d’informations, consultez [Event](../../extensions/event-cpp-component-extensions.md).

L'exemple suivant génère l'erreur C3909 et montre comment la corriger :

```cpp
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
