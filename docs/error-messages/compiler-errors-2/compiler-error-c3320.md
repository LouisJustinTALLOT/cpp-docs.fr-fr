---
title: Erreur du compilateur C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 98af3c84b48aa8e69ad883bf73299f2697618ce1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501334"
---
# <a name="compiler-error-c3320"></a>Erreur du compilateur C3320

'type' : le type ne peut pas avoir le même nom que la propriété 'name' du module

Un type défini par l’utilisateur (UDT) exporté, qui peut être un struct, une classe, une énumération ou une Union, ne peut pas avoir le même nom que le paramètre passé à la propriété Name de l’attribut de [module](../../windows/attributes/module-cpp.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3320 :

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```
