---
title: opérateur&lt;= (pile) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::operator<=
dev_langs:
- C++
helpviewer_keywords:
- operator<= member [STL/CLR]
ms.assetid: fd2f500b-84d1-4eed-98ba-3a6f481ae8f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 261d0485acf21c1c58f911bec52faaf89e900a50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135506"
---
# <a name="operatorlt-stack-stlclr"></a>opérateur&lt;= (pile) (STL/CLR)
Inférieur ou égal de pile comparaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<=(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
## <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si `left` n’est pas ordonné après `right` lorsque les deux piles sont comparé élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_stack_operator_le.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
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
 **En-tête :** \<cliext/stack >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [pile (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [opérateur == (pile) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)   
 [opérateur ! = (pile) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)   
 [opérateur\< (pile) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)   
 [opérateur > = (pile) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)   
 [operator> (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)