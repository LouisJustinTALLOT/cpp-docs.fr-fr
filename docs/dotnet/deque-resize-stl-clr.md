---
title: deque::Resize (STL/CLR) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::deque::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: c83f3c57-38b3-4706-a124-59bafbf88484
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fac11adade64d03696cbe73b09d1c35dfdd026b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="dequeresize-stlclr"></a>deque::resize (STL/CLR)
Modifie le nombre d’éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NEW_SIZE  
 Nouvelle taille de la séquence contrôlée.  
  
 Val  
 Valeur de l’élément de remplissage.  
  
## <a name="remarks"></a>Notes  
 Les deux fonctions membres Vérifiez que [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `()` retourne désormais `new_size`. Si elle doit rallonger la séquence contrôlée, la première fonction membre ajoute des éléments avec la valeur `value_type()`, tandis que la deuxième fonction membre ajoute des éléments avec la valeur `val`. Pour rendre la séquence contrôlée plus courte, les deux fonctions membres effacement efficacement le dernier élément [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() -` `new_size` fois. Vous l’utilisez pour vous assurer que la séquence contrôlée est de taille `new_size`, par la suppression ou la séquence contrôlée en cours de remplissage.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_deque_resize.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<cliext/deque >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::Clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)   
 [deque::Erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)   
 [deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)