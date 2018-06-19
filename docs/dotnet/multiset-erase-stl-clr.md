---
title: multiset::Erase (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 3ff9fe2d-bf43-446a-bd3f-74550313a1d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bb5ac657a70d61f43245fb04bd4f49642e81a5f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136712"
---
# <a name="multiseterase-stlclr"></a>multiset::erase (STL/CLR)
Supprime les éléments placés aux positions spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
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
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé `where`et retourne un itérateur qui désigne le premier élément restant après l’élément supprimé, ou [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()` si cet élément n’existe. Il permet de supprimer un seul élément.  
  
 La deuxième fonction membre supprime les éléments de la séquence contrôlée dans la plage [`first`, `last`) et retourne un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `end()` si aucun élément correspondant existe... Il permet de supprimer de zéro ou plusieurs éléments contigus.  
  
 La troisième fonction membre supprime tout élément de la séquence contrôlée, dont la clé a un classement équivalent à `key`et retourne le nombre d’éléments supprimés. Utilisez-le pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.  
  
 Effacement de chaque élément du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_multiset_erase.cpp   
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
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Mymultiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)