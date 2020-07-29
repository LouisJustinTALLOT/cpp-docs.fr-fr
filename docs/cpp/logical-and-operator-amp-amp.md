---
title: Opérateur AND logique :&amp;&amp;
description: Syntaxe et utilisation de l’opérateur et logique du langage C++ standard.
ms.date: 07/23/2020
f1_keywords:
- '&&'
- and_cpp
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: 431e76a2943c2373d6191f1fbe9f14c54cfaa6c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223692"
---
# <a name="logical-and-operator-ampamp"></a>Opérateur AND logique :&amp;&amp;

## <a name="syntax"></a>Syntaxe

> *expression* **`&&`** *expression*

## <a name="remarks"></a>Notes

L’opérateur AND logique ( **&&** ) retourne **`true`** si les deux opérandes sont **`true`** et retournent la valeur dans le **`false`** cas contraire. Les opérandes sont implicitement convertis en type **`bool`** avant l’évaluation, et le résultat est de type **`bool`** . L'opérateur logique présente une associativité de gauche à droite.

Les opérandes de l’opérateur logique AND n’ont pas besoin d’avoir le même type, mais ils doivent avoir un type booléen, intégral ou pointeur. Les opérandes sont souvent des expressions relationnelles ou d’égalité.

Le premier opérande est complètement évalué et tous les effets secondaires sont terminés avant que l’évaluation de l’expression AND logique continue.

Le deuxième opérande est évalué uniquement si le premier opérande a la valeur **`true`** (différente de zéro). Cette évaluation élimine l’évaluation inutile du second opérande lorsque l’expression AND logique est **`false`** . Vous pouvez utiliser cette évaluation de court-circuit pour empêcher le déréférencement du pointeur NULL, comme indiqué dans l'exemple suivant :

```cpp
char *pch = 0;
// ...
(pch) && (*pch = 'a');
```

Si `pch` est null (0), le côté droit de l'expression n'est jamais évalué. Cette évaluation de court-circuit rend l’assignation par le biais d’un pointeur null impossible.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour &&

C++ spécifie **`and`** comme autre orthographe pour **`&&`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="example"></a>Exemple

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs, priorité et associativité C++ intégrés](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs logiques C](../c-language/c-logical-operators.md)
