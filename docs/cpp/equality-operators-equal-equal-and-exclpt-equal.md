---
title: 'Opérateurs d’égalité : == et !='
description: La syntaxe de l’opérateur equal-to et not-equal-to du langage C++ standard est utilisée.
ms.date: 07/23/2020
f1_keywords:
- '!='
- ==
- not_eq_cpp
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 567b83e99dce0354626f08a4788f1343314493b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227541"
---
# <a name="equality-operators--and-"></a>Opérateurs d’égalité : == et !=

## <a name="syntax"></a>Syntaxe

> *expression* **`==`** *expression*\
> *expression* **`!=`** *expression*

## <a name="remarks"></a>Notes

Les opérateurs d'égalité binaires comparent l'égalité ou l'inégalité stricte de leurs opérandes.

Les opérateurs d’égalité, égal à ( **`==`** ) et différent de ( **`!=`** ), ont une priorité plus faible que les opérateurs relationnels, mais ils se comportent de la même façon. Le type de résultat de ces opérateurs est **`bool`** .

L’opérateur égal à ( **`==`** ) retourne **`true`** si les deux opérandes ont la même valeur ; sinon, il retourne **`false`** . L’opérateur différent de ( **`!=`** ) retourne **`true`** si les opérandes n’ont pas la même valeur ; sinon, il retourne **`false`** .

## <a name="operator-keyword-for-"></a>Mot clé Operator pour ! =

C++ spécifie **`not_eq`** comme autre orthographe pour **`!=`** . (Il n’existe aucune autre orthographe pour **`==`** .) En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

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
[Opérateurs intégrés C++, précédence ; et associativité](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs relationnels et d’égalité C](../c-language/c-relational-and-equality-operators.md)
