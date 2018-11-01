---
title: Erreur du compilateur C3712
ms.date: 11/04/2016
f1_keywords:
- C3712
helpviewer_keywords:
- C3712
ms.assetid: 65b1fcaf-be89-4c55-9e40-25ec03457253
ms.openlocfilehash: 0b84f4562dcc0dd5dcc3ecb647316772efab6b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492667"
---
# <a name="compiler-error-c3712"></a>Erreur du compilateur C3712

'méthode' : une méthode de gestionnaire d’événements doit retourner le même type que la source 'method'

Vous avez défini une méthode de gestionnaire d’événements qui n’a pas retourné le même type que la méthode d’événement source. Pour corriger cette erreur, donnez à la méthode de gestionnaire d’événements du même type de retour que celle de la méthode d’événement source.

L’exemple suivant génère l’erreur C3712 :

```
// C3712.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   int handler1() { return 0; }
   // try the following line instead
   // void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
};
```