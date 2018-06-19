---
title: collection_adapter::KEY_TYPE (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter::key_type
dev_langs:
- C++
helpviewer_keywords:
- key_type member [STL/CLR]
ms.assetid: 71ed32b0-af5b-4bac-ae09-2f5d08f0a79b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a5f5e06b94c2dd81e84f9c02fc91da1d7aab2caf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106282"
---
# <a name="collectionadapterkeytype-stlclr"></a>collection_adapter::key_type (STL/CLR)
Le type d’une clé de dictionnaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Key key_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Key`, dans une spécialisation pour `IDictionary` ou `IDictionary<Value>`; sinon, il n’est pas défini.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_collection_adapter_key_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/carte >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::mapped_type (STL/CLR)](../dotnet/collection-adapter-mapped-type-stl-clr.md)