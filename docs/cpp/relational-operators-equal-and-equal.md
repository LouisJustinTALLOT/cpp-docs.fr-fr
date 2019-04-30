---
title: 'Opérateurs relationnels : &lt;, &gt;, &lt;=, et &gt;='
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
ms.openlocfilehash: 52a3c10e6da42f6c181d3f93de13168e22141bec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404752"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Opérateurs relationnels : &lt;, &gt;, &lt;=, et &gt;=

## <a name="syntax"></a>Syntaxe

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Notes

Les opérateurs relationnels binaires déterminent les relations suivantes :

- Inférieur à (**\<**)

- Supérieur à (**>**)

- Inférieur ou égal à (**\<=**)

- Supérieur ou égal à (**>=**)

Les opérateurs relationnels ont une associativité de gauche à droite. Les deux opérandes des opérateurs relationnels doivent être de type arithmétique ou pointeur. Ils génèrent des valeurs de type **bool**. La valeur retournée est **false** (0) si la relation dans l’expression est false ; sinon, la valeur retournée est **true** (1).

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

Les expressions dans l’exemple précédent doivent être placées entre parenthèses, car l’opérateur d’insertion de flux (**<<**) a une priorité plus élevée que les opérateurs relationnels. Par conséquent, la première expression sans parenthèses est évaluée comme suit :

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Les conversions arithmétiques habituelles traitées dans [Conversions Standard](standard-conversions.md) sont appliquées aux opérandes de types arithmétiques.

## <a name="comparing-pointers"></a>Comparaison des pointeurs

Lorsque deux pointeurs vers des objets du même type sont comparés, le résultat est déterminé par l'emplacement des objets pointés figurant dans l'espace d'adressage du programme. Pointeurs peuvent également être comparées à une expression constante qui correspond à 0 ou à un pointeur de type `void *`. Si une comparaison de pointeur est effectuée avec un pointeur de type `void *`, l’autre pointeur est implicitement converti en type `void *`. Ensuite la comparaison est effectuée.

Deux pointeurs de types différents ne peuvent pas être comparés à moins que :

- Un type est un type de classe dérivé de l'autre type.

- Au moins un des pointeurs est explicitement converti (cast) en type `void *`. (L’autre pointeur est implicitement converti en type `void *` pour la conversion.)

Deux pointeurs du même type qui pointent vers le même objet ont la garantie d'être de comparer une valeur égale. Si deux pointeurs vers des membres non statique d'un objet sont comparés, les règles suivantes s'appliquent :

- Si le type de classe n’est pas un **union**, et si les deux membres ne sont pas séparés par un *spécificateur d’accès*, tel que **public**, **protégé**, ou **privé**, le pointeur vers le membre déclaré dernier fera une comparaison supérieure à celle du pointeur vers le membre déclaré précédemment.

- Si les deux membres sont séparés par un *spécificateur d’accès*, les résultats sont indéfinis.

- Si le type de classe est un **union**, pointeurs vers des membres de données différents dans qui **union** égal de comparaison.

Si les deux pointeurs pointent vers des éléments du même tableau ou vers l'avant dernier élément du tableau, le pointeur vers l'objet avec l'indice le plus élevé compare une valeur supérieure. La comparaison des pointeurs est garantie comme étant valide uniquement lorsque les pointeurs font référence à des objets du même tableau ou à l'emplacement situé après la fin du tableau.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs relationnels et d’égalité C](../c-language/c-relational-and-equality-operators.md)