---
title: List::Merge (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::merge
dev_langs:
- C++
helpviewer_keywords:
- merge member [STL/CLR]
ms.assetid: f8e93cd3-bd08-4086-859b-08a2899cc9a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ff5ba18dea3b33d1cf3a50dedfc5e90055e69c3e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133400"
---
# <a name="listmerge-stlclr"></a>list::merge (STL/CLR)
Fusionne deux séquences contrôlées ordonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pred  
 Comparateur pour les paires d’éléments.  
  
 droite  
 Conteneur à fusionner.  
  
## <a name="remarks"></a>Notes  
 La première fonction membre supprime tous les éléments de la séquence contrôlée par `right` et les insérer dans la séquence contrôlée. Les deux séquences doivent être triés précédemment par `operator<` --éléments ne doivent pas diminuer de valeur au cours de chaque séquence. La séquence résultante est également classée par `operator<`. Vous utilisez cette fonction membre pour fusionner deux séquences qui augmentent la valeur dans une séquence qui augmente également de valeur.  
  
 La deuxième fonction membre comporte comme la première, sauf que les séquences sont classés par `pred`  --  `pred(X, Y)` doit avoir la valeur false pour tout élément `X` qui suit l’élément `Y` dans la séquence. Il permet de fusionner deux séquences classés par une fonction de prédicat ou un délégué que vous spécifiez.  
  
 Les fonctions permettent d’effectuer une fusion stable--aucune paire d’éléments dans une des séquences contrôlées d’origine n’est inversée dans la séquence contrôlée qui en résulte. En outre, si une paire d’éléments `X` et `Y` dans la séquence contrôlée qui en résulte a un classement équivalent-- `!(X < Y) && !(X < Y)` --un élément à partir de la séquence contrôlée d’origine apparaît avant un élément de la séquence contrôlée par `right`.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)   
 [list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)