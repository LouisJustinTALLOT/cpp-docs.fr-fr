---
title: hash_set::rbegin (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: 1f2ff4ed-8557-40cf-8e61-816563acc43e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 062d6a62ca810a37aff2a7fd447526de7bd16487
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127391"
---
# <a name="hashsetrbegin-stlclr"></a>hash_set::rbegin (STL/CLR)
Désigne le début de la séquence contrôlée inverse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_set::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::Begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md)   
 [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)   
 [hash_set::rend (STL/CLR)](../dotnet/hash-set-rend-stl-clr.md)