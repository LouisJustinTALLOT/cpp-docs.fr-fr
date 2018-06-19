---
title: Queue::container_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::container_type
dev_langs:
- C++
helpviewer_keywords:
- container_type member [STL/CLR]
ms.assetid: 118168f9-e5ed-47e2-a4f5-26b0b56e41e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8513c6673473d47e1a2e237f1baa5f5471826c0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159702"
---
# <a name="queuecontainertype-stlclr"></a>queue::container_type (STL/CLR)
Type du conteneur sous-jacent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Container value_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Container`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Myqueue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
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
 [queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)