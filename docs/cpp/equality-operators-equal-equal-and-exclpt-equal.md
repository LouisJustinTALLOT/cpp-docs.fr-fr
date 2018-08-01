---
title: 'Opérateurs d’égalité : == et ! = | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 073e642b99dea4eb6f77fd1e79731713748f1f61
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403113"
---
# <a name="equality-operators--and-"></a>Opérateurs d'égalité : == et !=
## <a name="syntax"></a>Syntaxe  
  
```  
expression == expression  
expression != expression  
```  
  
## <a name="remarks"></a>Notes  
 Les opérateurs d’égalité binaires comparent l’égalité ou l’inégalité stricte de leurs opérandes.  
  
 Les opérateurs d'égalité, égal à (`==`) et différent de (`!=`), ont une priorité inférieure aux opérateurs relationnels, mais ils se comportent de la même manière. Le type de résultat de ces opérateurs est **bool**.  
  
 L’opérateur égal à (`==`) renvoie **true** (1) si les deux opérandes ont la même valeur ; sinon, elle retourne **false** (0). L’opérateur non-égal à (`!=`) renvoie **true** si les opérandes n’ont pas la même valeur ; sinon, elle retourne **false**.  
  
## <a name="operator-keyword-for-"></a>Mot clé d'opérateur pour !=  
 L'opérateur `not_eq` est l'équivalent textuel de `!=`. Il existe deux façons d’accéder à la `not_eq` opérateur dans vos programmes : inclure le fichier d’en-tête `iso646.h`, ou compiler avec la [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).  
  
## <a name="example"></a>Exemple  
  
```cpp 
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 Les opérateurs d'égalité permettent de comparer les pointeurs à des membres du même type. Dans ce type de comparaison, les conversions de pointeur vers membre sont effectuées. Les conversions de pointeur vers membre peuvent également être comparées à une expression constante qui a pour valeur 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)   
 [Opérateurs C++ intégrés, priorité et associativité](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Opérateurs relationnels et d’égalité C](../c-language/c-relational-and-equality-operators.md)