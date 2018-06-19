---
title: Queue::push (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::push
dev_langs:
- C++
helpviewer_keywords:
- push member [STL/CLR]
ms.assetid: 97cf1f98-d4c4-417f-b57a-89cdd351ef65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf0456daa738d63fef55737715fe377266ddd368
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160574"
---
# <a name="queuepush-stlclr"></a>queue::push (STL/CLR)
Ajoute un nouvel élément en dernier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void push(value_type val);  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre ajoute un élément avec la valeur `val` à la fin de la file d’attente. Il permet d’ajouter un élément à la file d’attente.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)