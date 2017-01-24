---
title: "hash_multimap::value_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membre value_comp [STL/CLR]"
ms.assetid: ec6108b8-a529-499b-bc7f-dce41f5b6175
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copies the ordering delegate for two element values.  
  
## Syntaxe  
  
```  
value_compare^ value_comp();  
```  
  
## Notes  
 The member function returns the ordering delegate used to order the controlled sequence.  You use it to compare two element values.  
  
## Exemple  
  
```  
// cliext_hash_multimap_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    Myhash_multimap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Myhash_multimap::make_value(L'a', 1),   
            Myhash_multimap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Myhash_multimap::make_value(L'a', 1),   
            Myhash_multimap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Myhash_multimap::make_value(L'b', 2),   
            Myhash_multimap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **compare\(\[L'a', 1\], \[L'a', 1\]\) \= True**  
**compare\(\[L'a', 1\], \[L'b', 2\]\) \= True**  
**compare\(\[L'b', 2\], \[L'a', 1\]\) \= False**   
## Configuration requise  
 **Header:** \<cliext\/hash\_map\>  
  
 **Namespace:** cliext  
  
## Voir aussi  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::value\_compare](../dotnet/hash-multimap-value-compare-stl-clr.md)   
 [hash\_multimap::value\_type](../dotnet/hash-multimap-value-type-stl-clr.md)