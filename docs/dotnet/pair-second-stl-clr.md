---
title: pair::second (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::second
dev_langs:
- C++
helpviewer_keywords:
- second member [STL/CLR]
ms.assetid: f30d3d1f-c7be-45d2-92ff-6861b96a92ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7b81d0649c4a8e07ccbfbeedd3a332813d0ef14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159910"
---
# <a name="pairsecond-stlclr"></a>pair::second (STL/CLR)
Le deuxième de valeur encapsulée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Value2 second;  
```  
  
## <a name="remarks"></a>Notes  
 L’objet stocke la deuxième valeur encapsulée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_pair_second.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/utilitaire >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [paire (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [pair::First (STL/CLR)](../dotnet/pair-first-stl-clr.md)   
 [pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)   
 [pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)