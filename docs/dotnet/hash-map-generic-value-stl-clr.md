---
title: hash_map::generic_value (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::generic_value
dev_langs:
- C++
helpviewer_keywords:
- generic_value member [STL/CLR]
ms.assetid: e370feb3-3d2d-493e-b29d-4e97756c33b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 961b11636984806360d670285d8103f4b4777ee9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107924"
---
# <a name="hashmapgenericvalue-stlclr"></a>hash_map::generic_value (STL/CLR)
Le type d’un élément pour une utilisation avec l’interface générique pour le conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef GValue generic_value;  
```  
  
## <a name="remarks"></a>Notes  
 Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké pour une utilisation avec l’interface générique pour cette classe de conteneur de modèle.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_map_generic_value.cpp   
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
  
// construct a generic container   
    Myhash_map::generic_container^ gc1 = %c1;   
    for each (Myhash_map::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_map::generic_iterator gcit = gc1->begin();   
    Myhash_map::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::generic_container (STL/CLR)](../dotnet/hash-map-generic-container-stl-clr.md)   
 [hash_map::generic_iterator (STL/CLR)](../dotnet/hash-map-generic-iterator-stl-clr.md)   
 [hash_map::generic_reverse_iterator (STL/CLR)](../dotnet/hash-map-generic-reverse-iterator-stl-clr.md)