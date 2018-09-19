---
title: continue, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88281d90ce15ced12079b3c66a74bb2f23c11034
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099704"
---
# <a name="continue-statement-c"></a>continue, instruction (C++)

Force le transfert de contrôle à l’expression de contrôle de la plus petite [faire](../cpp/do-while-statement-cpp.md), [pour](../cpp/for-statement-cpp.md), ou [tandis que](../cpp/while-statement-cpp.md) boucle.

## <a name="syntax"></a>Syntaxe

```
continue;
```

## <a name="remarks"></a>Notes

Toutes les instructions restantes dans l'itération actuelle ne sont pas exécutées. L'itération suivante de la boucle est déterminée comme suit :

- Dans un **faire** ou **tandis que** boucle, l’itération suivante démarre en réévaluant l’expression de contrôle de la **faire** ou **tandis que** instruction.

- Dans un **pour** boucle (à l’aide de la syntaxe `for`(`init-expr`; `cond-expr`; `loop-expr`)), le `loop-expr` clause est exécutée. Ensuite la clause `cond-expr` est réévaluée et, selon le résultat, la boucle se termine ou une autre itération a lieu.

L’exemple suivant montre comment la **continuer** instruction peut être utilisée pour ignorer les sections de code et commencer l’itération suivante d’une boucle.

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