---
title: "iterator_traits, struct | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::iterator_traits"
  - "xutility/std::iterator_traits"
  - "iterator_traits"
  - "std.iterator_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator_traits (classe)"
  - "iterator_traits (struct)"
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# iterator_traits, struct
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Une structure d'assistance de modèle utilisé pour spécifier toutes les définitions de type critiques qu'un itérateur doit être.  
  
## Syntaxe  
  
```  
template<class Iterator>  
    struct iterator_traits {  
        typedef typename Iterator::iterator_category iterator_category;  
        typedef typename Iterator::value_type value_type;  
        typedef typename Iterator::difference_type difference_type;  
        typedef difference_type distance_type;  
        typedef typename Iterator::pointer pointer;  
        typedef typename Iterator::reference reference;  
    };  
template<class Type>  
    struct iterator_traits<Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef Type *pointer;  
        typedef Type& reference;  
    };  
template<class Type>  
    struct iterator_traits<const Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef const Type *pointer;  
        typedef const Type& reference;  
    };  
```  
  
## Notes  
 La structure de modèle définit les types de membres  
  
-   **iterator\_category**: un synonyme pour **Iterator::iterator\_category**.  
  
-   `value_type`: un synonyme pour **Iterator::value\_type**.  
  
-   `difference_type`: un synonyme pour **Iterator::difference\_type**.  
  
-   `distance_type`: un synonyme pour **Iterator::difference\_type.**  
  
-   **pointer**: un synonyme pour **Iterator::pointer**.  
  
-   **référence**: un synonyme pour **Iterator::reference**.  
  
 Les spécialisations partielles déterminent les types critiques associés à un pointeur de type **Type \*** ou **Type \***const.  
  
 Dans cette implémentation vous pouvez également utiliser plusieurs fonctions de modèle qui n'utilisent pas de la spécialisation partielle :  
  
```  
template<class Category, class Type, class Diff>  
C _Iter_cat(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    random_access_iterator_tag _Iter_cat(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Ty *_Val_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    Ty *_Val_type(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    ptrdiff_t *_Dist_type(const Ty *);  
```  
  
 ce qui déterminent de nombreuses types ou plus.  Vous pouvez utiliser ces fonctions comme arguments dans un appel de fonction.  Le seul objectif est de fournir un paramètre de classe de modèle utile à la fonction appelée.  
  
## Exemple  
  
```  
// iterator_traits.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <vector>  
#include <list>  
  
using namespace std;  
  
template< class it >  
void  
function( it i1, it i2 )  
{  
   iterator_traits<it>::iterator_category cat;  
   cout << typeid( cat ).name( ) << endl;  
   while ( i1 != i2 )  
   {  
      iterator_traits<it>::value_type x;  
      x = *i1;  
      cout << x << " ";  
      i1++;  
   };     
   cout << endl;  
};  
  
int main( )   
{  
   vector<char> vc( 10,'a' );  
   list<int> li( 10 );  
   function( vc.begin( ), vc.end( ) );  
   function( li.begin( ), li.end( ) );  
}  
```  
  
  **std::random\_access\_iterator\_tag de structure**  
**un**   
**std::bidirectional\_iterator\_tag de structure**  
**0 0 0 0 0 0 0 0 0 0**    
## Configuration requise  
 **En\-tête :** \<iterator\>  
  
 **Espace de noms :** std  
  
## Voir aussi  
 [\<iterator\>](../standard-library/iterator.md)   
 [Sécurité des threads dans la bibliothèque standard C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Bibliothèque STL \(Standard Template Library\)](../misc/standard-template-library.md)