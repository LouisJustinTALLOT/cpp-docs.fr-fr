---
title: opérateur ! = (paire) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::operator!=
dev_langs:
- C++
helpviewer_keywords:
- operator!= member [STL/CLR]
ms.assetid: 167005f9-727d-40af-8d6d-2793d0daa96a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 70d5d51ecf63667744d8c75dd9d3384bad8deb2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33141163"
---
# <a name="operator-pair-stlclr"></a>operator!= (pair) (STL/CLR)
Paires de comparaison n’est pas égal.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator!=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Paire de gauche à comparer.  
  
 droite  
 Paire de droit à comparer.  
  
## <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si `left` n’est pas ordonné identique `right` lorsque deux paires sont comparé élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_pair_operator_ne.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] != [x 3] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[x 3] != [x 4] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] != [x 3] is False  
[x 3] != [x 4] is True  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/utilitaire >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [paire (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [opérateur == (pair) (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [opérateur\< (paire) (STL/CLR)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [opérateur > = (paire) (STL/CLR)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [opérateur > (paire) (STL/CLR)](../dotnet/operator-greater-than-pair-stl-clr.md)   
 [operator<= (pair) (STL/CLR)](../dotnet/operator-less-or-equal-pair-stl-clr.md)