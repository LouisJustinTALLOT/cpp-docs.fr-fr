---
description: 'En savoir plus sur : erreur du compilateur C3911'
title: Erreur du compilateur C3911
ms.date: 11/04/2016
f1_keywords:
- C3911
helpviewer_keywords:
- C3911
ms.assetid: b786da59-0e99-479d-bc0d-551126e940f2
ms.openlocfilehash: f66265934788110e5ff4db45f9345a97ff59dcbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144116"
---
# <a name="compiler-error-c3911"></a>Erreur du compilateur C3911

'event_accessor_method' : la fonction doit avoir le type’signature'

La méthode d’accesseur d’un événement n’a pas été correctement déclarée.

Pour plus d’informations, consultez [Event](../../extensions/event-cpp-component-extensions.md).

L’exemple suivant génère l’C3911 :

```cpp
// C3911.cpp
// compile with: /clr
using namespace System;
delegate void H(String^, int);

ref class X {
   event H^ E1 {
      void add() {}   // C3911
      // try the following line instead
      // void add(H ^ h) {}

      void remove(){}
      // try the following line instead
      // void remove(H ^ h) {}

      void raise(){}
      // try the following line instead
      // void raise(String ^ s, int i) {}
   };
};
```
