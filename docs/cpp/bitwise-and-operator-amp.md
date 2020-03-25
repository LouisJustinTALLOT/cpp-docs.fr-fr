---
title: 'Opérateur de bits AND : &amp;'
ms.date: 11/04/2016
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b5c99d19be3461b10a1126dea3a45d308c0fc558
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181289"
---
# <a name="bitwise-and-operator-amp"></a>Opérateur de bits AND : &amp;

## <a name="syntax"></a>Syntaxe

```
expression & expression
```

## <a name="remarks"></a>Notes

Les expressions peuvent être d'autres expressions-et, ou (en fonction des restrictions de type indiquées ci-dessous) des expressions d'égalité, des expressions relationnelles, des expressions additives, des expressions multiplicatives, des expressions de pointeur vers membre, des expressions de casts, des expressions unaires, des expressions suffixées ou des expressions primaires.

L’opérateur de bits AND ( **&** ) compare chaque bit du premier opérande au bit correspondant du second opérande. Si les deux bits ont pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.

Les deux opérandes de l’opérateur de bits AND doivent être de types intégraux. Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md)sont appliquées aux opérandes.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour &

L’opérateur **BITAND** est l’équivalent textuel de **&** . Il existe deux façons d’accéder à l’opérateur **BITAND** dans vos programmes : incluez le fichier d’en-tête `iso646.h`ou compilez avec l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) (désactivation des extensions de langage).

## <a name="example"></a>Exemple

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs intégrés, priorité et associativité C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs de bits C](../c-language/c-bitwise-operators.md)
