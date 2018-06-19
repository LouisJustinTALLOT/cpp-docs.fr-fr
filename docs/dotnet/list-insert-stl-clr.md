---
title: List::Insert (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 399ed30f-6b76-41a8-b180-6070e3ca1c68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0e1ce686cbf905a0e49f94e4d8cebf180fbc0224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134283"
---
# <a name="listinsert-stlclr"></a>list::insert (STL/CLR)
Ajoute des éléments à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 count  
 Nombre d’éléments à insérer.  
  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 droite  
 Énumération à insérer.  
  
 Val  
 Valeur de l’élément à insérer.  
  
 où  
 Emplacement dans le conteneur à insérer avant.  
  
## <a name="remarks"></a>Notes  
 Chaque membre fonctions insertions, avant l’élément vers lequel pointé `where` dans la séquence contrôlée, une séquence spécifiée par les opérandes restants.  
  
 La première fonction membre insère un élément avec la valeur `val` et retourne un itérateur qui désigne l’élément nouvellement inséré. Il permet d’insérer un élément unique avant un endroit désigné par un itérateur.  
  
 La deuxième fonction membre insère une répétition de `count` éléments ayant la valeur `val`. Il permet d’insérer des éléments contigus zéro ou plus qui sont toutes les copies de la même valeur.  
  
 Si `InIt` est un type entier, la troisième fonction membre se comporte comme `insert(where, (size_type)first, (value_type)last)`. Dans le cas contraire, il insère la séquence [`first`, `last`). Il permet d’insérer de zéro ou plusieurs éléments contigus, copiés à partir d’une autre séquence.  
  
 La quatrième fonction membre insère la séquence désignée par le `right`. Il permet d’insérer une séquence décrite par l’énumérateur.  
  
 Lors de l’insertion d’un élément unique, le nombre de copies de l’élément est linéaire quant au nombre d’éléments entre le point d’insertion et la fin la plus proche de la séquence. (Lors de l’insertion d’un ou plusieurs éléments à chaque extrémité de la séquence, aucune copie de l’élément se produit.) Si `InIt` est un itérateur d’entrée, la troisième fonction membre exécute en réalité une insertion unique pour chaque élément dans la séquence. Sinon, lors de l’insertion `N` éléments, le nombre de copies de l’élément est linéaire dans `N` plus le nombre d’éléments entre le point d’insertion et la fin la plus proche de la séquence.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_insert.cpp   
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
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)