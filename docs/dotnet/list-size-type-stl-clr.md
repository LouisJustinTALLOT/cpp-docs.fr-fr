---
title: List::size_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::size_type
dev_langs:
- C++
helpviewer_keywords:
- size_type member [STL/CLR]
ms.assetid: bfdf869f-fd7e-47b4-9ce9-68f7146dc3ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 17bc3c83220b64d94af14c85c24610218e563318
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131463"
---
# <a name="listsizetype-stlclr"></a>list::size_type (STL/CLR)
Le type d’une distance signée entre deux éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef int size_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type décrit un nombre non négatif élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_size_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::size_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)