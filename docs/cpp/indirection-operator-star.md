---
title: "Op&#233;rateur d&#39;indirection&#160;: * | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "* (opérateur)"
  - "opérateur d'indirection"
  - "opérateur d'indirection, syntaxe"
  - "opérateurs (C++), indirection"
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Op&#233;rateur d&#39;indirection&#160;: *
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Syntaxe  
  
```  
  
* cast-expression  
```  
  
## Notes  
 L'opérateur d'indirection unaire \(**\***\) déréférence un pointeur ; autrement dit, il convertit une valeur de pointeur en l\-value.  L'opérande de l'opérateur d'indirection doit être un pointeur vers un type.  Le résultat de l'expression d'indirection est le type à partir duquel le type pointeur est dérivé.  L'utilisation de l'opérateur **\*** dans ce contexte est différente de sa signification en tant qu'opérateur binaire, qui est la multiplication.  
  
 Si l'opérande pointe vers une fonction, le résultat est un désignateur de fonction.  S'il pointe vers un emplacement de stockage, le résultat est une l\-value désignant l'emplacement de stockage.  
  
 L'opérateur d'indirection peut être utilisé cumulativement pour déréférencer les pointeurs vers des pointeurs.  Par exemple :  
  
```  
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
  
 Si la valeur du pointeur n'est pas valide, le résultat n'est pas défini.  La liste ci\-dessous inclut certaines des conditions les plus courantes qui invalident une valeur de pointeur.  
  
-   Le pointeur est un pointeur null.  
  
-   Le pointeur spécifie l'adresse d'un élément local qui n'est pas visible au moment de la référence.  
  
-   Le pointeur spécifie une adresse alignée de façon inappropriée pour le type de l'objet désigné.  
  
-   Le pointeur spécifie une adresse non utilisée par le programme en cours d'exécution.  
  
## Voir aussi  
 [Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)   
 [Opérateurs C\+\+](../misc/cpp-operators.md)   
 [Opérateurs, priorité et associativité C\+\+](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Opérateur address\-of : &](../cpp/address-of-operator-amp.md)   
 [Indirection et opérateurs d'adresse](../c-language/indirection-and-address-of-operators.md)