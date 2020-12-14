---
description: 'En savoir plus sur : erreur du compilateur C3712'
title: Erreur du compilateur C3712
ms.date: 11/04/2016
f1_keywords:
- C3712
helpviewer_keywords:
- C3712
ms.assetid: 65b1fcaf-be89-4c55-9e40-25ec03457253
ms.openlocfilehash: 530666d72ff72abef1286d594922dc877907b4e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241662"
---
# <a name="compiler-error-c3712"></a>Erreur du compilateur C3712

'méthode' : une méthode de gestionnaire d’événements doit retourner le même type que la’méthode’source

Vous avez défini une méthode de gestionnaire d’événements qui n’a pas retourné le même type que la méthode d’événement source. Pour corriger cette erreur, donnez à la méthode de gestionnaire d’événements le même type de retour que celui de la méthode d’événement source.

L’exemple suivant génère l’C3712 :

```cpp
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
