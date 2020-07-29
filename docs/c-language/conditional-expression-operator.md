---
title: Opérateur d'expression conditionnelle
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: 03f9673da109151bd2146daf7539841f1cac07c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217127"
---
# <a name="conditional-expression-operator"></a>Opérateur d'expression conditionnelle

C contient un opérateur ternaire : l'opérateur d'expression conditionnelle (**? :**).

## <a name="syntax"></a>Syntaxe

*expression conditionnelle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression OU logique*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Expression OU logique*  **?**  *expression*  **:**  *Conditional-expression*

L'élément *logical-OR-expression* doit être de type intégral, flottant ou pointeur. Il est évalué en termes d'équivalence à 0. Un point de séquence suit l'élément *logical-OR-expression*. L’évaluation des opérandes continue comme suit :

- Si l'élément *logical-OR-expression* n'est pas égal à 0, l'élément *expression* est évalué. Le résultat de l'évaluation de l'expression est fourni par l'élément non terminal *expression*. (Cela signifie que l'élément *expression* n'est évalué que si l'élément *logical-OR-expression* a la valeur true.)

- Si l'élément *logical-OR-expression* a la valeur 0, l'élément *conditional-expression* est évalué. Le résultat de l'expression est la valeur de l'élément *conditional-expression*. (Cela signifie que l'élément *conditional-expression* n'est évalué que si l'élément *logical-OR-expression* a la valeur false.)

Notez que soit l'élément *expression*, soit l'élément *conditional-expression* est évalué, mais pas les deux.

Le type du résultat d’une opération conditionnelle dépend du type de l’opérande *expression* ou *conditional-expression*, comme suit :

- Si *expression* ou *conditional-expression* a un type intégral ou flottant (leurs types peuvent être différents), l'opérateur exécute les conversions arithmétiques habituelles. Le type du résultat est le type des opérandes après conversion.

- Si *expression* et *conditional-expression* ont le même type de structure, d'union, ou de pointeur, le type du résultat est le même type de structure, d'union ou de pointeur.

- Si les deux opérandes ont **`void`** le type, le résultat a le type **`void`** .

- Si l’un des opérandes est un pointeur vers un objet de tout type, et que l’autre opérande est un pointeur vers **`void`** , le pointeur vers l’objet est converti en pointeur vers **`void`** et le résultat est un pointeur vers **`void`** .

- Si *expression* ou *conditional-expression* est un pointeur et que l’autre opérande est une expression constante ayant la valeur 0, le type du résultat est le type pointeur.

Dans la comparaison de type pour les pointeurs, tous les qualificateurs de type ( **`const`** ou **`volatile`** ) dans le type vers lequel le pointeur pointe ne sont pas significatifs, mais le type de résultat hérite des qualificateurs des deux composants du conditionnel.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent différentes utilisations de l'opérateur conditionnel :

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

Cet exemple assigne la valeur absolue de `i` à `j`. Si `i` est inférieur à 0, `-i` est assigné à `j`. Si `i` est supérieur ou égal à 0, `i` est assigné à `j`.

```cpp
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

Dans cet exemple, deux fonctions, `f1` et `f2`, et deux variables, `x` et `y`, sont déclarées. Ultérieurement dans le programme, si deux variables ont la même valeur, la fonction `f1` est appelée. Sinon, c'est `f2` qui est appelée.

## <a name="see-also"></a>Voir aussi

[Opérateur conditionnel : ? :](../cpp/conditional-operator-q.md)
