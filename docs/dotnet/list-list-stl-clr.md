---
title: List::List (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::list
dev_langs:
- C++
helpviewer_keywords:
- list member [STL/CLR]
ms.assetid: 51b58f63-c65a-4d54-b746-0c10635b123b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cacfa4bb1d852a62d81d4496f19371072f2615f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137775"
---
# <a name="listlist-stlclr"></a>list::list (STL/CLR)
Construit un objet conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `count`  
 Nombre d’éléments à insérer.  
  
 `first`  
 Début de la plage à insérer.  
  
 `last`  
 Fin de la plage à insérer.  
  
 `right`  
 Objet ou plage à insérer.  
  
 `val`  
 Valeur de l’élément à insérer.  
  
## <a name="remarks"></a>Notes  
  
 Le constructeur :  
  
 `list();`  
  
 Initialise la séquence contrôlée sans aucun élément. Il permet de spécifier une séquence contrôlée initiale vide.  
  
 Le constructeur :  
  
 `list(list<Value>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de liste `right`.  
  
 Le constructeur :  
  
 `list(list<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de liste dont le handle est `right`.  
  
 Le constructeur :  
  
 `explicit list(size_type count);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `value_type()`. Utilisez-le pour remplir le conteneur avec des éléments dont la valeur par défaut.  
  
 Le constructeur :  
  
 `list(size_type count, value_type val);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `val`. Utilisez-le pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Le constructeur :  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`). Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence.  
  
 Le constructeur :  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::Assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [List::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)   
 [list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)