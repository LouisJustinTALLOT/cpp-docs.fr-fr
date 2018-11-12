---
title: Erreur du compilateur C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 9bfdf8b26ab599ef1a28483af7ebc28f0dbc1912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441871"
---
# <a name="compiler-error-c3714"></a>Erreur du compilateur C3714

'méthode' : une méthode de gestionnaire d’événements doit avoir la même convention d’appel comme source de 'method'

Vous avez défini une méthode de gestionnaire d’événements qui n’utilise pas la même convention d’appel en tant que la méthode d’événement source. Pour corriger cette erreur, donnez à la méthode de gestionnaire d’événements les mêmes conventions d’appel que ceux de la méthode d’événement source. Par exemple, dans le code ci-dessous, vérifiez les conventions d’appel de `handler1` et `event1` correspond à ([__cdecl](../../cpp/cdecl.md) ou [__stdcall](../../cpp/stdcall.md) ou d’autres). Suppression de l’appel de mots clés de convention les deux déclarations de sera aussi résoudre le problème et entraîner `event1` et `handler1` pour utiliser par défaut le [thiscall](../../cpp/thiscall.md) convention d’appel. Consultez [Conventions d’appel](../../cpp/calling-conventions.md) pour plus d’informations.

L’exemple suivant génère l’erreur C3714 :

```
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```