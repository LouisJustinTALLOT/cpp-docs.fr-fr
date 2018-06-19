---
title: Map::Value_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 9f02ac42-c1e0-4671-bed3-72d6c06a1e66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a87302d57b26f2e498974d16271bb3257dcf4031
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138603"
---
# <a name="mapvaluetype-stlclr"></a>map::value_type (STL/CLR)
Type d’un élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme de `generic_value`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_map_value_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymap::value_type val = *it;   
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
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)   
 [Map::KEY_TYPE (STL/CLR)](../dotnet/map-key-type-stl-clr.md)   
 [map::reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)