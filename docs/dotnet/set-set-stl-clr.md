---
title: Set::Set (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::set
dev_langs:
- C++
helpviewer_keywords:
- set member [STL/CLR]
ms.assetid: 0cce8501-92ed-431c-b711-14e0b7be7375
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6de8bb2616cd403e150ace02210e57ed5a019445
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172600"
---
# <a name="setset-stlclr"></a>set::set (STL/CLR)
Construit un objet conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 pred  
 Classement de prédicat pour la séquence contrôlée.  
  
 droite  
 Objet ou plage à insérer.  
  
## <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `set();`  
  
 Initialise la séquence contrôlée sans aucun élément, avec la valeur par défaut classement prédicat `key_compare()`. Il permet de spécifier une séquence contrôlée initiale vide avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `explicit set(key_compare^ pred);`  
  
 Initialise la séquence contrôlée sans aucun élément, avec le prédicat de tri `pred`. Il permet de spécifier une séquence contrôlée initiale vide avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `set(set<Key>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`), avec la valeur par défaut de classement de prédicat. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de jeu `right`, avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `set(set<Key>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`), avec la valeur par défaut de classement de prédicat. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de jeu `right`, avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`), avec la valeur par défaut de classement de prédicat. Il permet de rendre la séquence contrôlée une copie d’une autre séquence, avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`), avec le prédicat de tri `pred`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`, avec la valeur par défaut de classement de prédicat. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`, avec le prédicat de tri `pred`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur, avec le prédicat de tri spécifié.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)   
 [set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)