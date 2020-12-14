---
description: 'En savoir plus sur : erreur du compilateur C3711'
title: Erreur du compilateur C3711
ms.date: 11/04/2016
f1_keywords:
- C3711
helpviewer_keywords:
- C3711
ms.assetid: 26d581cc-2153-4ee0-b814-a371184be3e1
ms.openlocfilehash: 5ced0d5e83c149f3634053680aa52821e0d9bbe8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241688"
---
# <a name="compiler-error-c3711"></a>Erreur du compilateur C3711

'méthode' : une méthode source d’événement non managée doit retourner void ou un type intégral

Vous avez défini une méthode dans la source de l’événement qui n’a pas retourné void ou un type intégral. Pour corriger cette erreur, attribuez à l’événement et au gestionnaire d’événements un type de retour **`void`** ou un type intégral tel que **`int`** ou **`long`** .

L’exemple suivant génère l’C3711 :

```cpp
// C3711.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[event_source(native)]
class CEventSrc {
public:
   __event float event1();   // C3711
   // try the following line instead
   // __event int event1();
   // also change the handler, below
};

[event_receiver(native)]
class CEventRec {
public:
   float handler1() {         // change float to int
      return 0.0;             // change 0.0 to 0
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
