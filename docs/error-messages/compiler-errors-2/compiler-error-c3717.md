---
description: 'En savoir plus sur : erreur du compilateur C3717'
title: Erreur du compilateur C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: fecd417af1eceb40ef8b8e48fda40b3ec5e5b36a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189429"
---
# <a name="compiler-error-c3717"></a>Erreur du compilateur C3717

'méthode' : une méthode qui déclenche des événements ne peut pas être définie

Vous avez déclaré une méthode d’événement qui comprend une implémentation. Une déclaration de méthode [__event](../../cpp/event.md) ne peut pas avoir de définition. Pour corriger cette erreur, assurez-vous qu’aucune déclaration de méthode d’événement n’a de définitions. Par exemple, dans le code ci-dessous, supprimez le corps de la fonction de la `event1` déclaration, comme indiqué par les commentaires.

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
