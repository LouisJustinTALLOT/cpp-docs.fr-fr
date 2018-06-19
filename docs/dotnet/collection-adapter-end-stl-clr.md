---
title: collection_adapter::end (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter::end
dev_langs:
- C++
helpviewer_keywords:
- end member [STL/CLR]
ms.assetid: f953a734-2f17-4b68-9ca4-34f980d08887
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 246d51212cd8e88bf89e277aee169c41b04956b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104189"
---
# <a name="collectionadapterend-stlclr"></a>collection_adapter::end (STL/CLR)
Désigne la fin de la séquence contrôlée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator end();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur d’entrée qui pointe juste après la fin de la séquence contrôlée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_collection_adapter_end.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/carte >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::begin (STL/CLR)](../dotnet/collection-adapter-begin-stl-clr.md)