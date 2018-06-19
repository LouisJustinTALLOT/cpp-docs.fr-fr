---
title: opérateur ! = (set) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::operator!=
dev_langs:
- C++
helpviewer_keywords:
- operator!= member [STL/CLR]
ms.assetid: cb82d6a4-0954-49a4-b979-a9ae39df9553
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d841db6586f7b96caaf860b8fa783b9f8dbce34a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133829"
---
# <a name="operator-set-stlclr"></a>operator!= (set) (STL/CLR)
Liste de comparaison n’est pas égal.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key>  
    bool operator!=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
## <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si `left` n’est pas ordonné identique `right` lorsque les deux jeux sont comparé élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_set_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [opérateur == (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)   
 [opérateur\< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)   
 [opérateur > = (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)   
 [opérateur > (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)   
 [operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)