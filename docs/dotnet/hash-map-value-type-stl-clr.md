---
title: hash_map::Value_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 7aa29304-5e52-46be-b50e-45e11401764e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4dec06bf1136e0736b1583e6ff5bff454aa512d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108908"
---
# <a name="hashmapvaluetype-stlclr"></a>hash_map::value_type (STL/CLR)
Type d’un élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme de `generic_value`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_map_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_map::value_type val = *it;   
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
 **En-tête :** \<cliext/hash_map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::const_reference (STL/CLR)](../dotnet/hash-map-const-reference-stl-clr.md)   
 [hash_map::KEY_TYPE (STL/CLR)](../dotnet/hash-map-key-type-stl-clr.md)   
 [hash_map::reference (STL/CLR)](../dotnet/hash-map-reference-stl-clr.md)