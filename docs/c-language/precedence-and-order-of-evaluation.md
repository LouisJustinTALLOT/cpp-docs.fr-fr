---
title: Priorité et ordre d'évaluation
ms.date: 11/04/2016
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
ms.openlocfilehash: 88d0256e2ce948fbdfffb24037517690ef4b7cb7
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152493"
---
# <a name="precedence-and-order-of-evaluation"></a>Priorité et ordre d'évaluation

La priorité et l’associativité des opérateurs C affectent le regroupement et l’évaluation des opérandes dans les expressions. La priorité d'un opérateur est significative uniquement si d'autres opérateurs dotés d'une priorité supérieure ou inférieure sont présents. Les expressions avec des opérateurs de priorité supérieure sont évaluées en premier. La priorité peut également être décrite par le mot « liaison ». Les opérateurs dotés d'une priorité plus élevée sont considérés comme ayant une liaison plus stricte.

Le tableau ci-dessous résume la priorité et l'associativité (l'ordre dans lequel les opérandes sont évalués) des opérateurs C en les répertoriant par ordre de priorité, de la plus élevée à la plus basse. Lorsque plusieurs opérateurs apparaissent ensemble, ils ont une priorité égale et ils sont évalués en fonction de leur associativité. Les opérateurs figurant dans le tableau sont décrits dans les sections commençant par [Opérateurs suffixés](../c-language/postfix-operators.md). Le reste de cette section fournit des informations générales sur la priorité et l'associativité.

## <a name="precedence-and-associativity-of-c-operators"></a>Priorité et associativité des opérateurs C

|Symbole <sup>1</sup>|Type d'opération|l'associativité|
|-------------|-----------------------|-------------------|
|**\[ ] ( ) . ->**<br /><br />**++** **--** (suffixe)|Expression|De gauche à droite|
**sizeof & \* + - ~ !**<br /><br />**++ --** (préfixe)|Unaire|De droite à gauche|
|*casts de type*|Unaire|De droite à gauche|
|**\* / %**|Multiplication|De gauche à droite|
|**+ -**|Addition|De gauche à droite|
|**\<\< >>**|Décalage au niveau du bit|De gauche à droite|
|**\< > \<= >=**|Relation|De gauche à droite|
|**== !=**|Égalité|De gauche à droite|
|**&**|Opération de bits AND|De gauche à droite|
|**^**|Opération de bits OR exclusive|De gauche à droite|
|**&#124;**|Opération de bits OR inclusive|De gauche à droite|
|**&&**|AND logique|De gauche à droite|
|**&#124;&#124;**|OR logique|De gauche à droite|
|**? :**|Expression-conditionnelle|De droite à gauche|
|**= \*= /= %=**<br /><br /> **+= -= \<\<= >>= &=**<br /><br /> **^= &#124;=**|Affectation simple et composée<sup>2</sup>|De droite à gauche|
|**,**|Évaluation séquentielle|De gauche à droite|

1. Les opérateurs sont répertoriés par ordre de priorité descendant. Si plusieurs opérateurs apparaissent sur la même ligne ou dans un groupe, ils ont la même priorité.

1. Tous les opérateurs d'assignation simple et composée ont une même priorité.

Une expression peut contenir plusieurs opérateurs avec une même priorité. Lorsque plusieurs opérateurs de ce type apparaissent au même niveau dans une expression, l'évaluation se poursuit selon l'associativité de l'opérateur, de droite à gauche ou de gauche à droite. Le sens de l’évaluation n’affecte pas les résultats des expressions comprenant plusieurs opérateurs de multiplication (<strong>\*</strong>), plusieurs opérateurs d’addition (**+**) ou plusieurs opérateurs binaires au niveau du bit (**&**, **&#124;** ou **^**), à un même niveau. L'ordre des opérations n'est pas défini par le langage. Le compilateur est libre d'évaluer de telles expressions dans n'importe quel ordre, s'il peut garantir un résultat cohérent.

