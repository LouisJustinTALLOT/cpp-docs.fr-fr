---
title: Opérateurs logiques C
ms.date: 06/14/2018
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
ms.openlocfilehash: 5df0c0f16bdf298c47a6a0699ec10c7392ab84ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651267"
---
# <a name="c-logical-operators"></a>Opérateurs logiques C

Les opérateurs logiques effectuent des opérations de ET logique (**&&**) et de OU logique (**||**).

## <a name="syntax"></a>Syntaxe

*logical-AND-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="remarks"></a>Notes

Les opérateurs logiques n’effectuent pas les conversions arithmétiques habituelles. Au lieu de cela, ils évaluent chaque opérande en termes d’équivalence à 0. Le résultat d’une opération logique est 0 ou 1. Le type du résultat est **int**.

Les opérateurs logiques C sont décrits ci-dessous :

|Opérateur|Description|
|--------------|-----------------|
|**&&**|L’opérateur ET logique produit la valeur 1 si les deux opérandes ont des valeurs différentes de zéro. Si au moins un des opérandes est égal à 0, le résultat est 0. Si le premier opérande d’une opération ET logique est égal à 0, le second opérande n’est pas évalué.|
|**&#124;&#124;**|L’opérateur OU logique effectue une opération OU inclusive sur ses opérandes. Le résultat est 0 si les deux opérandes ont des valeurs de 0. Si au moins un des opérandes a une valeur différente de zéro, le résultat est 1. Si le premier opérande d’une opération OU logique a une valeur différente de zéro, le second opérande n’est pas évalué.|

Les opérandes des expressions ET logique et OU logique sont évalués de gauche à droite. Si la valeur du premier opérande est suffisante pour déterminer le résultat de l’opération, le second opérande n’est pas évalué. Cela est appelé « évaluation de court-circuit ». Il existe un point de séquence après le premier opérande. Pour plus d'informations, consultez [Points de séquence](../c-language/c-sequence-points.md).

## <a name="examples"></a>Exemples

Les exemples suivants illustrent les opérateurs logiques :

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

Dans cet exemple, la fonction **printf** est appelée à afficher un message si `x` est inférieur à `y` et `y` est inférieur à `z`. Si `x` est supérieur à `y`, le second opérande (`y < z`) n’est pas évalué et rien n’est affiché. Notez que cela peut entraîner des problèmes dans les cas où le second opérande a des effets secondaires qui sont utilisés pour une raison quelconque, le second opérande.

```C
printf( "%d" , (x == w || x == y || x == z) );
```

Dans cet exemple, si `x` est égal à `w`, à `y` ou à `z`, le second argument de la fonction **printf** équivaut à true et la valeur 1 est affichée. Dans le cas contraire, il équivaut à false et la valeur 0 est affichée. Dès que l'une des conditions équivaut à true, l'évaluation cesse.

## <a name="see-also"></a>Voir aussi

- [Opérateur AND logique : &&](../cpp/logical-and-operator-amp-amp.md)
- [Opérateur OR logique : &#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
