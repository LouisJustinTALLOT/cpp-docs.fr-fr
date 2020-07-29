---
title: Avertissement du compilateur (niveau 1) C4750
description: Décrit l’avertissement du compilateur MSVC C4750 sur un éventuel dépassement de capacité de la pile.
ms.date: 07/08/2020
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: a02b69981d3cf1d35a6700261fc5142cfa8ec8e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225356"
---
# <a name="compiler-warning-level-1-c4750"></a>Avertissement du compilateur (niveau 1) C4750

> '*identifier*' : fonction avec _alloca () Inline dans une boucle

## <a name="remarks"></a>Notes

La fonction'*identifier*'force l’expansion inline de la [`_alloca`](../../c-runtime-library/reference/alloca.md) fonction dans une boucle, ce qui peut provoquer un dépassement de capacité de la pile lors de l’exécution de la boucle.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que la fonction'*identifier*'n’est pas modifiée avec le [`__forceinline`](../../cpp/inline-functions-cpp.md) spécificateur.

1. Assurez-vous que la fonction'*identifier*'ne contient pas une [`_alloca`](../../c-runtime-library/reference/alloca.md) fonction contenue dans une boucle.

1. Ne spécifiez pas le [`/O1`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) commutateur de compilation,, [`/O2`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) [`/Ox`](../../build/reference/ox-full-optimization.md) ou [`/Og`](../../build/reference/og-global-optimizations.md) .

1. Placez la [`_alloca`](../../c-runtime-library/reference/alloca.md) fonction dans une [instruction try-except](../../cpp/try-except-statement.md) qui intercepte un dépassement de capacité de la pile.

## <a name="example"></a>Exemple

L’exemple de code suivant appelle `MyFunction` dans une boucle, et `MyFunction` appelle la fonction `_alloca` . Le **`__forceinline`** modificateur provoque l’expansion inline de la `_alloca` fonction.

```cpp
// c4750.cpp
// compile with: /O2 /W1 /c
#include <intrin.h>

char * volatile newstr;

__forceinline void myFunction(void) // C4750 warning
{
// The _alloca function does not require a __try/__except
// block because the example uses compiler option /c.
    newstr = (char * volatile) _alloca(1000);
}

int main(void)
{
    for (int i=0; i<50000; i++)
       myFunction();
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[_alloca](../../c-runtime-library/reference/alloca.md)
