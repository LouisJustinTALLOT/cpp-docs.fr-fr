---
title: 'Opérateur AND au niveau du bit : &amp;'
ms.date: 11/04/2016
f1_keywords:
- bitand
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b7d0d73802a5af7ab71e980d73eaff5c5b3c4bb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575355"
---
# <a name="bitwise-and-operator-amp"></a>Opérateur AND au niveau du bit : &amp;

## <a name="syntax"></a>Syntaxe

```
expression & expression
```

## <a name="remarks"></a>Notes

Les expressions peuvent être d'autres expressions-et, ou (en fonction des restrictions de type indiquées ci-dessous) des expressions d'égalité, des expressions relationnelles, des expressions additives, des expressions multiplicatives, des expressions de pointeur vers membre, des expressions de casts, des expressions unaires, des expressions suffixées ou des expressions primaires.

L’opérateur AND au niveau du bit (**&**) compare chaque bit du premier opérande au bit correspondant du second opérande. Si les deux bits sont 1, le bit de résultat correspondant a la valeur 1. Sinon, le bit de résultat correspondant a la valeur 0.

Les deux opérandes de l’opérateur de bits AND doivent être de types intégraux. Les conversions arithmétiques habituelles traitées dans [Conversions Standard](standard-conversions.md), sont appliquées aux opérandes.

## <a name="operator-keyword-for-"></a>Mot clé operator pour &

Le **bitand** opérateur est l’équivalent textuel de **&**. Il existe deux façons d’accéder à la **bitand** opérateur dans vos programmes : inclure le fichier d’en-tête `iso646.h`, ou compiler avec la [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).

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