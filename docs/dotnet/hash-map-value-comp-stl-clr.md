---
title: "hash_map::value_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_map::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membre value_comp [STL/CLR]"
ms.assetid: b11a2dee-07e8-450c-8f85-979c0a15ae64
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# hash_map::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copie le classement délégué pour deux valeurs d'éléments.  
  
## Syntaxe  
  
```  
value_compare^ value_comp();  
```  
  
## Notes  
 La méthode retourne le délégué de tri utilisé pour trier la séquence contrôlée.  Vous l'utilisez pour comparer les valeurs de deux éléments.  
  
## Exemple  
  
```  
// cliext_hash_map_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'b', 2),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **compare \(L'a', L'a'\) \= True**  
**compare\(\[L'a', 1\], \[L'b', 2\]\) \= Vrai**  
**compare\(\[L'b', 2\], \[L'a', 1\]\) \= Faux**   
## Configuration requise  
 **En\-tête :** \<cliext\/hash\_map\>  
  
 **Espace de noms** cliext  
  
## Voir aussi  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::value\_compare](../dotnet/hash-map-value-compare-stl-clr.md)   
 [hash\_map::value\_type](../dotnet/hash-map-value-type-stl-clr.md)