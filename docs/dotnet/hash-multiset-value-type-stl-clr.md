---
title: hash_multiset::Value_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 8f9cd362-28e7-4916-af4e-c37e780e097c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 776a672eb522fd2139a56a69255fa201e48b01dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126380"
---
# <a name="hashmultisetvaluetype-stlclr"></a>hash_multiset::value_type (STL/CLR)
Type d’un élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme de `generic_value`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_multiset_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_multiset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::const_reference (STL/CLR)](../dotnet/hash-multiset-const-reference-stl-clr.md)   
 [hash_multiset::KEY_TYPE (STL/CLR)](../dotnet/hash-multiset-key-type-stl-clr.md)   
 [hash_multiset::reference (STL/CLR)](../dotnet/hash-multiset-reference-stl-clr.md)