---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4738'
title: Avertissement du compilateur (niveau 1) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: d57b992438148b3925b5366747db0b9de53ec87e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332143"
---
# <a name="compiler-warning-level-3-c4738"></a>Avertissement du compilateur (niveau 1) C4738

stockage de résultat flottant 32 bits en mémoire, perte possible de performances

C4738 vous avertit que le résultat d’une assignation, d’un cast, d’un argument passé ou d’une autre opération doit peut-être être arrondi ou que l’opération ne s’est pas déroulée et qu’elle est nécessaire à l’utilisation de la mémoire (débordement). Cela peut entraîner une perte de performances.

Pour résoudre cet avertissement et éviter l’arrondi, compilez avec [/FP : Fast](../../build/reference/fp-specify-floating-point-behavior.md) ou utilisez à la **`double`** place de **`float`** .

Pour résoudre cet avertissement et éviter de manquer de registres, modifiez l’ordre de calcul et modifiez votre utilisation de l’incorporation

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4738 :

```cpp
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
