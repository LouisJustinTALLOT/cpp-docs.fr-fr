---
description: 'En savoir plus sur : erreur du compilateur C3732'
title: Erreur du compilateur C3732
ms.date: 11/04/2016
f1_keywords:
- C3732
helpviewer_keywords:
- C3732
ms.assetid: 2d55a7e1-9c39-4379-a093-2f7beb27e2ca
ms.openlocfilehash: 406acf356ee0bec09eb5d9e218114256f9c58858
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245055"
---
# <a name="compiler-error-c3732"></a>Erreur du compilateur C3732

'interface' : une interface personnalisée qui déclenche des événements COM ne peut pas hériter de IDispatch

Une interface qui prend en charge les événements COM ne peut pas hériter de `IDispatch` . Pour plus d’informations, consultez [gestion des événements dans com](../../cpp/event-handling-in-com.md).

L’erreur suivante génère C3732 :

```cpp
// C3732.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="test")];

// to resolve this C3732, use dual instead of object
// or inherit from IUnknown
[ object ]
__interface I : IDispatch
{
};

[ event_source(com), coclass ]
struct A
{
   __event __interface I;   // C3732
};

int main()
{
}
```
