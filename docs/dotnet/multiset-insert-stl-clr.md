---
title: multiset::Insert (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 7a3b1cc8-ec60-4ed0-ace5-46cb5872e6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed7be7302b1dcef069dc1e786e59e87755366613
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135302"
---
# <a name="multisetinsert-stlclr"></a>multiset::insert (STL/CLR)
Ajoute des éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 droite  
 Énumération à insérer.  
  
 Val  
 Valeur de clé à insérer.  
  
 où  
 Emplacement dans le conteneur à insérer (hint uniquement).  
  
## <a name="remarks"></a>Notes  
 Chacune des fonctions membres insère une séquence spécifiée par les opérandes restants.  
  
 La première fonction membre insère un élément avec la valeur `val`et retourne un itérateur qui désigne l’élément nouvellement inséré. Il permet d’insérer un élément unique.  
  
 La deuxième fonction membre insère un élément avec la valeur `val`, à l’aide `where` en tant qu’indicateur (pour améliorer les performances) et retourne un itérateur qui désigne l’élément nouvellement inséré. Il permet d’insérer un élément unique qui peut être adjacent à un élément que vous connaissez.  
  
 La troisième fonction membre insère la séquence [`first`, `last`). Il permet d’insérer de zéro ou plusieurs des éléments copiés à partir d’une autre séquence.  
  
 La quatrième fonction membre insère la séquence désignée par le `right`. Il permet d’insérer une séquence décrite par l’énumérateur.  
  
 Chaque insertion des éléments du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée. Insertion peut se produire dans le temps fixe amorti, toutefois, étant donné un indicateur qui désigne un élément adjacent au point d’insertion.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultiset c2;   
    Mymultiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)