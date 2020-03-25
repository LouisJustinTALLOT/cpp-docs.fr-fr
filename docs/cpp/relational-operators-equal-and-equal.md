---
title: 'Opérateurs relationnels : &lt;, &gt;, &lt;= et &gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 38e05b78d334ca690d9523797f7ca1813834c5d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179118"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Opérateurs relationnels : &lt;, &gt;, &lt;= et &gt;=

## <a name="syntax"></a>Syntaxe

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Notes

Les opérateurs relationnels binaires déterminent les relations suivantes :

- Inférieur à ( **\<** )

- Supérieur à ( **>** )

- Inférieur ou égal à ( **\<=** )

- Supérieur ou égal à ( **>=** )

Les opérateurs relationnels ont une associativité de gauche à droite. Les deux opérandes des opérateurs relationnels doivent être de type arithmétique ou pointeur. Elles produisent des valeurs de type **bool**. La valeur retournée est **false** (0) si la relation dans l’expression est false ; dans le cas contraire, la valeur retournée est **true** (1).

## <a name="example"></a>Exemple

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

Les expressions dans l’exemple précédent doivent être placées entre parenthèses, car l’opérateur d’insertion de flux ( **<<** ) a une priorité plus élevée que les opérateurs relationnels. Par conséquent, la première expression sans parenthèses est évaluée comme suit :

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes de types arithmétiques.

## <a name="comparing-pointers"></a>Comparaison des pointeurs

Lorsque deux pointeurs vers des objets du même type sont comparés, le résultat est déterminé par l'emplacement des objets pointés figurant dans l'espace d'adressage du programme. Les pointeurs peuvent également être comparés à une expression constante qui prend la valeur 0 ou un pointeur de type `void *`. Si une comparaison de pointeur est effectuée par rapport à un pointeur de type `void *`, l’autre pointeur est implicitement converti en type `void *`. Ensuite la comparaison est effectuée.

Deux pointeurs de types différents ne peuvent pas être comparés à moins que :

- Un type est un type de classe dérivé de l'autre type.

- Au moins un des pointeurs est explicitement converti (cast) en type `void *`. (L’autre pointeur est implicitement converti en type `void *` pour la conversion.)

Deux pointeurs du même type qui pointent vers le même objet ont la garantie d'être de comparer une valeur égale. Si deux pointeurs vers des membres non statique d'un objet sont comparés, les règles suivantes s'appliquent :

- Si le type de classe n’est pas une **Union**et si les deux membres ne sont pas séparés par un *spécificateur d’accès*, tel que **public**, **protected**ou **Private**, le pointeur vers le membre déclaré Last sera comparé au pointeur vers le membre déclaré précédemment.

- Si les deux membres sont séparés par un *spécificateur d’accès*, les résultats ne sont pas définis.

- Si le type de classe est une **Union**, les pointeurs vers des membres de données différents dans cette **Union** sont égaux.

Si les deux pointeurs pointent vers des éléments du même tableau ou vers l'avant dernier élément du tableau, le pointeur vers l'objet avec l'indice le plus élevé compare une valeur supérieure. La comparaison des pointeurs est garantie comme étant valide uniquement lorsque les pointeurs font référence à des objets du même tableau ou à l'emplacement situé après la fin du tableau.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs relationnels et d’égalité C](../c-language/c-relational-and-equality-operators.md)
