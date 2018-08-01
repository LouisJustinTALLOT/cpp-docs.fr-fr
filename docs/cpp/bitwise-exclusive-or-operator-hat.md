---
title: 'Exclusif au niveau du bit ou un opérateur : ^ | Microsoft Docs'
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
ms.openlocfilehash: fe2f64c20c0d741608dfb2631c2e36026a31e8bb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406674"
---
# <a name="bitwise-exclusive-or-operator-"></a>Opérateur de bits OR exclusif : ^
## <a name="syntax"></a>Syntaxe  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>Notes  
L’opérateur OR exclusif au niveau du bit (**^**) compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si un bit est 0 et que l'autre bit est 1, le bit de résultat correspondant prend la valeur 1. Sinon, le bit de résultat correspondant a la valeur 0.  
  
Les deux opérandes de l’opérateur de bits OR exclusif doivent être de types intégraux. Les conversions arithmétiques habituelles traitées dans [Conversions Standard](standard-conversions.md) sont appliquées aux opérandes.  
  
## <a name="operator-keyword-for-"></a>Mot clé d'opérateur pour ^  
Le **xor** opérateur est l’équivalent textuel de **^**. Il existe deux façons d’accéder à la **xor** opérateur dans vos programmes : inclure le fichier d’en-tête `iso646.h`, ou compiler avec la [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).  
  
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