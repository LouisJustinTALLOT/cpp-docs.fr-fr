---
title: Set::upper_bound (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::upper_bound
dev_langs:
- C++
helpviewer_keywords:
- upper_bound member [STL/CLR]
ms.assetid: 874d258a-990f-486f-ac7b-757a2f7c150a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da9f1ce48d77d3168dbfcb61d6ff23415d4f4c5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164065"
---
# <a name="setupperbound-stlclr"></a>set::upper_bound (STL/CLR)
Fin de la recherche de plage qui correspond à une clé spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Paramètres  
 clé  
 Valeur de clé à rechercher.  
  
## <a name="remarks"></a>Notes  
 La fonction membre détermine le dernier élément `X` dans la séquence contrôlée qui a un classement équivalent à `key`. Si cet élément n’existe, ou si `X` est le dernier élément dans la séquence contrôlée, elle retourne [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; sinon, elle retourne un itérateur qui désigne le premier élément au-delà de `X`. Il permet de localiser la fin d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_set_upper_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set::Count (STL/CLR)](../dotnet/set-count-stl-clr.md)   
 [Set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)   
 [Set::Find (STL/CLR)](../dotnet/set-find-stl-clr.md)   
 [set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)