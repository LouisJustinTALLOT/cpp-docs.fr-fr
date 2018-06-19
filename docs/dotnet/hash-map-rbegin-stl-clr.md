---
title: hash_map::rbegin (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: e3b6c4d5-9482-471e-b5fc-70331b082a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4bec2f5ac33fcbb0f68ae799443a92b0d69695ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108447"
---
# <a name="hashmaprbegin-stlclr"></a>hash_map::rbegin (STL/CLR)
Désigne le début de la séquence contrôlée inverse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_map_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_map::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::Begin (STL/CLR)](../dotnet/hash-map-begin-stl-clr.md)   
 [hash_map::end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)   
 [hash_map::rend (STL/CLR)](../dotnet/hash-map-rend-stl-clr.md)