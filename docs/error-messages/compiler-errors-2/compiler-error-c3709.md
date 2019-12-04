---
title: Erreur du compilateur C3709
ms.date: 11/04/2016
f1_keywords:
- C3709
helpviewer_keywords:
- C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
ms.openlocfilehash: 47320c79dbbfc2152c126c80d1eb8c061f3ceb3a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757915"
---
# <a name="compiler-error-c3709"></a>Erreur du compilateur C3709

'fonction' : syntaxe incorrecte pour spécifier un événement dans __hook/\__unhook

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
