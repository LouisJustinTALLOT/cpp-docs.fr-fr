---
title: 'Au niveau du bit opérateur OR inclusif : |'
ms.date: 06/14/2018
f1_keywords:
- bitor
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 848bf3b2ec61084b59ab5b1ee6807f6066a4675e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184284"
---
# <a name="bitwise-inclusive-or-operator-"></a>Au niveau du bit opérateur OR inclusif : |

## <a name="syntax"></a>Syntaxe

> *expression1* **|** *expression2*

## <a name="remarks"></a>Notes

L’opérateur OR inclusif au niveau du bit (**&#124;**) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si l'un des bits est 1, le bit correspondant de résultat a la valeur 1. Sinon, le bit de résultat correspondant a la valeur 0.

Les deux opérandes de l’opérateur OR inclusif de bits doivent être de types intégraux. Les conversions arithmétiques habituelles traitées dans [Conversions Standard](standard-conversions.md) sont appliquées aux opérandes.

## <a name="operator-keyword-for-124"></a>Mot clé operator pour&#124;

Le **bitor** opérateur est l’équivalent textuel de **&#124;**. Il existe deux façons d’accéder à la **bitor** opérateur dans vos programmes : inclure le fichier d’en-tête \<iso646.h >, ou compiler avec la [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).

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