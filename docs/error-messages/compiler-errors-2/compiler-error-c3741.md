---
description: 'En savoir plus sur : erreur du compilateur C3741'
title: Erreur du compilateur C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: 158555995449416da23120cafe16262cbb1a6208
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340253"
---
# <a name="compiler-error-c3741"></a>Erreur du compilateur C3741

'class' : doit être une coclasse quand le paramètre’layout_dependent’de event_receiver = true

Quand `layout_dependent=true` pour une classe [event_receiver](../../windows/attributes/event-receiver.md) , la classe doit également avoir l’attribut [coclass](../../windows/attributes/coclass.md) .

L’exemple suivant génère l’C3741

```cpp
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
