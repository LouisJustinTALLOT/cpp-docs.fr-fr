---
title: Map::Empty (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::empty
dev_langs:
- C++
helpviewer_keywords:
- empty member [STL/CLR]
ms.assetid: ce41d37a-2896-48df-87ea-d3f3b3e5ab45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4f24130dfff1a3d2236a9e0273560dd44b425993
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132581"
---
# <a name="mapempty-stlclr"></a>map::empty (STL/CLR)
Vérifie l'absence d'éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool empty();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle est équivalente à [map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)`() == 0`. Il permet de vérifier si la carte est vide.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_map_empty.cpp   
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
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)