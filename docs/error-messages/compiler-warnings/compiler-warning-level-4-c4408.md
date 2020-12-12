---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4408'
title: Avertissement du compilateur (niveau 4) C4408
ms.date: 11/04/2016
f1_keywords:
- C4408
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
ms.openlocfilehash: 94764cd23c8bf4af757afa7bd8a084f61c5f24a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251477"
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
