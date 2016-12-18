---
title: "Op&#233;rateurs d&#39;&#233;galit&#233;&#160;: == et != | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "not_eq"
  - "!="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= (opérateur)"
  - "== (opérateur)"
  - "opérateur d'égalité"
  - "opérateur d'égalité"
  - "opérateur d'égalité, syntaxe"
  - "différent de (opérateur de comparaison)"
  - "not_eq (opérateur)"
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Op&#233;rateurs d&#39;&#233;galit&#233;&#160;: == et !=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Syntaxe  
  
```  
  
      expression == expression  
expression != expression  
```  
  
## Notes  
 Les opérateurs d'égalité binaires comparent l'égalité ou l'inégalité stricte de leurs opérandes.  
  
 Les opérateurs d'égalité, égal à \(`==`\) et différent de \(`!=`\), ont une priorité inférieure aux opérateurs relationnels, mais ils se comportent de la même manière.  Le type de résultat pour ces opérateurs est `bool`.  
  
 L'opérateur égal à \(`==`\) retourne la valeur **true** \(1\) si les deux opérandes ont la même valeur, sinon il retourne la valeur **false** \(0\).  L'opérateur différent de \(`!=`\) retourne la valeur **true** si les opérandes n'ont pas la même valeur, sinon il retourne la valeur **false**.  
  
## Mot clé d'opérateur pour \!\=  
 L'opérateur `not_eq` est l'équivalent textuel de `!=`.  Il existe deux moyens d'accéder à l'opérateur `not_eq` dans vos programmes : incluez le fichier d'en\-tête `iso646.h` ou compilez avec l'option de compilateur [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(Désactivation des extensions de langage\).  
  
## Exemple  
  
```  
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
  
 Les opérateurs d'égalité permettent de comparer les pointeurs à des membres du même type.  Dans ce type de comparaison, ce sont des conversions de pointeur vers membre, comme indiqué dans [Conversions de pointeur vers membre](../misc/pointer-to-member-conversions.md), qui sont exécutées.  Les conversions de pointeur vers membre peuvent également être comparées à une expression constante qui a pour valeur 0.  
  
## Voir aussi  
 [Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)   
 [Opérateurs C\+\+](../misc/cpp-operators.md)   
 [Opérateurs, priorité et associativité C\+\+](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Opérateurs relationnels et d'égalité C](../c-language/c-relational-and-equality-operators.md)