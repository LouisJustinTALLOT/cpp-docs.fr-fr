---
title: Erreur du compilateur C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 0b34760bc3f5b23148ce84cf590685efad2008df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324634"
---
# <a name="compiler-error-c3703"></a>Erreur du compilateur C3703

'Gestionnaire d’événements' : une méthode de gestionnaire d’événements doit avoir la même classe de stockage en tant que la source 'event'

Un [événement](../../cpp/event-handling.md) a une classe de stockage autre que le Gestionnaire d’événements auquel il est lié. Par exemple, cette erreur se produit si le Gestionnaire d’événements est une fonction membre statique et l’événement n’est pas statique. Pour corriger cette erreur, donnez à l’événement et le Gestionnaire d’événements la même classe de stockage.

L’exemple suivant génère l’erreur C3703 :

```
// C3703.cpp
// C3703 expected
#include <stdio.h>

[event_source(type=native)]
class CEventSrc {
public:
   __event static void MyEvent();
};

[event_receiver(type=native)]
class CEventHandler {
public:
   // delete the following line to resolve
   void MyHandler() {}

   // try the following line instead
   // static void MyHandler() {}

   void HookIt(CEventSrc* pSource) {
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }

   void UnhookIt(CEventSrc* pSource) {
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }
};

int main() {
   CEventSrc src;
   CEventHandler hnd;

   hnd.HookIt(&src);
   __raise src.MyEvent();
   hnd.UnhookIt(&src);
}
```