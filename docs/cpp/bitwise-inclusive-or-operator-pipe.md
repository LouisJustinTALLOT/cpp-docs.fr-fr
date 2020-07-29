---
title: 'Opérateur de bits OR inclusif : &#124;'
description: Syntaxe de l’opérateur OR inclusif de langage C++ standard et utilisation.
ms.date: 07/23/2020
f1_keywords:
- '|'
- bitor_cpp
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 76f80c2101b3acfac71dc4d8ad1be4a999f69aa5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229088"
---
# <a name="bitwise-inclusive-or-operator-124"></a>Opérateur de bits OR inclusif : &#124;

## <a name="syntax"></a>Syntaxe

> *expression1* **`|`** *Expression2*

## <a name="remarks"></a>Notes

L’opérateur de bits OR inclusif ( **`|`** ) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si l'un des deux bits a pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.

Les deux opérandes de l’opérateur doivent avoir des types intégraux. Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes.

## <a name="operator-keyword-for-124"></a>Mot clé Operator pour &#124;

C++ spécifie **`bitor`** comme autre orthographe pour **`|`** . En C, l’orthographe alternative est fournie sous la forme d’une macro dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est un mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="example"></a>Exemple

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs de bits C](../c-language/c-bitwise-operators.md)
