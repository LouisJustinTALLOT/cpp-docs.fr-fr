---
title: "map::equal_range (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membre equal_range [STL/CLR]"
ms.assetid: c0d7409c-344d-4102-99c4-aeab8643a073
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recherche la plage qui correspond à une clé spécifiée.  
  
## Syntaxe  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### Paramètres  
 key  
 Valeur clé à rechercher  
  
## Notes  
 La fonction membre retourne une paire d'itérateurs `cliext::pair<iterator, iterator>(` [map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)`(``key``),` [map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)`(``key``))`.  Vous l'utilisez pour déterminer la plage d'éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.  
  
## Exemple  
  
```  
// cliext_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_iter Pairii;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**equal\_range \(L'x'\) vide \= True**  
 **\[b 2\]**   
## Configuration requise  
 **En\-tête:** \<cliext\/map\>  
  
 **Espace de noms :** cliext  
  
## Voir aussi  
 [map](../dotnet/map-stl-clr.md)   
 [map::count](../dotnet/map-count-stl-clr.md)   
 [map::find](../dotnet/map-find-stl-clr.md)   
 [map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)   
 [map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)