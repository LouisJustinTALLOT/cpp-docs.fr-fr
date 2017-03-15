---
title: "set::value_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membre value_comp [STL/CLR]"
ms.assetid: 3b7e469d-ca73-415b-bd20-24968c51107c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# set::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copie le classement délégué pour deux valeurs d'éléments.  
  
## Syntaxe  
  
```  
value_compare^ value_comp();  
```  
  
## Notes  
 La fonction considérée retourne le délégué de classement utilisé pour ordonner la séquence contrôlée.  Vous l'utilisez pour comparer les valeurs de deux éléments.  
  
## Exemple  
  
```  
// cliext_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
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
  
  **compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= True**  
**compare\(L'b', L'a'\) \= False**   
## Configuration requise  
 **En\-tête :** \<cliext\/set\>  
  
 **Espace de nom :** cliext  
  
## Voir aussi  
 [set](../dotnet/set-stl-clr.md)   
 [set::value\_compare](../dotnet/set-value-compare-stl-clr.md)   
 [set::value\_type](../dotnet/set-value-type-stl-clr.md)