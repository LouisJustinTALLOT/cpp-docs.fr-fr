---
title: "hash_map::upper_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_map::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membre upper_bound [STL/CLR]"
ms.assetid: f83e88b4-e15e-49d5-90e4-cf7360c27c30
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_map::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recherche la fin de la plage qui correspond à une clé spécifiée.  
  
## Syntaxe  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### Paramètres  
 key  
 Valeur de clé à rechercher.  
  
## Notes  
 La méthode détermine le dernier élément `X` de la séquence contrôlée qui est haché dans le même compartiment que `key` et qui a un classement équivalent à `key`.  Si aucun élément de ce type n'existe, ou si `X` est le dernier élément de la séquence contrôlée, cela retourne [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)`()`; sinon cela renvoie un itérateur qui indique le premier élément au delà de `X`.  Vous l'utilisez pour rechercher la fin d'une séquence d'éléments figurant actuellement dans la séquence contrôlée qui correspond à la clé spécifiée.  
  
## Exemple  
  
```  
// cliext_hash_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Myhash_map::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**upper\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*upper\_bound\(L'a'\) \= \[b 2\]**  
**\*upper\_bound\(L'b'\) \= \[c 3\]**   
## Configuration requise  
 **En\-tête :** \<cliext\/hash\_map\>  
  
 **Espace de noms** cliext  
  
## Voir aussi  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::count](../dotnet/hash-map-count-stl-clr.md)   
 [hash\_map::equal\_range](../dotnet/hash-map-equal-range-stl-clr.md)   
 [hash\_map::find](../dotnet/hash-map-find-stl-clr.md)   
 [hash\_map::lower\_bound](../dotnet/hash-map-lower-bound-stl-clr.md)