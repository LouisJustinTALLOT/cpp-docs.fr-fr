---
title: Avertissement du compilateur (niveau 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 8a3697b3bf63ac2a7a1e4e4bd0bf3a626c6bd631
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566125"
---
# <a name="compiler-warning-level-4-c4213"></a>Avertissement du compilateur (niveau 4) C4213

extension non standard utilisée : cast sur l-value

Avec les extensions Microsoft (/Ze), vous pouvez utiliser des casts sur le côté gauche d’une instruction d’assignation.

## <a name="example"></a>Exemple

```
// C4213.c
// compile with: /W4
void *a;
void f()
{
   int   i[3];
   a = &i;
   *(( int * )a )++ = 3;  // C4213
}

int main()
{
}
```

De telles conversions ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).