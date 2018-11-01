---
title: Avertissement du compilateur (niveau 4) C4408
ms.date: 11/04/2016
f1_keywords:
- C4408
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
ms.openlocfilehash: 3c7613d42bbd0ac7fa58a0b95ba68efb60d9f50a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553866"
---
# <a name="compiler-warning-level-4-c4408"></a>Avertissement du compilateur (niveau 4) C4408

anonymousstruct ou une union n’a déclaré aucune donnée membre

Un struct ou une union anonyme doit avoir au moins un membre de données.

L'exemple suivant génère l'avertissement C4408 :

```
// C4408.cpp
// compile with: /W4 /LD
static union
{
   // int i;
};
// a named union can have no data members
// } MyUnion;
```