---
title: opérateur&lt;= (deque) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::operator<=
dev_langs:
- C++
helpviewer_keywords:
- operator<= member [STL/CLR]
ms.assetid: b70cc499-35fb-4fa5-b8e3-5270bc647ace
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2f088c3d0cd1cb6c50d2bb4366c0217d9c6fde51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136660"
---
# <a name="operatorlt-deque-stlclr"></a>opérateur&lt;= (deque) (STL/CLR)
Deque inférieur ou égal comparaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
## <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si `left` n’est pas ordonné après `right` lorsque les deux classes deque est comparé élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_deque_operator_le.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/deque >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [opérateur == (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)   
 [deque::operator ! = (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)   
 [opérateur\< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)   
 [opérateur > = (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)   
 [operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)