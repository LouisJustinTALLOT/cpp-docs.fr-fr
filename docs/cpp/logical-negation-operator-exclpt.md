---
title: 'Opérateur de négation logique : !'
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446540"
---
# <a name="logical-negation-operator-"></a>Opérateur de négation logique : !

## <a name="syntax"></a>Syntaxe

```
! cast-expression
```

## <a name="remarks"></a>Notes

L’opérateur de négation logique ( **!** ) inverse la signification de son opérande. L’opérande doit être de type arithmétique ou pointeur (ou une expression qui a pour valeur le type arithmétique ou pointeur). L’opérande est implicitement converti en type **bool**. Le résultat est TRUE si l’opérande converti est FALSe ; le résultat est FALSe si l’opérande converti est TRUE. Le résultat est de type **bool**.

Pour une expression *e*, l’expression unaire `!e` est équivalente à l’expression `(e == 0)`, sauf lorsque des opérateurs surchargés sont impliqués.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour !

L’opérateur **not** est une autre orthographe de **!** . Il existe deux façons d’accéder à l’opérateur **not** dans vos programmes : incluez le fichier d’en-tête \<ISO646. h > ou compilez avec l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) (désactivation des extensions de langage).

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
