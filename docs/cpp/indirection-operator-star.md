---
title: 'Opérateur d’indirection : * | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80fdbe14539c5b32c2da80a5de75fbe0a2b64241
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409124"
---
# <a name="indirection-operator-"></a>Opérateur d'indirection : *
## <a name="syntax"></a>Syntaxe  
  
```  
* cast-expression  
```  
  
## <a name="remarks"></a>Notes  
 L’opérateur d’indirection unaire (**\***) déréférence un pointeur ; autrement dit, elle convertit une valeur de pointeur à une l-value. L’opérande de l’opérateur d’indirection doit être un pointeur vers un type. Le résultat de l'expression d'indirection est le type à partir duquel le type pointeur est dérivé. L’utilisation de la **\*** opérateur dans ce contexte est différente de sa signification comme opérateur binaire, qui est la multiplication.  
  
 Si l'opérande pointe vers une fonction, le résultat est un désignateur de fonction. S'il pointe vers un emplacement de stockage, le résultat est une l-value désignant l'emplacement de stockage.  
  
 L'opérateur d'indirection peut être utilisé cumulativement pour déréférencer les pointeurs vers des pointeurs. Exemple :  
  
```cpp 
// expre_Indirection_Operator.cpp  
// compile with: /EHsc  
// Demonstrate indirection operator  
#include <iostream>  
using namespace std;  
int main() {  
   int n = 5;  
   int *pn = &n;  
   int **ppn = &pn;  
  
   cout  << "Value of n:\n"  
         << "direct value: " << n << endl  
         << "indirect value: " << *pn << endl  
         << "doubly indirect value: " << **ppn << endl  
         << "address of n: " << pn << endl  
         << "address of n via indirection: " << *ppn << endl;  
}  
```  
  
 Si la valeur du pointeur n'est pas valide, le résultat n'est pas défini. La liste ci-dessous inclut certaines des conditions les plus courantes qui invalident une valeur de pointeur.  
  
-   Le pointeur est un pointeur null.  
  
-   Le pointeur spécifie l'adresse d'un élément local qui n'est pas visible au moment de la référence.  
  
-   Le pointeur spécifie une adresse alignée de façon inappropriée pour le type de l'objet désigné.  
  
-   Le pointeur spécifie une adresse non utilisée par le programme en cours d'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)   
 [Opérateurs C++ intégrés, priorité et associativité](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Opérateur address-of : &](../cpp/address-of-operator-amp.md)   
 [Opérateurs d’indirection et d’adresse](../c-language/indirection-and-address-of-operators.md)