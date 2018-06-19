---
title: Vector::rend (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::rend
dev_langs:
- C++
helpviewer_keywords:
- rend member [STL/CLR]
ms.assetid: 8dc1927f-9214-468d-877e-eda20c03e90d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 36d701d9259720663b12a0d2985ff2a97f16940b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168072"
---
# <a name="vectorrend-stlclr"></a>vector::rend (STL/CLR)
Désigne la fin de la séquence contrôlée inverse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rend();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` fin de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)   
 [Vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)   
 [vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)