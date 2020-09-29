---
title: Erreur du compilateur C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: b4bb198ae883e53e7947ce7f123bb0d3f092aaf3
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500401"
---
# <a name="compiler-error-c3743"></a>Erreur du compilateur C3743

peut uniquement raccorder/décrocher une interface entière quand le paramètre « layout_dependent » de event_receiver a la valeur true

La fonction [__unhook](../../cpp/unhook.md) varie selon le nombre de paramètres qu’elle prend en fonction de la valeur transmise au `layout_dependent` paramètre dans la classe [event_receiver](../../windows/attributes/event-receiver.md) .

L’exemple suivant génère l’C3743 :

```cpp
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```
