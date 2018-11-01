---
title: Avertissement du compilateur (niveau 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 31711d3709b7c2ae3658d760f538ea9e841d33a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655726"
---
# <a name="compiler-warning-level-4-c4214"></a>Avertissement du compilateur (niveau 4) C4214

extension non standard utilisée : types de champs autres qu’int de bits

Avec les extensions Microsoft (/Ze), les membres de structure de champ de bits peuvent être de n’importe quel type entier.

## <a name="example"></a>Exemple

```
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

Ces champs de bits ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).