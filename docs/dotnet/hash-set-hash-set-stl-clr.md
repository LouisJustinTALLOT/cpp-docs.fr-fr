---
title: hash_set::hash_set (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::hash_set
dev_langs:
- C++
helpviewer_keywords:
- hash_set member [STL/CLR]
ms.assetid: 006414ed-db5a-4c08-ac81-4a8ae57d0aad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e0f8ce11d66b02c63d2eee6cf2022c16c214fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136192"
---
# <a name="hashsethashset-stlclr"></a>hash_set::hash_set (STL/CLR)
Construit un objet conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
hash_set();  
explicit hash_set(key_compare^ pred);  
hash_set(key_compare^ pred, hasher^ hashfn);  
hash_set(hash_set<Key>% right);  
hash_set(hash_set<Key>^ right);  
template<typename InIter>  
    hash_sethash_set(InIter first, InIter last);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>Paramètres  
 premier  
 Début de la plage à insérer.  
  
 hashfn  
 Fonction pour les clés de mappage pour les compartiments de hachage.  
  
 last  
 Fin de la plage à insérer.  
  
 pred  
 Classement de prédicat pour la séquence contrôlée.  
  
 droite  
 Objet ou plage à insérer.  
  
## <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `hash_set();`  
  
 Initialise la séquence contrôlée sans aucun élément, avec la valeur par défaut classement prédicat `key_compare()`et avec la fonction de hachage par défaut. Il permet de spécifier une séquence contrôlée initiale vide avec la fonction de prédicat et hachage de classement par défaut.  
  
 Le constructeur :  
  
 `explicit hash_set(key_compare^ pred);`  
  
 Initialise la séquence contrôlée sans aucun élément, avec le prédicat de tri `pred`et avec la fonction de hachage par défaut. Il permet de spécifier une séquence contrôlée initiale vide avec le prédicat de tri spécifié et la fonction de hachage par défaut.  
  
 Le constructeur :  
  
 `hash_set(key_compare^ pred, hasher^ hashfn);`  
  
 Initialise la séquence contrôlée sans aucun élément, avec le prédicat de tri `pred`et avec la fonction de hachage `hashfn`. Il permet de spécifier une séquence contrôlée initiale vide avec la fonction de prédicat et hachage de tri spécifiée.  
  
 Le constructeur :  
  
 `hash_set(hash_set<Key>% right);`  
  
 Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`), avec la valeur par défaut de classement de prédicat et avec la fonction de hachage par défaut. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet hash_set `right`avec le prédicat de tri par défaut et la fonction de hachage.  
  
 Le constructeur :  
  
 `hash_set(hash_set<Key>^ right);`  
  
 Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`), avec la valeur par défaut de classement de prédicat et avec la fonction de hachage par défaut. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet hash_set `right`avec le prédicat de tri par défaut et la fonction de hachage.  
  
 Le constructeur :  
  
 `template<typename InIter> hash_set(InIter first, InIter last);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`), avec la valeur par défaut de classement de prédicat et avec la fonction de hachage par défaut. Il permet de rendre la séquence contrôlée une copie d’une autre séquence, avec la fonction de prédicat et hachage de classement par défaut.  
  
 Le constructeur :  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`), avec le prédicat de tri `pred`et avec la fonction de hachage par défaut. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri spécifié et la fonction de hachage par défaut.  
  
 Le constructeur :  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Initialise la séquence contrôlée par la séquence [`first`, `last`), avec le prédicat de tri `pred`et avec la fonction de hachage `hashfn`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence, avec la fonction de prédicat et hachage de tri spécifiée.  
  
 Le constructeur :  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`, avec la valeur par défaut de classement de prédicat et avec la fonction de hachage par défaut. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec la fonction de prédicat et hachage de classement par défaut.  
  
 Le constructeur :  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`, avec le prédicat de tri `pred`et avec la fonction de hachage par défaut. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur avec la fonction de hachage par défaut et le prédicat de tri spécifiée.  
  
 Le constructeur :  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Initialise la séquence contrôlée par la séquence désignée par l’énumérateur `right`, avec le prédicat de tri `pred`et avec la fonction de hachage `hashfn`. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par l’énumérateur, avec la fonction de prédicat et hachage de tri spécifiée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
// construct an empty container   
    Myhash_set c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_set c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_set c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_set c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_set c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_set c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_set c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_set c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_set c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_set c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash_set::operator= (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)