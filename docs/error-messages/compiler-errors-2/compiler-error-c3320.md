---
title: Erreur du compilateur C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581465"
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