---
title: "collection_adapter::key_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::collection_adapter::key_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_type (membre) (STL/CLR)"
ms.assetid: 71ed32b0-af5b-4bac-ae09-2f5d08f0a79b
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# collection_adapter::key_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Le type de clé de dictionnaire.  
  
## Syntaxe  
  
```  
typedef Key key_type;  
```  
  
## Notes  
 Le type est un synonyme pour le paramètre `Key`de modèles, dans une spécialisation pour `IDictionary` ou `IDictionary<Value>`; sinon il n'est pas définie.  
  
## Exemple  
  
```  
// cliext_collection_adapter_key_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**   
## Configuration requise  
 **En\-tête :** \<cliext\/adapter\>  
  
 **Espace de noms** cliext  
  
## Voir aussi  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [collection\_adapter::mapped\_type](../dotnet/collection-adapter-mapped-type-stl-clr.md)