---
title: Erreur du compilateur C2702
description: Décrit l’erreur C2702 du compilateur Microsoft C/C++.
ms.date: 08/25/2020
f1_keywords:
- C2702
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
ms.openlocfilehash: 83210f6ab261a5ae6dd7320182c3f4c3539ff4d1
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898423"
---
# <a name="compiler-error-c2702"></a>Erreur du compilateur C2702

> `__except` peut ne pas apparaître dans le bloc de fin

Un gestionnaire d’exceptions ( **`__try`** / **`__except`** ) ne peut pas être imbriqué à l’intérieur d’un **`__finally`** bloc.

L’exemple suivant génère l’C2702 :

```cpp
// C2702.cpp
// processor: x86 IPF
int Counter;
int main() {
   __try {}
   __finally {
      __try {}   // C2702
      __except( Counter ) {}   // C2702
   }
}
```
