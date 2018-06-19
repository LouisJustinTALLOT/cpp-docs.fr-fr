---
title: hash_multiset::hasher (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::hasher
dev_langs:
- C++
helpviewer_keywords:
- hasher member [STL/CLR]
ms.assetid: c68c59ae-bc9e-4caf-9240-04eb65273517
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fb5e62e020e01fd8355c5c4128e20c0e56a00283
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126341"
---
# <a name="hashmultisethasher-stlclr"></a>hash_multiset::hasher (STL/CLR)
Délégué d’une clé de hachage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>  
    hasher;  
```  
  
## <a name="remarks"></a>Notes  
 Le type décrit un délégué qui convertit une valeur de clé en entier.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_multiset_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::hash_delegate (STL/CLR)](../dotnet/hash-multiset-hash-delegate-stl-clr.md)