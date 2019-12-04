---
title: Erreur du compilateur C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753326"
---
# <a name="compiler-error-c3714"></a>Erreur du compilateur C3714

'méthode' : une méthode de gestionnaire d’événements doit avoir la même convention d’appel que la’méthode’source

Vous avez défini une méthode de gestionnaire d’événements qui n’utilise pas la même convention d’appel que la méthode d’événement source. Pour corriger cette erreur, attribuez à la méthode de gestionnaire d’événements les mêmes conventions d’appel que celles de la méthode d’événement source. Par exemple, dans le code ci-dessous, définissez les conventions d’appel de `handler1` et `event1` match ([__cdecl](../../cpp/cdecl.md) ou [__stdcall](../../cpp/stdcall.md) , etc.). La suppression des mots clés de convention d’appel des deux déclarations résoudra également le problème et entraînera la valeur par défaut `event1` et `handler1` à la Convention d’appel [thiscall](../../cpp/thiscall.md) . Pour plus d’informations, consultez [conventions d’appel](../../cpp/calling-conventions.md) .

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
