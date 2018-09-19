---
title: Erreur du compilateur C3765 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3765
dev_langs:
- C++
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cac3930e4f5ec42587a9f557adc7a82d750b3819
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042128"
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