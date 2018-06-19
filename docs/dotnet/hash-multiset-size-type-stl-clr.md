---
title: hash_multiset::size_type (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::size_type
dev_langs:
- C++
helpviewer_keywords:
- size_type member [STL/CLR]
ms.assetid: cf4e2a5f-6d46-4ade-9bb4-407e12f310b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d117ac5d0a97e31ecd7304ace3eeaf561021d752
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126094"
---
# <a name="hashmultisetsizetype-stlclr"></a>hash_multiset::size_type (STL/CLR)
Le type d’une distance signée entre deux éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef int size_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type décrit un nombre non négatif élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_multiset_size_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::size_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)