---
title: hash_set::key_compare (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::key_compare
dev_langs:
- C++
helpviewer_keywords:
- key_compare member [STL/CLR]
ms.assetid: 93a94dde-3296-4e34-b461-3e2a20801041
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 16bc1ed13ecbe06693dbd92763fecfb7ee97bff8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33139972"
---
# <a name="hashsetkeycompare-stlclr"></a>hash_set::key_compare (STL/CLR)
Délégué de classement pour les deux clés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme pour le délégué qui détermine l’ordre de ses arguments de clé.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_key_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_set c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)   
 [hash_set::KEY_TYPE (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)   
 [hash_set::value_compare (STL/CLR)](../dotnet/hash-set-value-compare-stl-clr.md)