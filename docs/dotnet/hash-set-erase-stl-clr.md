---
title: hash_set::Erase (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 620998a0-00c9-4be6-899b-2d71661375b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9bed64a6a96d5f7a1b4a629496072c6b886eb56e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128304"
---
# <a name="hashseterase-stlclr"></a>hash_set::erase (STL/CLR)
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
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé `where`et retourne un itérateur qui désigne le premier élément restant après l’élément supprimé, ou [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) `()` si cet élément n’existe. Il permet de supprimer un seul élément.  
  
 La deuxième fonction membre supprime les éléments de la séquence contrôlée dans la plage [`first`, `last`) et retourne un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `end()` si aucun élément correspondant existe... Il permet de supprimer de zéro ou plusieurs éléments contigus.  
  
 La troisième fonction membre supprime tout élément de la séquence contrôlée, dont la clé a un classement équivalent à `key`et retourne le nombre d’éléments supprimés. Utilisez-le pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.  
  
 Effacement de chaque élément du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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
    Myhash_set::iterator it = c1.end();   
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
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::clear (STL/CLR)](../dotnet/hash-set-clear-stl-clr.md)