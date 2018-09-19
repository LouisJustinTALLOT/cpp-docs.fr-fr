---
title: Compilateur avertissement (niveau 3) C4738 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e017ef94dd28de8d4c66ab89b1509f755beeb07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053218"
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