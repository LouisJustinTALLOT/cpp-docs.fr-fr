---
title: hash_set::to_array (STL/CLR) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_set::to_array
dev_langs:
- C++
helpviewer_keywords:
- to_array member [STL/CLR]
ms.assetid: 2aa61f13-85b8-4aa4-91b4-69ddcc5064dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03b7087d448a158ddd65b514c5ade0ce810a3c53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="hashsettoarray-stlclr"></a>hash_set::to_array (STL/CLR)
Copie de la séquence contrôlée vers un nouveau tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne un tableau contenant la séquence contrôlée. Il permet d’obtenir une copie de la séquence contrôlée sous forme de tableau.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)