---
title: Erreur du compilateur C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 1071623c8dbaef52a6a391d8858e7502de9c74b4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757993"
---
# <a name="compiler-error-c3703"></a>Erreur du compilateur C3703

'gestionnaire d’événements' : une méthode de gestionnaire d’événements doit avoir la même classe de stockage que le’Event’source

Un [événement](../../cpp/event-handling.md) a une classe de stockage différente de celle du gestionnaire d’événements auquel il est raccordé. Par exemple, cette erreur se produit si le gestionnaire d’événements est une fonction membre statique et que l’événement n’est pas statique. Pour corriger cette erreur, attribuez à l’événement et au gestionnaire d’événements la même classe de stockage.

L’exemple suivant génère l’C3703 :

```cpp
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
