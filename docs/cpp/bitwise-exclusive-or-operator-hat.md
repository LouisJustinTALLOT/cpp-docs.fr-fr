---
title: 'Exclusif au niveau du bit ou opérateur : ^ | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d080fa28e8f70cb6a4086709c4a5fc6215c4519
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409850"
---
# <a name="bitwise-exclusive-or-operator-"></a>Opérateur de bits OR exclusif : ^
## <a name="syntax"></a>Syntaxe  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>Notes  
L’opérateur OR exclusif au niveau du bit (**^**) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si un bit est 0 et que l'autre bit est 1, le bit de résultat correspondant prend la valeur 1. Sinon, le bit de résultat correspondant a la valeur 0.  
  
Les deux opérandes de l’opérateur de bits OR exclusif doivent être de types intégraux. Les conversions arithmétiques courantes traitées dans [Conversions Standard](standard-conversions.md) sont appliquées aux opérandes.  
  
## <a name="operator-keyword-for-"></a>Mot clé d'opérateur pour ^  
Le **xor** opérateur est l’équivalent textuel de **^**. Il existe deux moyens d’accéder à la **xor** opérateur dans vos programmes : incluez le fichier d’en-tête `iso646.h`, ou compilez avec le [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).  
  
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


