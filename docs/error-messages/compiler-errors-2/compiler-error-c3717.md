---
title: Erreur du compilateur C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: cd9a97f1b0d9c9eecfa6a42f735f21a42fd846e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753235"
---
# <a name="compiler-error-c3717"></a>Erreur du compilateur C3717

'méthode' : une méthode qui déclenche des événements ne peut pas être définie

Vous avez déclaré une méthode d’événement qui comprend une implémentation. Une déclaration de méthode [__event](../../cpp/event.md) ne peut pas avoir de définition. Pour corriger cette erreur, assurez-vous qu’aucune déclaration de méthode d’événement n’a de définitions. Par exemple, dans le code ci-dessous, supprimez le corps de la fonction de la déclaration `event1`, comme indiqué par les commentaires.

L’exemple suivant génère l’C3717 :

```cpp
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
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
