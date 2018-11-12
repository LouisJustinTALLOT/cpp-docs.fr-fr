---
title: while, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: d774971910fe69ed707bc545e4c0e022282a1d17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662343"
---
# <a name="while-statement-c"></a>while, instruction (C)

L'instruction `while` vous permet de répéter une instruction jusqu'à ce qu'une expression spécifiée devienne false.

## <a name="syntax"></a>Syntaxe

*itération-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (**  *expression*  **)**  *statement*

L'élément *expression* doit être de type arithmétique ou pointeur. L'exécution se déroule comme suit :

1. L'élément *expression* est évalué.

1. Si l'élément *expression* est initialement false, le corps de l'instruction `while` n'est jamais exécuté et le contrôle passe de l'instruction `while` à l'instruction suivante dans le programme.

   Si l'élément *expression* est true (différent de zéro), le corps de l'instruction est exécuté et le processus est répété à partir de l'étape 1.

L'instruction `while` peut également se terminer lorsqu'une instruction **break**, `goto` ou `return` est exécutée dans le corps de l'instruction. Utilisez l'instruction **continue** pour terminer une itération sans quitter la boucle de `while`. L'instruction **continue** passe le contrôle à l'itération suivante de l'instruction `while`.

Voici un exemple d'instruction `while` :

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

Cet exemple copie des caractères de `string2` à `string1`. Si `i` est supérieur ou égal à 0, `string2[i]` est assigné à `string1[i]` et `i` est décrémenté. Lorsque `i` atteint 0 ou une valeur inférieure, l'exécution de l'instruction `while` se termine.

## <a name="see-also"></a>Voir aussi

[while, instruction (C++)](../cpp/while-statement-cpp.md)
