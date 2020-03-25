---
title: Avertissement du compilateur (niveau 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 492fe4a75b4ddf9b5f78810226f14aa84ab2b56a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176128"
---
# <a name="compiler-warning-level-1-c4163"></a>Avertissement du compilateur (niveau 1) C4163

'identificateur' : non disponible comme fonction intrinsèque

La fonction spécifiée ne peut pas être utilisée comme fonction [intrinsèque](../../preprocessor/intrinsic.md) . Le compilateur ignore le nom de fonction non valide.

L’exemple suivant génère l’avertissement C4163 :

```cpp
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```
