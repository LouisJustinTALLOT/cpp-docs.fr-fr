---
title: List::unique (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::unique
dev_langs:
- C++
helpviewer_keywords:
- unique member [STL/CLR]
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5dbfab0fb53a4ca11128d01e7b32060c6428549
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137573"
---
# <a name="listunique-stlclr"></a>list::unique (STL/CLR)
Supprime des éléments adjacents qui réussissent un test spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pred  
 Comparateur pour les paires d’éléments.  
  
## <a name="remarks"></a>Notes  
 La première fonction membre supprime de la séquence contrôlée (efface) chaque élément dont la valeur est égale à son élément précédent--si élément `X` précède l’élément `Y` et `X == Y`, la fonction membre supprime `Y`. Utilisez-le pour supprimer un seul copie de chaque sous-séquence des éléments adjacents qu’égal à comparer. Notez que si la séquence contrôlée est triée, par exemple en appelant [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, la fonction membre laisse uniquement les éléments avec des valeurs uniques. (D’où leur nom.)  
  
 La deuxième fonction membre comporte comme la première, à ceci près qu’elle supprime chaque élément `Y` suivant d’un élément `X` pour lequel `pred(X, Y)`. Il permet de supprimer un seul copie de chaque sous-séquence des éléments adjacents qui satisfont une fonction de prédicat ou un délégué que vous spécifiez. Notez que si la séquence contrôlée est triée, par exemple en appelant `sort(pred)`, la fonction membre laisse uniquement les éléments qui n’ont pas un classement équivalent à d’autres éléments.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List::Remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [List::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)