---
description: 'En savoir plus sur : erreur du compilateur C3724'
title: Erreur du compilateur C3724
ms.date: 11/04/2016
f1_keywords:
- C3724
helpviewer_keywords:
- C3724
ms.assetid: cab8aba7-14fc-406f-8cc6-32744c8f31c1
ms.openlocfilehash: 509467b964f8b4db35d3823ff9f89be0223061f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326586"
---
# <a name="compiler-error-c3724"></a>Erreur du compilateur C3724

doit #include \<windows.h> pour utiliser le Multi-Threading avec les événements

Le fichier Windows. h est requis si vous utilisez le multithreading avec des événements. Pour corriger cette erreur, ajoutez `#include <windows.h>` au début du fichier dans lequel les sources d’événements et les récepteurs d’événements sont définis.

```cpp
// C3724.cpp
// uncomment the following line to resolve
// #include <windows.h>

[event_source(native), threading(apartment)]
class CEventSrc {
public:
   __event void event1();   // C3724
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```
