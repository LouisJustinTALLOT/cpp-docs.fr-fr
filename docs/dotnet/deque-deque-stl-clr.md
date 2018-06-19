---
title: deque::deque (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::deque
dev_langs:
- C++
helpviewer_keywords:
- deque member [STL/CLR]
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 433b6ff053db0c642c2a81a5765755c9f42e1a0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112119"
---
# <a name="dequedeque-stlclr"></a>deque::deque (STL/CLR)
Construit un objet conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 `deque();`  
  
 Initialise la séquence contrôlée sans aucun élément. Il permet de spécifier une séquence contrôlée initiale vide.  
  
 Le constructeur :  
  
 `deque(deque<Value>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet deque `right`. Pour plus d’informations sur les itérateurs, consultez [deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md) et [deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md).  
  
 Le constructeur :  
  
 `deque(deque<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet deque dont le handle est `right`.  
  
 Le constructeur :  
  
 `explicit deque(size_type count);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `value_type()`. Utilisez-le pour remplir le conteneur avec des éléments dont la valeur par défaut.  
  
 Le constructeur :  
  
 `deque(size_type count, value_type val);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `val`. Utilisez-le pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Le constructeur :  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`). Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence.  
  
 Le constructeur :  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
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
 **En-tête :** \<cliext/deque >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::Assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)