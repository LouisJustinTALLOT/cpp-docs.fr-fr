---
title: "Suffixe des opérateurs d’incrémentation et décrémentation : ++ et--| Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs: C++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cbf22e57abaefc7b14be9c4eab404f7c20cb9359
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Opérateurs suffixés d'incrémentation et de décrémentation : ++ et --
## <a name="syntax"></a>Syntaxe  
  
```  
postfix-expression ++  
postfix-expression --  
```  
  
## <a name="remarks"></a>Remarques  
 C++ fournit des opérateurs d'incrémentation et de décrémentation préfixés et suffixés. Cette section décrit uniquement les opérateurs d'incrémentation et de décrémentation suffixés. (Pour plus d’informations, consultez [préfixe opérateurs d’incrémentation et décrémentation](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) La différence entre les deux est que, dans la notation suffixée, l’opérateur apparaît après *postfix-expression*, alors que dans la notation de préfixe, l’opérateur apparaît avant *expression.* L'exemple suivant montre un opérateur d'incrémentation suffixé :  
  
```  
i++;  
```  
  
 L'application de l'opérateur d'incrémentation suffixé (`++`) entraîne l'augmentation de la valeur de l'opérande d'une unité du type approprié. De même, l’effet de l’application de l’opérateur de décrémentation suffixé (**--**) diminution de la valeur de l’opérande d’une unité du type approprié.  
  
 Il est important de noter qu’un suffixe incrémenter ou décrémenter expression prend la valeur de l’expression **antérieures à** application de l’opérateur respectif. L’opération d’incrémentation ou décrémentation **après** l’opérande est évalué. Ce problème survient uniquement lorsque l'opération d'incrémentation ou de décrémentation suffixée intervient dans le contexte d'une plus grande expression.  
  
 Lorsqu'un opérateur suffixé est appliqué à un argument de fonction, il n'est pas garanti que la valeur de cet argument sera incrémentée ou décrémentée avant d'être passée à la fonction.  Pour plus d'informations, reportez-vous à la section 1.9.17 de la norme C++.  
  
 Application de l’opérateur d’incrément postfix vers un pointeur vers un tableau d’objets de type **long** ajoute en fait quatre à la représentation interne du pointeur. Ce comportement provoque le pointeur, qui référençait auparavant le  *n* ième élément de tableau, pour faire référence à la (*n*+ 1) élément.  
  
 Les opérandes incrémentation et les opérateurs de décrémentation suffixés doivent être modifiables (pas **const**) valeurs l-value de type arithmétique ou pointeur. Le type du résultat est le même que celui de la *postfix-expression*, mais il n’est plus une l-value.  
  
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : l’opérande d’une incrémentation ou de décrémentation opérateur ne peut pas être de type `bool`.
  
 Le code suivant illustre l'opérateur d'incrémentation suffixé :  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 Les opérations d'incrémentation et de décrémentation suffixées sur les types énumérés ne sont pas prises en charge :  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions suffixées](../cpp/postfix-expressions.md)   
 [Les opérateurs C++ intégrés, priorité et associativité](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Opérateurs suffixés d’incrémentation et de décrémentation C](../c-language/c-postfix-increment-and-decrement-operators.md)