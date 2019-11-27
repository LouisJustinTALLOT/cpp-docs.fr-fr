---
title: Avertissement du compilateur (niveau 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: ecbe8bddd3f868070470555e79608ac1ecce380a
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541669"
---
# <a name="compiler-warning-level-4-c4204"></a>Avertissement du compilateur (niveau 4) C4204

extension non standard utilisée : initialiseur d’agrégat non constant

Avec les extensions Microsoft (/Ze), vous pouvez initialiser des types d’agrégats (tableaux, structures, unions et classes) avec des valeurs qui ne sont pas des constantes.

## <a name="example"></a>Exemple

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).