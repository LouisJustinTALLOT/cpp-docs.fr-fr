---
title: 'Opérateur de bits OU inclusif : |'
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 38def2b1ac585c751699227d2a065b45145d290d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190753"
---
# <a name="bitwise-inclusive-or-operator-"></a>Opérateur de bits OU inclusif : |

## <a name="syntax"></a>Syntaxe

> *expression1* **|** *Expression2*

## <a name="remarks"></a>Notes

L’opérateur de bits OR inclusif ( **&#124;** ) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si l'un des deux bits a pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.

Les deux opérandes de l’opérateur OR inclusif de bits doivent être de types intégraux. Les conversions arithmétiques habituelles traitées dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes.

## <a name="operator-keyword-for-124"></a>Mot clé Operator pour&#124;

L’opérateur **BITOR** est l’équivalent textuel de **&#124;** . Il existe deux façons d’accéder à l’opérateur **BITOR** dans vos programmes : incluez le fichier d’en-tête \<ISO646. h > ou compilez avec l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) (désactivation des extensions de langage).

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

[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs de bits C](../c-language/c-bitwise-operators.md)
