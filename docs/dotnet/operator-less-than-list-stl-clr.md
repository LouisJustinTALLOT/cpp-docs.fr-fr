---
title: opérateur&lt; (liste) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::operator<
dev_langs:
- C++
helpviewer_keywords:
- operator< member [STL/CLR]
ms.assetid: 6990fac2-3eeb-481f-b289-1c93f51422e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9cfea5ae23ffa7e84367ea878bcf3c74c002280a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134292"
---
# <a name="operatorlt-list-stlclr"></a>opérateur&lt; (liste) (STL/CLR)
Liste inférieure à comparaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
## <a name="remarks"></a>Notes  
 L’opérateur fonction retourne true si, pour la position la plus basse `i` pour lequel `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Sinon, elle retourne `left->size() < right->size()` vous l’utiliser pour tester si `left` est classé avant `right` lorsque les deux listes sont comparées d’élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_operator_lt.cpp   
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
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [opérateur == (liste) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)   
 [opérateur ! = (liste) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [opérateur > = (liste) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [opérateur > (liste) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)