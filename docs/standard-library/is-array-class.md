---
title: "is_array, classe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_array"
  - "std.tr1.is_array"
  - "std::tr1::is_array"
  - "std.is_array"
  - "std::is_array"
  - "type_traits/std::is_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_array (classe) (TR1)"
  - "is_array"
ms.assetid: 61fb2201-8de3-4746-9721-617f02df170f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_array, classe
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Teste si le type est un tableau.  
  
## Syntaxe  
  
```  
template<class Ty>  
    struct is_array;  
```  
  
#### Paramètres  
 `Ty`  
 Type à interroger.  
  
## Notes  
 Une instance du prédicat de type a la valeur true si le type `Ty` est un type tableau. Sinon, sa valeur est false.  
  
## Exemple  
  
```  
// std_tr1__type_traits__is_array.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_array<trivial> == " << std::boolalpha   
        << std::is_array<trivial>::value << std::endl;   
    std::cout << "is_array<int> == " << std::boolalpha   
        << std::is_array<int>::value << std::endl;   
    std::cout << "is_array<int[5]> == " << std::boolalpha   
        << std::is_array<int[5]>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_array\<trivial\> \=\= false**  
**is\_array\<int\> \=\= false**  
**is\_array\<int\[5\]\> \=\= true**   
## Configuration requise  
 **En\-tête :** \<type\_traits\>  
  
 **Espace de noms :** std  
  
## Voir aussi  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [extent, classe](../standard-library/extent-class.md)   
 [rank, classe](../standard-library/rank-class.md)