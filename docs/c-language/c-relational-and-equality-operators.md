---
title: Opérateurs relationnels et d'égalité C
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 9ae5a31b5f4b81876d2fe518635a9766d2b5323c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227944"
---
# <a name="c-relational-and-equality-operators"></a>Opérateurs relationnels et d'égalité C

Les opérateurs binaires relationnels et d’égalité comparent leur premier opérande à leur second opérande pour tester la validité de la relation spécifiée. Le résultat d'une expression relationnelle est 1 si la relation testée a la valeur true et 0 si elle a la valeur false. Le type du résultat est **`int`** .

**Syntaxe**

*Relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relationnelle-expression* **&lt;** *Shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relationnelle-expression* **>** *Shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relationnelle-expression* **&lt;=** *Shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relationnelle-expression* **>=** *Shift-expression*

*equality-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*égalité-expression* **==** *relationnelle-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **!=** *relational-expression*

Les opérateurs relationnels et d'égalité testent les relations suivantes :

|Opérateur|Relation testée|
|--------------|-------------------------|
|**&lt;**|Premier opérande inférieur au second opérande|
|**>**|Premier opérande supérieur au second opérande|
|**&lt;=**|Premier opérande inférieur ou égal au second opérande|
|**>=**|Premier opérande supérieur ou égal au second opérande|
|**==**|Premier opérande égal au second opérande|
|**!=**|Premier opérande différent du second opérande|

Les quatre premiers opérateurs dans la liste ci-dessus ont une priorité plus élevée que les opérateurs d'égalité (`==` et `!=`). Consultez les informations de priorité dans la table [Priorité et associativité des opérateurs C](../c-language/precedence-and-order-of-evaluation.md).

Les opérandes peuvent être de type intégral, flottant ou pointeur. Les types d'opérande peuvent être différents. Les opérateurs relationnels exécutent les conversions arithmétiques habituelles sur les opérandes de type intégral et flottant. En outre, vous pouvez utiliser les combinaisons suivantes des types d'opérande avec les opérateurs relationnels et d'égalité :

- Les deux opérandes de tout opérateur relationnel ou d'égalité peuvent être des pointeurs vers le même type. Pour les opérateurs d'égalité (`==`) et d'inégalité (`!=`), le résultat de la comparaison indique si les deux pointeurs pointent vers le même emplacement de mémoire. Pour les autres opérateurs relationnels ( **\<**, **>** , **\<**=, and **>** =), le résultat de la comparaison indique la position relative des deux adresses mémoire des objets vers lesquels pointe. Les opérateurs relationnels comparent uniquement les décalages.

   La comparaison de pointeur est définie uniquement pour les parties du même objet. Si les pointeurs font référence aux membres d'un tableau, la comparaison est équivalente à la comparaison des indices correspondants. L'adresse du premier élément du tableau est « inférieure à » l'adresse du dernier élément. Dans le cas de structures, les pointeurs vers des membres de structures déclarés ultérieurement sont « supérieurs à » aux pointeurs vers des membres déclarés précédemment dans la structure. Les pointeurs vers des membres de la même union sont égaux.

- Une valeur de pointeur peut être comparée à la valeur de constante 0 pour l'égalité (`==`) ou l'inégalité (`!=`). Un pointeur avec une valeur de 0 est appelé pointeur « Null » ; autrement dit, il ne pointe pas vers un emplacement de mémoire valide.

- Les opérateurs d’égalité suivent les mêmes règles que les opérateurs relationnels, mais autorisent des possibilités supplémentaires : un pointeur peut être comparé à une expression intégrale constante avec la valeur 0, ou à un pointeur vers **`void`** . Si deux pointeurs sont tous deux des pointeurs Null, ils sont considérés comme égaux. Les opérateurs d'égalité comparent à la fois le segment et le décalage.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent des opérateurs relationnels et d'égalité.

```C
int x = 0, y = 0;
if ( x < y )
```

Étant donné que `x` et `y` sont égaux, l'expression dans cet exemple génère la valeur 0.

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

Le fragment dans cet exemple affecte à chaque élément d'`array` une constante caractère Null.

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

Ces instructions déclarent une variable d'énumération nommée `col` avec la balise `color`. À tout moment, la variable peut contenir une valeur entière 0, 1 ou 2, qui représente un des éléments de l'ensemble d'énumération `color` : le rouge, le blanc ou le vert, respectivement. Si `col` contient 0 lorsque l' **`if`** instruction est exécutée, toutes les instructions dépendant de l' **`if`** seront exécutées.

## <a name="see-also"></a>Voir aussi

[Opérateurs relationnels : \<, > ,\<=, and >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[Opérateurs d’égalité : = = et ! =](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
