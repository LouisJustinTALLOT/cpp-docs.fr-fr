---
title: Erreur du compilateur C2159
ms.date: 11/04/2016
f1_keywords:
- C2159
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
ms.openlocfilehash: 8c0ef75f63f5aa57e02297ebd94d4224048b0f2d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755856"
---
# <a name="compiler-error-c2159"></a>Erreur du compilateur C2159

plus d'une classe de stockage spécifiée

Une déclaration contient plusieurs classes de stockage.

L’exemple suivant génère l’erreur C2159 :

```cpp
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```
