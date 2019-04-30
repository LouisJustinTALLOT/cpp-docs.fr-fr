---
title: Avertissement du compilateur (niveau 1) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: 833546d20454e6104a2d5fcb272bf5bb9518ea44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401577"
---
# <a name="compiler-warning-level-3-c4738"></a>Avertissement du compilateur (niveau 1) C4738

stockage de résultat flottant 32 bits en mémoire, perte possible de performances

C4738 signale que le résultat d’une assignation, effectuer un cast, transmis argument, ou autre opération peut devoir être arrondi ou que l’opération a manqué de registres et nécessaires à l’utilisation de mémoire (débordement). Cela peut entraîner une perte de performances.

Pour résoudre cet avertissement et éviter d’arrondi, compilez avec [Fast](../../build/reference/fp-specify-floating-point-behavior.md) ou utilisez `double` au lieu de `float`.

Pour résoudre cet avertissement et éviter de manquer de registres, modifier l’ordre de calcul et votre utilisation d’incorporation (inlining)

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4738 :

```
// C4738.cpp
// compile with: /c /fp:precise /O2 /W3
// processor: x86
#include <stdio.h>

#pragma warning(default : 4738)

float func(float f)
{
    return f;
}

int main()
{
    extern float f, f1, f2;
    double d = 0.0;

    f1 = func(d);
    f2 = (float) d;
    f = f1 + f2;   // C4738
    printf_s("%f\n", f);
}
```