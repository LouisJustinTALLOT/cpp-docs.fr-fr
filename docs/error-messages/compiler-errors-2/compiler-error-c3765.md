---
title: Erreur du compilateur C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 5bb2dba57c680882bb4bf8e4026f5720276b47b4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509381"
---
# <a name="compiler-error-c3765"></a>Erreur du compilateur C3765

'Event' : impossible de définir un événement dans un class/struct’type’marqué comme event_receiver

Si une classe est marquée avec l’attribut [event_receiver](../../windows/attributes/event-receiver.md) , la classe ne peut pas contenir de Déclaration [__event](../../cpp/event.md) .

L’exemple suivant génère l’C3765 :

```cpp
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```