Seuls les opérateurs d’évaluation séquentielle (**,**), les opérateurs logiques AND (**&&**), les opérateurs logiques OR (**||**), les opérateurs d’expression conditionnelle (**? :**) et les opérateurs d’appel de fonction constituent des points de séquence, et garantissent par conséquent un ordre particulier d’évaluation pour leurs opérandes. L'opérateur d'appel de fonction correspond au jeu de parenthèses suivant l'identificateur de fonction. L’opérateur d’évaluation séquentielle (**,**) est assuré d’évaluer ses opérandes de gauche à droite. (Notez que l'opérateur virgule dans un appel de fonction n'est pas le même que l'opérateur d'évaluation-séquentielle et ne fournit pas de garantie.) Pour plus d’informations, consultez [Points de séquence](../c-language/c-sequence-points.md).

Les opérateurs logiques garantissent également l’évaluation de leurs opérandes de gauche à droite. Toutefois, ils évaluent le plus petit nombre d'opérandes nécessaires pour déterminer le résultat de l'expression. Cela est appelé « évaluation de court-circuit ». Ainsi, certains opérandes de l'expression ne peuvent pas être évalués. Par exemple, dans l'expression

`x && y++`

le second opérande, `y++`, est évaluée uniquement si `x` est vrai (valeur différente de zéro). Par conséquent, `y` n'est pas incrémenté si `x` a la valeur False (0).

## <a name="examples"></a>Exemples

La liste suivante montre comment le compilateur lie automatiquement plusieurs exemples d'expressions :

|Expression|Liaison automatique|
|----------------|-----------------------|
|a & b &#124;&#124; c|(a & b) &#124;&#124; c|
|a = b &#124;&#124; c|a = (b &#124;&#124; c)|
|q && r &#124;&#124; s--|(q && r) &#124;&#124; s--|

Dans la première expression, l’opérateur AND au niveau du bit (**&**) a une priorité plus élevée que l’opérateur OR logique (**||**). `a & b` est donc le premier opérande de l’opération OR logique.

Dans la deuxième expression, l’opérateur OR logique (**||**) a une priorité plus élevée que l’opérateur d’assignation simple (**=**). `b || c` est donc regroupé comme opérande de droite dans l’assignation. Notez que la valeur assignée à `a` est 0 ou 1.

La troisième expression montre une expression formée correctement qui peut produire un résultat inattendu. L’opérateur AND logique (**&&**) a une priorité plus élevée que l’opérateur OR logique (**||**). `q && r` est donc regroupé comme opérande. Comme les opérateurs logiques garantissent l’évaluation des opérandes de gauche à droite, `q && r` est évalué avant `s--`. Toutefois, si `q && r` correspond à une valeur différente de zéro, `s--` n’est pas évalué et `s` n’est pas décrémenté. Si le fait de ne pas décrémenter `s` peut poser problème dans votre programme, `s--` doit apparaître comme premier opérande de l’expression ou `s` doit être décrémenté dans une opération distincte.

L'expression suivante est non conforme et produit un message de diagnostic au moment de la compilation :

|Expression non conforme|Regroupement par défaut|
|------------------------|----------------------|
|p == 0 ? p += 1: p += 2|( p == 0 ? p += 1 : p ) += 2|

Dans cette expression, l’opérateur d’égalité (**==**) a la priorité la plus élevée. `p == 0` est donc regroupé comme opérande. L’opérateur d’expression conditionnelle (**? :**) possède la deuxième priorité la plus élevée. Son premier opérande est `p == 0` et son deuxième opérande est `p += 1`. Toutefois, le dernier opérande de l'opérateur d'expression conditionnelle est considéré comme étant `p` plutôt que `p += 2`, étant donné que cette occurrence de `p` se lie plus étroitement à l'opérateur d'expression conditionnelle qu'à l'opérateur d'assignation composée. Une erreur de syntaxe se produit car `+= 2` n'a pas d'opérande gauche. Vous devez utiliser des parenthèses pour éviter ce type d'erreurs et rédiger un code plus lisible. Par exemple, vous pouvez utiliser des parenthèses, comme indiqué ci-dessous, pour corriger et clarifier l'exemple précédent :

`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`

## <a name="see-also"></a>Voir aussi

[Opérateurs C](../c-language/c-operators.md)
