---
title: "priority_queue::value_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::value_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_type (membre) (STL/CLR)"
ms.assetid: 0d81ef75-8bd1-44f5-8753-4b42a505d8c3
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::value_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Le type d'un élément.  
  
## Syntaxe  
  
```  
typedef Value value_type;  
```  
  
## Notes  
 Le type est un synonyme du paramètre de modèle `Value`.  
  
## Exemple  
  
```  
// cliext_priority_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mypriority_queue::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b a**   
## Configuration requise  
 **En\-tête :** \<cliext\/queue\>  
  
 **Espace de noms :** cliext  
  
## Voir aussi  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::const\_reference](../dotnet/priority-queue-const-reference-stl-clr.md)   
 [priority\_queue::reference](../dotnet/priority-queue-reference-stl-clr.md)