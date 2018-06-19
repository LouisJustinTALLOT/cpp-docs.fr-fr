---
title: Map::Clear (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::clear
dev_langs:
- C++
helpviewer_keywords:
- clear member [STL/CLR]
ms.assetid: 2a6a01fe-2998-447d-9ae8-6cb6343d0dfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e8f453e777bb1320fd88aeee68882f96d41d2fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132136"
---
# <a name="mapclear-stlclr"></a>map::clear (STL/CLR)
Supprime tous les éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre appelle [map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md) `(` [map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md) `(),` [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md) `())`. Il permet de vous assurer que la séquence contrôlée est vide.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_map_clear.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2]  
size() = 0  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)