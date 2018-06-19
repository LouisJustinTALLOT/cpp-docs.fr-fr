---
title: List::splice (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::splice
dev_langs:
- C++
helpviewer_keywords:
- splice member [STL/CLR]
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0c92faf6a4ec84e6ed65c58d02337038398d37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135948"
---
# <a name="listsplice-stlclr"></a>list::splice (STL/CLR)
Restitch les liens entre les nœuds.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Paramètres  
 premier  
 Début de plage à splice.  
  
 last  
 Fin de la plage à splice.  
  
 droite  
 Splice, à partir de conteneur.  
  
 où  
 Emplacement dans le conteneur à splice avant.  
  
## <a name="remarks"></a>Notes  
 La première fonction membre insère la séquence contrôlée par `right` avant l’élément dans la séquence contrôlée vers lequel pointée `where`. Elle supprime également tous les éléments de `right`. (`%right` ne doit pas correspondre `this`.) Il permet de splice tous d’une liste dans un autre.  
  
 La deuxième fonction membre supprime l’élément vers lequel pointé `first` dans la séquence contrôlée par `right` et l’insère avant l’élément dans la séquence contrôlée vers lequel pointe `where`. (Si `where` `==` `first` `||` `where` `== ++first`, aucune modification se produit.) Il permet de splice un élément unique d’une liste dans un autre.  
  
 La troisième fonction membre insère la sous-plage désignée par [`first`, `last`) à partir de la séquence contrôlée par `right` avant l’élément dans la séquence contrôlée vers lequel pointée `where`. Elle supprime également la sous-plage d'origine de la séquence contrôlée par `right`. (If `right` `==` `this`, la plage [`first`, `last`) ne doit pas inclure l’élément vers lequel pointé `where`.) Il permet de splice une sous-séquence de zéro ou plusieurs éléments d’une liste dans un autre.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_splice.cpp   
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
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::Assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [List::Insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)