---
title: "is_nothrow_assignable (classe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_assignable"
  - "std.is_nothrow_assignable"
  - "std::is_nothrow_assignable"
  - "type_traits/std::is_nothrow_assignable"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_nothrow_assignable"
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_assignable (classe)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Teste si une valeur de `From` type peut être affecté à `To` type et l’assignation ne connaît ne pas lever.  
  
## Syntaxe  
  
```  
template <class To, class From>   
    struct is_nothrow_assignable;  
```  
  
#### Paramètres  
 Pour  
 Type de l'objet qui reçoit l'assignation.  
  
 From  
 Type de l'objet qui fournit la valeur.  
  
## Notes  
 L’expression `declval<To>() = declval<From>()` doit être correctement construit et doit être connu du compilateur ne pas lever. Les deux `From` et `To` doivent être des types complets, `void`, ou les tableaux de la limite est inconnue.  
  
## Configuration requise  
 **En\-tête :** \<type\_traits\>  
  
 **Espace de noms :** std  
  
## Voir aussi  
 [\<type\_traits\>](../standard-library/type-traits.md)