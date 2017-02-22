---
title: "divides, struct | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::divides"
  - "std::divides"
  - "std.divides"
  - "divides"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "divides (struct)"
  - "divides (classe)"
ms.assetid: b9cf8e9c-6981-43a6-a6a3-8f761987dd7a
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# divides, struct
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objet de fonction prédéfinie qui exécute l'opération de division \( `operator/`\) à ses arguments.  
  
## Syntaxe  
  
```  
template<class Type = void>  
   struct divides : public binary_function <Type, Type, Type>   
   {  
      Type operator()(  
         const Type& Left,   
         const Type& Right   
         ) const;  
   };  
  
// specialized transparent functor for operator/  
template<>  
   struct divides<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            / std::forward<Type2>(Right));  
   };  
  
```  
  
#### Paramètres  
 `Type`, `Type1`, `Type2`  
 Un type qui prend en charge `operator/` qui prend des opérandes des types spécifiés ou déduits.  
  
 `Left`  
 L'opérande de gauche de l'opération de division.  Le modèle non spécialisé prend un argument de référence lvalue de type `Type`.  Le modèle spécialisé perfectionne le transfert des arguments de référence lvalue et rvalue de type déduit `Type1`.  
  
 `Right`  
 L'opérande de droite de l'opération de division.  Le modèle non spécialisé prend un argument de référence lvalue de type `Type`.  Le modèle spécialisé perfectionne le transfert des arguments de référence lvalue et rvalue de type déduit `Type2`.  
  
## Valeur de retour  
 Le résultat de `Left` \* `/` \+ `Right`.  Le modèle spécialisé effectue de façon parfaite le transfert du résultat, qui a le type retourné par `operator/`.  
  
## Exemple  
  
```  
// functional_divides.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 (6);  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 7.0 * i );  
   }  
  
   int j;  
   for ( j = 1 ; j <= 6 ; j++ )  
   {  
      v2.push_back( 2.0 * j);  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise quotients of the elements of v1 & v2  
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),   
      divides<double>( ) );  
  
   cout << "The element-wise quotients are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **Le vecteur v1 \= \(0 7 14 21 28 35\)**  
**Le vecteur v2 \= \( 2 4 6 8 10 12 \)**  
**Les quotients en ce qui concerne l'élément sont : \(0 1,75 2,33333 2,625 2,8 2,91667\)**   
## Configuration requise  
 **En\-tête :** \<functional\>  
  
 **Espace de noms :** std  
  
## Voir aussi  
 [Sécurité des threads dans la bibliothèque standard C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Bibliothèque STL \(Standard Template Library\)](../misc/standard-template-library.md)