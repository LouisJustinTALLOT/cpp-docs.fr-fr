---
title: deque::Erase (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 831fbc2b-604f-446b-88bc-b37531304c33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5afcc69c27cf96f31d85b4c48d57540669941cbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110180"
---
# <a name="dequeerase-stlclr"></a>deque::erase (STL/CLR)
Supprime les éléments placés aux positions spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `first`  
 Début de la plage à effacer.  
  
 `last`  
 Fin de la plage à effacer.  
  
 `where`  
 Élément à effacer.  
  
## <a name="remarks"></a>Notes  
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé `where`. Il permet de supprimer un seul élément.  
  
 La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Il permet de supprimer de zéro ou plusieurs éléments contigus.  
  
 Les deux fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md) `()` si cet élément n’existe.  
  
 Lorsque vous supprimez des éléments, le nombre de copies de l’élément est linéaire quant au nombre d’éléments entre la fin de la suppression et la fin la plus proche de la séquence. (Lorsque vous supprimez un ou plusieurs éléments à chaque extrémité de la séquence, aucune copie de l’élément se produit.)  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cliext_deque_erase.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::deque<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/deque >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)