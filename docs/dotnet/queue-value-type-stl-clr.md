---
title: "queue::value_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::value_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_type (membre) (STL/CLR)"
ms.assetid: f1abde03-982c-4aaf-91a6-cc613df9690e
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::value_type (STL/CLR)
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
// cliext_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Myqueue::value_type val = c1.front();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Configuration requise  
 **En\-tête :** \<cliext\/queue\>  
  
 **Espace de nommage:** cliext  
  
## Voir aussi  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::const\_reference](../dotnet/queue-const-reference-stl-clr.md)   
 [queue::reference](../dotnet/queue-reference-stl-clr.md)