---
title: Avertissement du compilateur (niveau 4) C4408
ms.date: 11/04/2016
f1_keywords:
- C4408
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
ms.openlocfilehash: 90ca85384b28f1cf2cdef5e4083813686b96c524
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682967"
---
# <a name="compiler-warning-level-4-c4408"></a>Avertissement du compilateur (niveau 4) C4408

anonymousstruct ou Union n’a déclaré aucune donnée membre

Un struct ou une union anonyme doit avoir au moins un membre de données.

L'exemple suivant génère l'avertissement C4408 :

```cpp
// C4408.cpp
// compile with: /W4 /LD
static union
{
   // int i;
};
// a named union can have no data members
// } MyUnion;
```