---
title: Erreur du compilateur C3320 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b67d419630d59902270638213ce7a79dd8b9e0c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078437"
---
# <a name="compiler-error-c3320"></a>Erreur du compilateur C3320

'type' : le type ne peut pas avoir le même nom que la propriété 'name' du module

Un défini par l’utilisateur type exporté (UDT), qui peut être struct, class, enum ou union, ne peut pas avoir le même nom que le paramètre passé à la [module](../../windows/module-cpp.md) propriété de nom de l’attribut.

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