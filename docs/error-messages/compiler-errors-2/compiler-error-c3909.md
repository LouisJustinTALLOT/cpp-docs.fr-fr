---
title: Erreur du compilateur C3909 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb3526f537a2eceb006f6af9e9b0faba44bf9cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058703"
---
# <a name="compiler-error-c3909"></a>Erreur du compilateur C3909

aWinRT ou déclaration d’événement managé doit se produire dans un type managé ou WinRT

Un événement Windows Runtime ou managé a été déclaré dans un type natif. Pour corriger cette erreur, déclarez les événements dans des types Windows Runtime ou managés.

Pour plus d’informations, consultez [événement](../../windows/event-cpp-component-extensions.md).

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