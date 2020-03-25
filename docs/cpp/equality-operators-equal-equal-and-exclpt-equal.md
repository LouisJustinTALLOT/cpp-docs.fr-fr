---
title: "Opérateurs d'égalité : == et !="
ms.date: 11/04/2016
f1_keywords:
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 8a0c08f438528caeaac6d5e52e806a36fe56dd25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189245"
---
# <a name="equality-operators--and-"></a>Opérateurs d'égalité : == et !=

## <a name="syntax"></a>Syntaxe

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Notes

Les opérateurs d'égalité binaires comparent l'égalité ou l'inégalité stricte de leurs opérandes.

Les opérateurs d'égalité, égal à (`==`) et différent de (`!=`), ont une priorité inférieure aux opérateurs relationnels, mais ils se comportent de la même manière. Le type de résultat de ces opérateurs est **bool**.

L’opérateur égal à (`==`) retourne la valeur **true** (1) si les deux opérandes ont la même valeur ; Sinon, elle retourne **false** (0). L’opérateur « égal à » (`!=`) retourne la valeur **true** si les opérandes n’ont pas la même valeur ; Sinon, elle retourne **false**.

## <a name="operator-keyword-for-"></a>Mot clé d'opérateur pour !=

L'opérateur `not_eq` est l'équivalent textuel de `!=`. Il existe deux façons d’accéder à l’opérateur `not_eq` dans vos programmes : incluez le fichier d’en-tête `iso646.h`ou compilez avec l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) (désactivation des extensions de langage).

## <a name="example"></a>Exemple

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

Les opérateurs d'égalité permettent de comparer les pointeurs à des membres du même type. Dans ce type de comparaison, les conversions de pointeur vers membre sont effectuées. Les conversions de pointeur vers membre peuvent également être comparées à une expression constante qui a pour valeur 0.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs relationnels et d’égalité C](../c-language/c-relational-and-equality-operators.md)
