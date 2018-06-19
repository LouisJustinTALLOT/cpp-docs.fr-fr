---
title: priority_queue::top_item (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::top_item
dev_langs:
- C++
helpviewer_keywords:
- top_item member [STL/CLR]
ms.assetid: d497403b-6b1d-4c6e-a0f4-c744cc5fad75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3a36bff75f0c1140157078d7e747dd576dbd684a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162115"
---
# <a name="priorityqueuetopitem-stlclr"></a>priority_queue::top_item (STL/CLR)
Accède à l’élément de priorité la plus élevée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
property value_type back_item;  
```  
  
## <a name="remarks"></a>Notes  
 La propriété accède à l’élément du haut (priorité la plus élevée) de la séquence contrôlée, qui doit être vide. Vous l’utilisez pour lire ou écrire l’élément de la priorité la plus élevée, lorsque vous savez qu’il existe.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_priority_queue_top_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
top_item = c  
 x a b  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::top (STL/CLR)](../dotnet/priority-queue-top-stl-clr.md)