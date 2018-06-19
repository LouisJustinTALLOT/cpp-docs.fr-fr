---
title: List::remove_if (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::remove_if
dev_langs:
- C++
helpviewer_keywords:
- remove_if member [STL/CLR]
ms.assetid: cbc66192-751b-41c5-b557-d5d7bbc2a840
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 53a6c12509e34e40d3a6a439fb03dc1f6779aba3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132321"
---
# <a name="listremoveif-stlclr"></a>list::remove_if (STL/CLR)
Supprime les éléments qui réussissent un test spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pred  
 Test d’éléments à supprimer.  
  
## <a name="remarks"></a>Notes  
 La fonction membre supprime de la séquence contrôlée (efface) chaque élément `X` pour laquelle `pred(X)` a la valeur true. Il permet de supprimer tous les éléments qui répondent à une condition que vous spécifiez comme une fonction ou un délégué.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b b b c  
a b b b c  
b b b  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::Clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [List::Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [List::Remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)