---
title: pair::swap (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::swap
dev_langs:
- C++
helpviewer_keywords:
- swap member [STL/CLR]
ms.assetid: 7f5cbfa0-3702-40ab-a3f4-ffde02126095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 537cbbfcc3c2ad92dd023d3733e6420a2af9e32a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159455"
---
# <a name="pairswap-stlclr"></a>pair::swap (STL/CLR)
Échange le contenu de deux paires.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Paire d’échange de contenu avec.  
  
## <a name="remarks"></a>Notes  
 La fonction membre échange la paire de valeurs entre stockée `*this` et `right`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_pair_swap.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/utilitaire >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [paire (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [pair::operator= (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)