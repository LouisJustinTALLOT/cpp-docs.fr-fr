---
title: multimap::operator = (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: 9bef7dc5-591d-443b-88b1-e68286422fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 54d4a0fa182536f46d230443b25ba94afa20ba80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137021"
---
# <a name="multimapoperator-stlclr"></a>multimap::operator= (STL/CLR)
Remplace la séquence contrôlée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
multimap<Key, Mapped>% operator=(multimap<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Conteneur à copier.  
  
## <a name="remarks"></a>Notes  
 Les copies d’opérateur de membre `right` à l’objet, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans `right`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_multimap_operator_as.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultimap c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)