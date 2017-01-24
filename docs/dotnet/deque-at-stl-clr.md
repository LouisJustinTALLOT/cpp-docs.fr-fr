---
title: "deque::at (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::at"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "member at [STL/CLR]"
ms.assetid: 9af83d8a-c519-4b2a-a25f-d3dc8bbb87fb
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::at (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Accède à un élément à une position spécifiée.  
  
## Syntaxe  
  
```  
reference at(size_type pos);  
```  
  
#### Paramètres  
 position  
 Position de l'élément auquel accéder.  
  
## Notes  
 La fonction membre retourne une référence à l'élément de la séquence contrôlée à la position `pos`.  Vous l'utilisez pour lire ou écrire un élément dont vous connaissez la position.  
  
## Exemple  
  
```  
// cliext_deque_at.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a x c**   
## Configuration requise  
 **Header:** \<cliext\/deque\>  
  
 **Espace pour le nom :** cliext  
  
## Voir aussi  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::operator](../dotnet/deque-operator-stl-clr.md)