---
title: Erreur du compilateur C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 95de97a27fc42e98247675b1b48325593ff3c21e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779373"
---
# <a name="compiler-error-c3909"></a>Erreur du compilateur C3909

aWinRT ou déclaration d’événement managé doit se produire dans un type managé ou WinRT

Un événement Windows Runtime ou managé a été déclaré dans un type natif. Pour corriger cette erreur, déclarez les événements dans des types Windows Runtime ou managés.

Pour plus d’informations, consultez [événement](../../extensions/event-cpp-component-extensions.md).

L'exemple suivant génère l'erreur C3909 et montre comment la corriger :

```
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