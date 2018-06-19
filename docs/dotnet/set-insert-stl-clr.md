---
title: Set::Insert (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 40472869-5c28-4658-b1d3-3ede4d8b8921
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 619dab8844920f61a19c5159fc96c688cafebfdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166024"
---
# <a name="setinsert-stlclr"></a>set::insert (STL/CLR)
Ajoute des éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
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
  
 La première fonction membre s’efforce insérer un élément avec la valeur `val`et retourne une paire de valeurs `X`. Si `X.second` a la valeur true, `X.first` désigne l’élément nouvellement inséré ; sinon `X.first` désigne un élément avec les équivalents classement déjà existe et qu’aucun nouvel élément est inséré. Il permet d’insérer un élément unique.  
  
 La deuxième fonction membre insère un élément avec la valeur `val`, à l’aide `where` en tant qu’indicateur (pour améliorer les performances) et retourne un itérateur qui désigne l’élément nouvellement inséré. Il permet d’insérer un élément unique qui peut être adjacent à un élément que vous connaissez.  
  
 La troisième fonction membre insère la séquence [`first`, `last`). Il permet d’insérer de zéro ou plusieurs des éléments copiés à partir d’une autre séquence.  
  
 La quatrième fonction membre insère la séquence désignée par le `right`. Il permet d’insérer une séquence décrite par l’énumérateur.  
  
 Chaque insertion des éléments du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée. Insertion peut se produire dans le temps fixe amorti, toutefois, étant donné un indicateur qui désigne un élément adjacent au point d’insertion.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_set_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_bool Pairib;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
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
    Myset c2;   
    Myset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myset c3;   
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
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [set (STL/CLR)](../dotnet/set-stl-clr.md)