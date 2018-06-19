---
title: hash_set::generic_reverse_iterator (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::generic_reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- generic_reverse_iterator member [STL/CLR]
ms.assetid: ffec7e08-07e4-49cf-b2f2-679c6a2a450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c1b29d97346d745c5e60db3e44d4730227838f0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126185"
---
# <a name="hashsetgenericreverseiterator-stlclr"></a>hash_set::generic_reverse_iterator (STL/CLR)
Le type d’un itérateur inverse pour une utilisation avec l’interface générique pour le conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
## <a name="remarks"></a>Notes  
 Le type décrit un itérateur inverse générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_set::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_set::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash_set::generic_iterator (STL/CLR)](../dotnet/hash-set-generic-iterator-stl-clr.md)