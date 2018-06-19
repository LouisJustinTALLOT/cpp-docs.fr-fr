---
title: Queue::front_item (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::front_item
dev_langs:
- C++
helpviewer_keywords:
- front_item member [STL/CLR]
ms.assetid: 389ab030-4351-48e6-9b03-417f1d3fcb86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d1c91b72c9109a8b6b3ee54231cf3d2d2713f0ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161260"
---
# <a name="queuefrontitem-stlclr"></a>queue::front_item (STL/CLR)
Accède au premier élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
property value_type front_item;  
```  
  
## <a name="remarks"></a>Notes  
 La propriété accède au premier élément de la séquence contrôlée, qui doit être vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_queue_front_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter last item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::Back (STL/CLR)](../dotnet/queue-back-stl-clr.md)   
 [Queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)   
 [Queue::Front (STL/CLR)](../dotnet/queue-front-stl-clr.md)   
 [queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)