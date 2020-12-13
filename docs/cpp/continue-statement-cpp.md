---
description: 'En savoir plus sur : instruction continue (C++)'
title: continue, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6899e5cd249ab5a7a3b786e4b82c9890c08a7183
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344638"
---
# <a name="continue-statement-c"></a>continue, instruction (C++)

Force le transfert de contrôle vers l’expression de contrôle de la plus petite boucle [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)ou [while](../cpp/while-statement-cpp.md) .

## <a name="syntax"></a>Syntaxe

```
continue;
```

## <a name="remarks"></a>Notes

Toutes les instructions restantes dans l'itération actuelle ne sont pas exécutées. L'itération suivante de la boucle est déterminée comme suit :

- Dans une **`do`** **`while`** boucle ou, l’itération suivante démarre en réévaluant l’expression de contrôle de l' **`do`** **`while`** instruction ou.

- Dans une **`for`** boucle (à l’aide de la syntaxe `for( <init-expr> ; <cond-expr> ; <loop-expr> )` ), la `<loop-expr>` clause est exécutée. Ensuite la clause `<cond-expr>` est réévaluée et, selon le résultat, la boucle se termine ou une autre itération a lieu.

L’exemple suivant montre comment l' **`continue`** instruction peut être utilisée pour ignorer des sections de code et commencer l’itération suivante d’une boucle.

## <a name="example"></a>Exemple

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>Voir aussi

[Instructions de saut](../cpp/jump-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
