---
title: List::Resize (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: c4b8d41f-a62b-4dbc-8568-0e0a9da24016
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bc9a883c2bd645713d631365675cfd7fd302d53e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133608"
---
# <a name="listresize-stlclr"></a>list::resize (STL/CLR)
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
 Les deux fonctions membres Vérifiez que [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` retourne désormais `new_size`. Si elle doit rallonger la séquence contrôlée, la première fonction membre ajoute des éléments avec la valeur `value_type()`, tandis que la deuxième fonction membre ajoute des éléments avec la valeur `val`. Pour rendre la séquence contrôlée plus courte, les deux fonctions membres effacement efficacement le dernier élément [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` fois. Vous l’utilisez pour vous assurer que la séquence contrôlée est de taille `new_size`, par la suppression ou la séquence contrôlée en cours de remplissage.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::Clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [List::Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)