---
title: Avertissement du compilateur (niveau 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 640ce66233fb8820ec434e70060a5ab3cf56c3c0
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627435"
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