---
title: multimap::Value_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: c10d75f9-2efe-41f7-babc-655c68c14a4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 616ab63b4cdb42acd4ed9e93002f12af38a37b44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135129"
---
# <a name="multimapvaluetype-stlclr"></a>multimap::value_type (STL/CLR)
Type d’un élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme de `generic_value`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_multimap_value_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymultimap::value_type val = *it;   
        System::Console::Write(" [{0} {1}]", val->first, val->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)   
 [multimap::KEY_TYPE (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)   
 [multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)