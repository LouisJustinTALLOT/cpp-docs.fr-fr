---
title: Erreur du compilateur C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 86c043889c5342ed4f3edfc4d8a298bcbd345b3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400238"
---
# <a name="compiler-error-c3765"></a>Erreur du compilateur C3765

'event' : Impossible de définir un événement dans un class/struct 'type' marqué comme event_receiver

Si une classe est marquée avec le [event_receiver](../../windows/event-receiver.md) attribut, la classe ne peut pas contenir un [__event](../../cpp/event.md) déclaration.

L’exemple suivant génère l’erreur C3765 :

```
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```