---
title: Opérateur de bits AND :&amp;
description: Syntaxe et utilisation de l’opérateur de bits and du langage C++ standard.
ms.date: 07/23/2020
f1_keywords:
- bitand_cpp
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: 7e78e4003a31ee59ebd974275df784b7a76e73ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229114"
---
# <a name="bitwise-and-operator-amp"></a>Opérateur de bits AND :&amp;

## <a name="syntax"></a>Syntaxe

> *expression* **`&`** *expression*

## <a name="remarks"></a>Notes

L’opérateur de bits AND ( **`&`** ) compare chaque bit du premier opérande au bit correspondant du second opérande. Si les deux bits ont pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.

Les deux opérandes de l’opérateur de bits AND doivent avoir des types intégraux. Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour &

C++ spécifie **`bitand`** comme autre orthographe pour **`&`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

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

[Opérateurs, priorité et associativité C++ intégrés](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs de bits C](../c-language/c-bitwise-operators.md)
