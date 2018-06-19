---
title: List::operator = (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: 0e4fdcc6-7574-40af-b947-98c2c683676d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2af22713e5f8339eb9a60509bba04d67dfb5f572
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131265"
---
# <a name="listoperator-stlclr"></a>list::operator= (STL/CLR)
Remplace la séquence contrôlée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
list<Value>% operator=(list<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Conteneur à copier.  
  
## <a name="remarks"></a>Notes  
 Les copies d’opérateur de membre `right` à l’objet, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans `right`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_operator_as.cpp   
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
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)