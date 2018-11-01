---
title: 'Opérateur de négation logique : !'
ms.date: 08/27/2018
f1_keywords:
- '!'
- Not
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 7b37e5108ca01d782c13508c0cd7a96b096cd745
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493723"
---
# <a name="logical-negation-operator-"></a>Opérateur de négation logique : !

## <a name="syntax"></a>Syntaxe

```
! cast-expression
```

## <a name="remarks"></a>Notes

L’opérateur de négation logique (**!**) inverse la signification de son opérande. L’opérande doit être de type arithmétique ou pointeur (ou une expression qui a pour valeur le type arithmétique ou pointeur). L’opérande est converti implicitement en type **bool**. Le résultat est TRUE si l’opérande converti est FALSE ; le résultat est FALSE si l’opérande converti est TRUE. Le résultat est de type **bool**.

Pour une expression *e*, l’expression unaire `!e` est équivalente à l’expression `(e == 0)`, sauf lorsque les opérateurs surchargés sont impliqués.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour !

Le **pas** opérateur est une orthographe de remplacement de **!**. Il existe deux façons d’accéder à la **pas** opérateur dans vos programmes : inclure le fichier d’en-tête \<iso646.h >, ou compiler avec la [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).

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
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs arithmétiques unaires](../c-language/unary-arithmetic-operators.md)<br/>
