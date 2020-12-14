---
description: 'En savoir plus sur : erreur du compilateur C3713'
title: Erreur du compilateur C3713
ms.date: 11/04/2016
f1_keywords:
- C3713
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
ms.openlocfilehash: 83a3e22e6b58d13b419bcd5c586fe18a888f6779
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241675"
---
# <a name="compiler-error-c3713"></a>Erreur du compilateur C3713

'méthode' : une méthode de gestionnaire d’événements doit avoir les mêmes paramètres de fonction que la’méthode’source

Vous avez défini une méthode de gestionnaire d’événements qui n’utilisait pas les mêmes paramètres que la méthode d’événement source. Pour corriger cette erreur, attribuez à la méthode de gestionnaire d’événements les mêmes paramètres que ceux de la méthode d’événement source.

L’exemple suivant génère l’C3713 :

```cpp
// C3713.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1(int nValue);
   // try the following line instead
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713
   }
};
```
