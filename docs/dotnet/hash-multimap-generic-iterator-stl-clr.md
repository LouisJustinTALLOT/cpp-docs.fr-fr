---
title: hash_multimap::generic_iterator (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multimap::generic_iterator
dev_langs:
- C++
helpviewer_keywords:
- generic_iterator member [STL/CLR]
ms.assetid: 8f661962-a88f-4aec-a3eb-cf420be9313e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0a9d4855b191a1f6df9acc902b7823f899ec978f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110827"
---
# <a name="hashmultimapgenericiterator-stlclr"></a>hash_multimap::generic_iterator (STL/CLR)
Le type d’un itérateur pour une utilisation avec l’interface générique pour le conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
## <a name="remarks"></a>Notes  
 Le type décrit un itérateur générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_multimap_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multimap::generic_container^ gc1 = %c1;   
    for each (Myhash_multimap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multimap::generic_iterator gcit = gc1->begin();   
    Myhash_multimap::generic_value gcval = *gcit;   
    System::Console::Write(" [{0} {1}]", gcval->first, gcval->second);   
    System::Console::WriteLine();   
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
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)