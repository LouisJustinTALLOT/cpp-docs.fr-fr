---
description: 'En savoir plus sur : erreur du compilateur C3719'
title: Erreur du compilateur C3719
ms.date: 11/04/2016
f1_keywords:
- C3719
helpviewer_keywords:
- C3719
ms.assetid: d0d59d4e-babb-4480-9ef7-70cf1a28165c
ms.openlocfilehash: a05e6cf7ee1aa67f3e8aa3e1fab737b9f5bc2969
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239075"
---
# <a name="compiler-error-c3719"></a>Erreur du compilateur C3719

'interface' : une source d’événements basée sur une interface ne peut être utilisée que pour les événements COM

Vous avez déclaré une interface dans un contexte non-COM.

L’exemple suivant génère l’C3719 :

```cpp
// C3719a.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];

[object]
__interface I {
   HRESULT func1();
};

[event_source(native), coclass]
struct A {
   __event __interface I;   // C3719

   // try the following line instead
   // __event func2();
};

int main() {
}
```

Pour corriger cette erreur, appliquez les attributs [Object](../../windows/attributes/object-cpp.md), [coclass](../../windows/attributes/coclass.md), [event_source](../../windows/attributes/event-source.md)et [event_receiver](../../windows/attributes/event-receiver.md) de manière appropriée afin de rendre les classes dans lesquelles vous utilisez les classes com de l’interface. Par exemple :

```cpp
// C3719b.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="xx")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f();
};

[coclass, event_source(com) , uuid("00000000-0000-0000-0000-000000000002")]
struct MyStruct {
   __event __interface I;
};

[event_receiver(com)]
struct MyStruct2 {
   void f() {
   }
   MyStruct2(I* pB) {
      __hook(&I::f, pB, &MyStruct2::f);
   }
};

int main()
{
}
```
