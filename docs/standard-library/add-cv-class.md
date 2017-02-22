---
title: "add_cv, classe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.add_cv"
  - "add_cv"
  - "std::tr1::add_cv"
  - "std.add_cv"
  - "std::add_cv"
  - "type_traits/std::add_cv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_cv (classe) (TR1)"
  - "add_cv"
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# add_cv, classe
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Rend un type volatile ou const.  
  
## Syntaxe  
  
```  
template<class Ty>  
    struct add_cv;  
  
template<class T>  
using add_cv_t = typename add_cv<T>::type;  
```  
  
#### Paramètres  
 `Ty`  
 Type à modifier.  
  
## Notes  
 Une instance du modificateur de type contient le type modifié [add\_volatile, classe](../standard-library/add-volatile-class.md)`<` [add\_const, classe](../standard-library/add-const-class.md)`<Ty> >`.  
  
## Exemple  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_cv_t<int> *p = (const volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_cv<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_cv\_t\<int\> \=\= int**   
## Configuration requise  
 **En\-tête :** \<type\_traits\>  
  
 **Espace de noms :** std  
  
## Voir aussi  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_const, classe](../standard-library/remove-const-class.md)   
 [remove\_volatile, classe](../standard-library/remove-volatile-class.md)