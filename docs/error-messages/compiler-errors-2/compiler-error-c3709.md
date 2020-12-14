---
description: 'En savoir plus sur : erreur du compilateur C3709'
title: Erreur du compilateur C3709
ms.date: 11/04/2016
f1_keywords:
- C3709
helpviewer_keywords:
- C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
ms.openlocfilehash: 0c884801cc3c720df1018bf7c6d13b13465982a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241792"
---
# <a name="compiler-error-c3709"></a>Erreur du compilateur C3709

'fonction' : syntaxe incorrecte pour spécifier un événement dans __hook/ \_ _unhook

Quand vous spécifiez une source d’événements avec [__hook](../../cpp/hook.md) ou [__unhook](../../cpp/unhook.md), le premier paramètre doit être une méthode d’événement valide et le deuxième paramètre doit être un objet source d’événement valide (et non une méthode).

L’exemple suivant génère l’C3709 :

```cpp
// C3709.cpp
// compile with: /LD
[event_source(native)]
class CEventSrc
{
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec
{
public:
   void handler1()
   {
   }

   void HookEvents(CEventSrc* pSrc)
   {
      __hook(bad, pSrc, CEventRec::handler1);   // C3709
      // Try the following line instead:
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc)
   {
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};
```
