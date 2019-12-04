---
title: Erreur du compilateur C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: c0e2082dc87c6236aa11dd3094d056b0024dfc2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752468"
---
# <a name="compiler-error-c3743"></a>Erreur du compilateur C3743

peut uniquement raccorder/décrocher une interface entière quand le paramètre « layout_dependent » de event_receiver a la valeur true

La fonction [__unhook](../../cpp/unhook.md) varie selon le nombre de paramètres qu’elle prend en fonction de la valeur transmise au paramètre `layout_dependent` dans la classe [event_receiver](../../windows/event-receiver.md) .

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
