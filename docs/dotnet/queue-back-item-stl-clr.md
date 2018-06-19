---
title: Queue::back_item (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::back_item
dev_langs:
- C++
helpviewer_keywords:
- back_item member [STL/CLR]
ms.assetid: 721e44e1-eb46-41bf-8b3c-0fcbc02fb155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 18e64eca64264d130bbb004fd770070c8f50f033
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162260"
---
# <a name="queuebackitem-stlclr"></a>queue::back_item (STL/CLR)
Accède au dernier élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
property value_type back_item;  
```  
  
## <a name="remarks"></a>Notes  
 La propriété accède le dernier élément de la séquence contrôlée, qui doit être vide. Vous l’utilisez pour lire ou écrire le dernier élément, lorsque vous savez qu’il existe.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_queue_back_item.cpp   
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
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::Back (STL/CLR)](../dotnet/queue-back-stl-clr.md)   
 [Queue::Front (STL/CLR)](../dotnet/queue-front-stl-clr.md)   
 [queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)