---
title: Compilateur avertissement (niveau 1) C4163 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4163
dev_langs:
- C++
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 677264a557b8d95adc99f7fa804ebaa26e53fd6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118217"
---
# <a name="compiler-warning-level-1-c4163"></a>Avertissement du compilateur (niveau 1) C4163

'identificateur' : non disponible comme fonction intrinsèque

La fonction spécifiée ne peut pas être utilisée comme fonction [intrinsèque](../../preprocessor/intrinsic.md) . Le compilateur ignore le nom de fonction non valide.

L’exemple suivant génère l’avertissement C4163 :

```
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```