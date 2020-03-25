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
ms.openlocfilehash: f52c065210a8861dc065508248a506770b039b1d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189271"
---
# <a name="do-while-statement-c"></a>do-while, instruction (C++)

Exécute une *instruction* à plusieurs reprises jusqu’à ce que la condition d’arrêt spécifiée (l' *expression*) soit égale à zéro.

## <a name="syntax"></a>Syntaxe

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Notes

Le test de la condition d’arrêt est effectué après chaque exécution de la boucle. par conséquent, une boucle **do-while** s’exécute une ou plusieurs fois, selon la valeur de l’expression d’arrêt. L'instruction **do-while** peut également se terminer lorsqu'une instruction [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) ou [return](../cpp/return-statement-cpp.md) est exécutée dans le corps de l'instruction.

L'élément *expression* doit être de type arithmétique ou pointeur. L'exécution se déroule comme suit :

1. Le corps de l'instruction est exécuté.

1. Ensuite, l'élément *expression* est évalué. Si l'élément *expression* est false, l'instruction **do-while** se termine et le contrôle passe à l'instruction suivante du programme. Si l'élément *expression* est true (différent de zéro), le processus se répète, en commençant à l'étape 1.

## <a name="example"></a>Exemple

L’exemple suivant illustre l’instruction **do-while** :

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
