---
title: while, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 8095dd8672218239dbcfa879e3df929643e93d90
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231401"
---
# <a name="while-statement-c"></a>while, instruction (C)

L' **`while`** instruction vous permet de répéter une instruction jusqu’à ce qu’une expression spécifiée devienne false.

## <a name="syntax"></a>Syntaxe

*itération-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction* **while (***expression***)**      

L'élément *expression* doit être de type arithmétique ou pointeur. L'exécution se déroule comme suit :

1. L'élément *expression* est évalué.

1. Si *expression* est initialement false, le corps de l' **`while`** instruction n’est jamais exécuté et le contrôle passe de l' **`while`** instruction à l’instruction suivante dans le programme.

   Si l'élément *expression* est true (différent de zéro), le corps de l'instruction est exécuté et le processus est répété à partir de l'étape 1.

L' **`while`** instruction peut également se terminer lorsqu’un **`break`** , **`goto`** ou **`return`** dans le corps de l’instruction est exécuté. Utilisez l' **`continue`** instruction pour terminer une itération sans quitter la **`while`** boucle. L' **`continue`** instruction passe le contrôle à l’itération suivante de l' **`while`** instruction.

Voici un exemple de l' **`while`** instruction :

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

Cet exemple copie des caractères de `string2` à `string1`. Si `i` est supérieur ou égal à 0, `string2[i]` est assigné à `string1[i]` et `i` est décrémenté. Lorsque `i` atteint ou descend en dessous de 0, l’exécution de l' **`while`** instruction se termine.

## <a name="see-also"></a>Voir aussi

[while, instruction (C++)](../cpp/while-statement-cpp.md)
