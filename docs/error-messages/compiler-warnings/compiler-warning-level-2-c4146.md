---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4146'
title: Avertissement du compilateur (niveau 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: 85aebd34ed83ef14e306f7512689ccdfba713eec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326502"
---
# <a name="compiler-warning-level-2-c4146"></a>Avertissement du compilateur (niveau 2) C4146

opérateur moins unaire appliqué à un type non signé, résultat toujours non signé

Les types non signés ne peuvent contenir que des valeurs non négatives, de sorte que le moins unaire (négation) n’a généralement pas de sens lorsqu’il est appliqué à un type non signé. L’opérande et le résultat ne sont pas négatifs.

Concrètement, cela se produit lorsque le programmeur tente d’exprimer la valeur entière minimale, soit-2147483648. Cette valeur ne peut pas être écrite en tant que-2147483648, car l’expression est traitée en deux étapes :

1. Le nombre 2147483648 est évalué. Étant donné qu’il est supérieur à la valeur entière maximale de 2147483647, le type de 2147483648 n’est pas [int](../../c-language/integer-types.md), mais **`unsigned int`** .

1. Le moins unaire est appliqué à la valeur, avec un résultat non signé, qui se présente également comme 2147483648.

Le type non signé du résultat peut provoquer un comportement inattendu. Si le résultat est utilisé dans une comparaison, une comparaison non signée peut être utilisée, par exemple, lorsque l’autre opérande est un **`int`** . Cela explique pourquoi l’exemple de programme ci-dessous n’affiche qu’une seule ligne.

La deuxième ligne attendue, `1 is greater than the most negative int` , n’est pas imprimée car `((unsigned int)1) > 2147483648` a la valeur false.

Vous pouvez éviter les C4146 à l’aide de INT_MIN à partir de Limits. h, qui a le type **`signed int`** .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4146 :

```cpp
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```
