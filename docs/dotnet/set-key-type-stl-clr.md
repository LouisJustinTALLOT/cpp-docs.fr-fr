---
title: Set::KEY_TYPE (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::key_type
dev_langs:
- C++
helpviewer_keywords:
- key_type member [STL/CLR]
ms.assetid: 2c057cf7-ac3d-40a6-b7fc-eb1c0a317381
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9df2304f83bde9217e116063672608bd982ca59f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163109"
---
# <a name="setkeytype-stlclr"></a>set::key_type (STL/CLR)
Type d'une clé de tri.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Key key_type;  
```  
  
## <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Key`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_set_key_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myset::key_type val = *it;   
  
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
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)   
 [set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)