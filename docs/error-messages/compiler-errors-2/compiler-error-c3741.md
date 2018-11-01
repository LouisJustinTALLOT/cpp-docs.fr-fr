---
title: Erreur du compilateur C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: d207c87c7b3f75ac939c155da127720562973160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569258"
---
# <a name="compiler-error-c3741"></a>Erreur du compilateur C3741

'classe' : doit être une coclasse quand le paramètre 'layout_dependent' d’event_receiver = true

Lorsque `layout_dependent=true` pour un [event_receiver](../../windows/event-receiver.md) classe, la classe doit également disposer du [coclasse](../../windows/coclass.md) attribut.

L’exemple suivant génère l’erreur C3741.

```
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```