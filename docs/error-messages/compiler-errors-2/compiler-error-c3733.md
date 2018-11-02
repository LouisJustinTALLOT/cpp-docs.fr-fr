---
title: Erreur du compilateur C3733
ms.date: 11/04/2016
f1_keywords:
- C3733
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
ms.openlocfilehash: 006f87691c6e0839115e2c02ab0d922aa95eaa93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501645"
---
# <a name="compiler-error-c3733"></a>Erreur du compilateur C3733

'event' : syntaxe incorrecte pour spécifier un événement COM ; n’auriez-vous pas oublié '__interface' ?

Syntaxe incorrecte a été utilisée pour un événement COM. Pour corriger cette erreur, modifiez le type d’événement ou corrigez la syntaxe pour respecter les règles d’événement COM.

L’exemple suivant génère l’erreur C3733 :

```
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[coclass, event_source(com), // change 'com' to 'native' to resolve
uuid("00000000-0000-0000-0000-000000000001")]
class A
{
   __event void func();   // C3733
};

int main()
{
}
```