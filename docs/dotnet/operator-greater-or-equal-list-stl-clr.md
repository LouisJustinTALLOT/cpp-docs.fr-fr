---
title: opérateur&gt;= (liste) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::operator>=
dev_langs:
- C++
helpviewer_keywords:
- operator>= member [STL/CLR]
ms.assetid: c6142241-8e85-4759-98fd-4f2b7d37b255
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f1eff6977b5929fec58b4ec9ed3b9ffe20f2d584
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135844"
---
# <a name="operatorgt-list-stlclr"></a>opérateur&gt;= (liste) (STL/CLR)
Liste supérieur ou égal à comparaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator>=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
## <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left` `<` `right)`. Il permet de tester si `left` n’est pas classé avant `right` lorsque les deux listes sont comparées d’élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_operator_ge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [opérateur == (liste) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)   
 [opérateur ! = (liste) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [opérateur\< (liste) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)   
 [opérateur > (liste) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)