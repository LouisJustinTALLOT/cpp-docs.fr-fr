---
title: "map::const_reference (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::const_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reference (membre) (STL/CLR)"
ms.assetid: 0b343e23-7f8d-46d3-876f-f1ec86776110
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# map::const_reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Type d'une référence constante à un élément.  
  
## Syntaxe  
  
```  
typedef value_type% const_reference;  
```  
  
## Notes  
 Ce type décrit une référence constante à un élément.  
  
## Exemple  
  
```  
// cliext_map_const_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Mymap::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**   
## Configuration requise  
 **En\-tête:** \<cliext\/map\>  
  
 **Espace de noms:** cliext  
  
## Voir aussi  
 [map](../dotnet/map-stl-clr.md)   
 [map::reference](../dotnet/map-reference-stl-clr.md)   
 [map::value\_type](../dotnet/map-value-type-stl-clr.md)