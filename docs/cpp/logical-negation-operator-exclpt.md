---
title: 'Opérateur de négation logique : !'
description: Syntaxe et utilisation de l’opérateur de négation logique du langage C++ standard.
ms.date: 07/23/2020
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: fdd2e7a71b791375f898372d058a5eeb2afc59f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223679"
---
# <a name="logical-negation-operator-"></a>Opérateur de négation logique : !

## <a name="syntax"></a>Syntaxe

> **`!`***Cast-expression*

## <a name="remarks"></a>Notes

L’opérateur de négation logique ( **`!`** ) inverse la signification de son opérande. L’opérande doit être de type arithmétique ou pointeur (ou une expression qui a pour valeur le type arithmétique ou pointeur). L’opérande est implicitement converti en type **`bool`** . Le résultat est **`true`** si l’opérande converti est **`false`** ; le résultat est **`false`** si l’opérande converti est **`true`** . Le résultat est de type **`bool`** .

Pour une expression `e` , l’expression unaire `!e` est équivalente à l’expression `(e == 0)` , sauf lorsque des opérateurs surchargés sont impliqués.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour !

C++ spécifie **`not`** comme autre orthographe pour **`!`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="example"></a>Exemple

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs arithmétiques unaires](../c-language/unary-arithmetic-operators.md)<br/>
