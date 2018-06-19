---
title: List::sort (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::sort
dev_langs:
- C++
helpviewer_keywords:
- sort member [STL/CLR]
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 670b18e5901ef264474256a1a1e57cde7a28ef01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138342"
---
# <a name="listsort-stlclr"></a>list::sort (STL/CLR)
Ordonne la séquence contrôlée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pred  
 Comparateur pour les paires d’éléments.  
  
## <a name="remarks"></a>Notes  
 La première fonction membre réorganise les éléments dans la séquence contrôlée afin qu’ils sont classés par `operator<` --éléments ne réduisez pas de valeur au cours de la séquence. Vous utilisez cette fonction membre pour trier la séquence dans l’ordre croissant.  
  
 La deuxième fonction membre comporte comme la première, sauf que la séquence est triée par `pred`  --  `pred(X, Y)` a la valeur false pour tout élément `X` qui suit l’élément `Y` dans la séquence résultante. Il permet de trier la séquence dans un ordre que vous spécifiez à une fonction de prédicat ou un délégué.  
  
 Les fonctions permettent d’effectuer un tri stable--aucune paire d’éléments dans la séquence contrôlée d’origine n’est inversée dans la séquence contrôlée qui en résulte.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::Merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)   
 [List::Reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)   
 [List::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)   
 [list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)