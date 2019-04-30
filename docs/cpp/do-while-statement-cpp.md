---
title: do-while, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: d930c1884975288ff11f4d4e5cf2728e717e17d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392256"
---
# <a name="do-while-statement-c"></a>do-while, instruction (C++)

Exécute un *instruction* à plusieurs reprises jusqu'à ce que la condition d’arrêt spécifié (la *expression*) correspond à zéro.

## <a name="syntax"></a>Syntaxe

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Notes

Le test de la condition d’arrêt est effectué après chaque exécution de la boucle ; Par conséquent, un **faire-tandis que** boucle exécute une ou plusieurs fois, selon la valeur de l’expression d’arrêt. L'instruction **do-while** peut également se terminer lorsqu'une instruction [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) ou [return](../cpp/return-statement-cpp.md) est exécutée dans le corps de l'instruction.

L'élément *expression* doit être de type arithmétique ou pointeur. L'exécution se déroule comme suit :

1. Le corps de l'instruction est exécuté.

1. Ensuite, l'élément *expression* est évalué. Si l'élément *expression* est false, l'instruction **do-while** se termine et le contrôle passe à l'instruction suivante du programme. Si l'élément *expression* est true (différent de zéro), le processus se répète, en commençant à l'étape 1.

## <a name="example"></a>Exemple

L’exemple suivant montre comment la **faire-tandis que** instruction :

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Voir aussi

[Instructions d’itération](../cpp/iteration-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[while, instruction (C++)](../cpp/while-statement-cpp.md)<br/>
[for, instruction (C++)](../cpp/for-statement-cpp.md)<br/>
[Basé sur une plage, instruction (C++)](../cpp/range-based-for-statement-cpp.md)