---
title: multimap::Erase (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 94623cfc-4464-44a6-afd4-90a36828ac2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d9d57632c65c7140334869b6b2dbca71a3f25b2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134960"
---
# <a name="multimaperase-stlclr"></a>multimap::erase (STL/CLR)
Supprime les éléments placés aux positions spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>Paramètres  
 premier  
 Début de la plage à effacer.  
  
 clé  
 Valeur de clé à effacer.  
  
 last  
 Fin de la plage à effacer.  
  
 où  
 Élément à effacer.  
  
## <a name="remarks"></a>Notes  
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé `where`et retourne un itérateur qui désigne le premier élément restant après l’élément supprimé, ou [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md) `()` si cet élément n’existe. Il permet de supprimer un seul élément.  
  
 La deuxième fonction membre supprime les éléments de la séquence contrôlée dans la plage [`first`, `last`) et retourne un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `end()` si aucun élément correspondant existe... Il permet de supprimer de zéro ou plusieurs éléments contigus.  
  
 La troisième fonction membre supprime tout élément de la séquence contrôlée, dont la clé a un classement équivalent à `key`et retourne le nombre d’éléments supprimés. Utilisez-le pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.  
  
 Effacement de chaque élément du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_multimap_erase.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    cliext::multimap<wchar_t, int> c1;   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::multimap<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)