---
title: Map::swap (STL/CLR) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::swap
dev_langs: C++
helpviewer_keywords: swap member [STL/CLR]
ms.assetid: b36ed982-21ce-40e5-9636-ecdbaf1b7eec
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f82ac0547b58d3e85afdf8fe1c951ed8cec1f742
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="mapswap-stlclr"></a>map::swap (STL/CLR)
Échange le contenu de deux conteneurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droit  
 Conteneur avec lequel échanger le contenu.  
  
## <a name="remarks"></a>Notes  
 La fonction membre échange les séquences contrôlées entre `this` et `right`. Cela se fait en temps constant et ne lève aucune exception. Vous l’utiliser comme un moyen rapide de l’échange le contenu de deux conteneurs.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_map_swap.cpp   
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
  
// construct another container with repetition of values   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'd', 4));   
    c2.insert(Mymap::make_value(L'e', 5));   
    c2.insert(Mymap::make_value(L'f', 6));   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[d 4] [e 5] [f 6]  
[d 4] [e 5] [f 6]  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)