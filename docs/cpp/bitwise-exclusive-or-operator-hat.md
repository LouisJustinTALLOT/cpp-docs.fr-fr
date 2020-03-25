---
title: 'Opérateur de bits OR exclusif : ^'
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 9a44dc60a985729aae79ed0e2e48c44adace647b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190714"
---
# <a name="bitwise-exclusive-or-operator-"></a>Opérateur de bits OR exclusif : ^

## <a name="syntax"></a>Syntaxe

```
expression ^ expression
```

## <a name="remarks"></a>Notes

L’opérateur de bits or exclusif ( **^** ) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si un bit a pour valeur 0 et que l'autre a pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.

Les deux opérandes de l'opérateur de bits OR exclusif doivent être de types intégraux. Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes.

## <a name="operator-keyword-for-"></a>Mot clé d'opérateur pour ^

L’opérateur **Xor** est l’équivalent textuel de **^** . Il existe deux façons d’accéder à l’opérateur **Xor** dans vos programmes : incluez le fichier d’en-tête `iso646.h`ou compilez avec l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) (désactivation des extensions de langage).

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

[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
