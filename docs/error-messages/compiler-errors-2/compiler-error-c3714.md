---
description: 'En savoir plus sur : erreur du compilateur C3714'
title: Erreur du compilateur C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: a01544558a156b746c16e731584e30bab7a77825
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241623"
---
# <a name="compiler-error-c3714"></a>Erreur du compilateur C3714

'méthode' : une méthode de gestionnaire d’événements doit avoir la même convention d’appel que la’méthode’source

Vous avez défini une méthode de gestionnaire d’événements qui n’utilise pas la même convention d’appel que la méthode d’événement source. Pour corriger cette erreur, attribuez à la méthode de gestionnaire d’événements les mêmes conventions d’appel que celles de la méthode d’événement source. Par exemple, dans le code ci-dessous, faites en sorte que les conventions d’appel de `handler1` et `event1` correspondent ([__cdecl](../../cpp/cdecl.md) ou [__stdcall](../../cpp/stdcall.md) ou d’autres). La suppression des mots clés de convention d’appel des deux déclarations permet également de résoudre le problème, et de générer `event1` et `handler1` d’utiliser par défaut la Convention d’appel [thiscall](../../cpp/thiscall.md) . Pour plus d’informations, consultez [conventions d’appel](../../cpp/calling-conventions.md) .

L’exemple suivant génère l’C3714 :

```cpp
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
