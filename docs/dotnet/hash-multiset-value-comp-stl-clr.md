---
title: "hash_multiset::value_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membre value_comp [STL/CLR]"
ms.assetid: c5b25ded-9b27-43d5-9821-3f6e17338919
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copie le délégué de classement pour deux valeurs d'éléments.  
  
## Syntaxe  
  
```  
value_compare^ value_comp();  
```  
  
## Notes  
 La fonction considérée retourne le délégué de classement utilisé pour ordonner la séquence contrôlée.  Vous l'utilisez pour comparer les valeurs de deux éléments.  
  
## Exemple  
  
```  
// cliext_hash_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **compare \(L'a', L'a'\) \= True**  
**compare\(L'a', L'b'\) \= Vrai**  
**compare\(L'b', L'a'\) \= Faux**   
## Configuration requise  
 **En\-tête :** \<cliext\/hash\_set\>  
  
 **Espace de noms :** cliext  
  
## Voir aussi  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::value\_compare](../dotnet/hash-multiset-value-compare-stl-clr.md)   
 [hash\_multiset::value\_type](../dotnet/hash-multiset-value-type-stl-clr.md)