---
title: Vector::Vector (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector member [STL/CLR]
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6921428c43ccc46b28b14523f8b17fff9185453
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172564"
---
# <a name="vectorvector-stlclr"></a>vector::vector (STL/CLR)
Construit un objet conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 count  
 Nombre d’éléments à insérer.  
  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 droite  
 Objet ou plage à insérer.  
  
 Val  
 Valeur de l’élément à insérer.  
  
## <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `vector();`  
  
 Initialise la séquence contrôlée sans aucun élément. Il permet de spécifier une séquence contrôlée initiale vide.  
  
 Le constructeur :  
  
 `vector(vector<Value>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet vector `right`.  
  
 Le constructeur :  
  
 `vector(vector<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`). Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de vecteur dont le handle est `right`.  
  
 Le constructeur :  
  
 `explicit vector(size_type count);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `value_type()`. Utilisez-le pour remplir le conteneur avec des éléments dont la valeur par défaut.  
  
 Le constructeur :  
  
 `vector(size_type count, value_type val);`  
  
 Initialise la séquence contrôlée avec `count` éléments dont la valeur `val`. Utilisez-le pour remplir le conteneur avec des éléments dont la même valeur.  
  
 Le constructeur :  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`). Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence.  
  
 Le constructeur :  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
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
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)   
 [Vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)