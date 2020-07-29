---
title: 'Opérateur OR logique :  &#124;&#124;'
description: Syntaxe et utilisation de l’opérateur ou logique du langage C++ standard.
ms.date: 07/23/2020
f1_keywords:
- '||'
- or_cpp
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 1845aef59f88d5dd044cefedd21cb618e1102e13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225993"
---
# <a name="logical-or-operator-124124"></a>Opérateur OR logique :  &#124;&#124;

## <a name="syntax"></a>Syntaxe

> *Logical-or-expression* **`||`** *expression and logique*

## <a name="remarks"></a>Notes

L’opérateur OR logique ( **`||`** ) retourne la valeur booléenne **`true`** si l’un des opérandes, ou les deux, est et retourne la valeur dans le **`true`** **`false`** cas contraire. Les opérandes sont implicitement convertis en type **`bool`** avant l’évaluation, et le résultat est de type **`bool`** . L'opérateur OR logique présente une associativité de gauche à droite.

Les opérandes de l’opérateur OR logique ne doivent pas nécessairement avoir le même type, mais ils doivent être de type booléen, intégral ou pointeur. Les opérandes sont souvent des expressions relationnelles ou d’égalité.

Le premier opérande doit être complètement évalué et tous les effets secondaires terminés pour que l’évaluation de l’expression OR logique se poursuive.

Le deuxième opérande est évalué uniquement si le premier opérande a la valeur **`false`** , car l’évaluation n’est pas nécessaire lorsque l’expression or logique est **`true`** . Il s’agit d' *une évaluation de court-circuit* .

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

Dans l’exemple ci-dessus, si `x` est égal à `w` , à ou à `y` `z` , le deuxième argument de la `printf` fonction prend la **`true`** valeur, qui est ensuite promu en entier et la valeur 1 est imprimée. Sinon, elle prend **`false`** la valeur et la valeur 0 est imprimée. Dès que l’une des conditions prend la valeur **`true`** , l’évaluation s’arrête.

## <a name="operator-keyword-for-124124"></a>Mot clé Operator pour &#124;&#124;

C++ spécifie **`or`** comme autre orthographe pour **`||`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="example"></a>Exemple

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs, priorité et associativité C++ intégrés](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs logiques C](../c-language/c-logical-operators.md)
