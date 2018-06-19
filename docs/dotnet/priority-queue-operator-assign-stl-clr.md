---
title: priority_queue::operator = (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: 796b4ad2-3e40-49e8-8462-87460d086fe4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 13fc58554617ef7e59c4483eadc2e82fbb02a22d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159442"
---
# <a name="priorityqueueoperator-stlclr"></a>priority_queue::operator= (STL/CLR)
Remplace la séquence contrôlée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Adaptateur de conteneur à copier.  
  
## <a name="remarks"></a>Notes  
 Les copies d’opérateur de membre `right` à l’objet, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans `right`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_priority_queue_operator_as.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mypriority_queue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)