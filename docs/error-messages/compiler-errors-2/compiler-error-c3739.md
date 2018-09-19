---
title: Erreur du compilateur C3739 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3739
dev_langs:
- C++
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0cc0bbe61f807ccd6b2f2f1404fb8e5cc724107
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069883"
---
# <a name="compiler-error-c3739"></a>Erreur du compilateur C3739

'class' : uniquement en charge la syntaxe lorsque le paramètre 'layout_dependent' d’event_receiver a la valeur true

Vous avez essayé de raccorder une interface d’événements complète mais `layout_dependent` sur [event_receiver](../../windows/event-receiver.md) attribut n’est pas vrai ; vous devez associer un seul événement à la fois.

L’exemple suivant génère l’erreur C3739 :

```
// C3739.cpp
struct A
{
   __event void e();
};

// event_receiver is implied
// [ event_receiver(layout_dependent=false)]

// use the following line instead
// [event_receiver(com, layout_dependent=true), coclass ]
struct B
{
   void f();
   B(A* a)
   {
      __hook(A, a, &B::f);   // C3739
      // use the following line instead to hook a single event
      // __hook(&A::e, a, &B::f);
   }
};

int main()
{
}
```