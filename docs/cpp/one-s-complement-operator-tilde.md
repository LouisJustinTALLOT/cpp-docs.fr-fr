---
title: 'Opérateur de complément à 1 : ~'
description: La syntaxe et l’utilisation de l’opérateur de complément à un langage C++ standard.
ms.date: 07/23/2020
f1_keywords:
- "~"
- compl_cpp
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 89c67855cd67df2af315cea941b487e7462889b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227242"
---
# <a name="ones-complement-operator-"></a>Opérateur de complément à 1 : ~

## <a name="syntax"></a>Syntaxe

```cpp
~ cast-expression
```

## <a name="remarks"></a>Notes

L’opérateur de complément à un ( **`~`** ), parfois appelé opérateur de *complément de bits* , génère un complément à un au niveau du bit de son opérande. Autrement dit, chaque bit qui est 1 dans l’opérande est 0 dans le résultat. Inversement, chaque bit qui est 0 dans l’opérande est 1 dans le résultat. L'opérande de l'opérateur de complément à un doit être un type intégral.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour ~

C++ spécifie **`compl`** comme autre orthographe pour **`~`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="example"></a>Exemple

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

Dans cet exemple, la nouvelle valeur assignée à `y` est le complément à 1 de la valeur non signée 0xFFFF ou 0x0000.

La promotion d’un intégral est exécutée sur des opérandes intégraux. Le type sur lequel l’opérande est promu est le type résultant. Pour plus d’informations sur la promotion intégrale, consultez [conversions standard](standard-conversions.md).

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](expressions-with-unary-operators.md)<br/>
[Opérateurs, priorité et associativité C++ intégrés](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs arithmétiques unaires](../c-language/unary-arithmetic-operators.md)
