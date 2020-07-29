---
title: 'Opérateur de bits OU exclusif : ^'
description: Syntaxe et utilisation de l’opérateur ou exclusif du langage C++ standard.
ms.date: 07/23/2020
f1_keywords:
- xor_cpp
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 0f64b9f90b70756d29fcabb361cc07abe58e0a54
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229101"
---
# <a name="bitwise-exclusive-or-operator-"></a>Opérateur de bits OU exclusif : ^

## <a name="syntax"></a>Syntaxe

> *expression* **`^`** *expression*

## <a name="remarks"></a>Notes

L’opérateur de bits or exclusif ( **`^`** ) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si le bit dans le premier opérande est 0 et que l’autre bit est 1, le bit de résultat correspondant a la valeur 1. Sinon, il a pour valeur 0.

Les deux opérandes de l’opérateur doivent avoir des types intégraux. Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour ^

C++ spécifie **`xor`** comme autre orthographe pour **`^`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.


## <a name="example"></a>Exemple

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
