---
title: unordered_multiset, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_multiset
- unordered_set/std::unordered_multiset
- unordered_set/std::unordered_multiset::allocator_type
- unordered_set/std::unordered_multiset::const_iterator
- unordered_set/std::unordered_multiset::const_local_iterator
- unordered_set/std::unordered_multiset::const_pointer
- unordered_set/std::unordered_multiset::const_reference
- unordered_set/std::unordered_multiset::difference_type
- unordered_set/std::unordered_multiset::hasher
- unordered_set/std::unordered_multiset::iterator
- unordered_set/std::unordered_multiset::key_equal
- unordered_set/std::unordered_multiset::key_type
- unordered_set/std::unordered_multiset::local_iterator
- unordered_set/std::unordered_multiset::pointer
- unordered_set/std::unordered_multiset::reference
- unordered_set/std::unordered_multiset::size_type
- unordered_set/std::unordered_multiset::value_type
- unordered_set/std::unordered_multiset::begin
- unordered_set/std::unordered_multiset::bucket
- unordered_set/std::unordered_multiset::bucket_count
- unordered_set/std::unordered_multiset::bucket_size
- unordered_set/std::unordered_multiset::cbegin
- unordered_set/std::unordered_multiset::cend
- unordered_set/std::unordered_multiset::clear
- unordered_set/std::unordered_multiset::count
- unordered_set/std::unordered_multiset::emplace
- unordered_set/std::unordered_multiset::emplace_hint
- unordered_set/std::unordered_multiset::empty
- unordered_set/std::unordered_multiset::end
- unordered_set/std::unordered_multiset::equal_range
- unordered_set/std::unordered_multiset::erase
- unordered_set/std::unordered_multiset::find
- unordered_set/std::unordered_multiset::get_allocator
- unordered_set/std::unordered_multiset::hash
- unordered_set/std::unordered_multiset::insert
- unordered_set/std::unordered_multiset::key_eq
- unordered_set/std::unordered_multiset::load_factor
- unordered_set/std::unordered_multiset::max_bucket_count
- unordered_set/std::unordered_multiset::max_load_factor
- unordered_set/std::unordered_multiset::max_size
- unordered_set/std::unordered_multiset::rehash
- unordered_set/std::unordered_multiset::size
- unordered_set/std::unordered_multiset::swap
- unordered_set/std::unordered_multiset::unordered_multiset
- unordered_set/std::unordered_multiset::operator=
- unordered_set/std::unordered_multiset::allocator_type
- unordered_set/std::unordered_multiset::const_iterator
- unordered_set/std::unordered_multiset::const_local_iterator
- unordered_set/std::unordered_multiset::const_pointer
- unordered_set/std::unordered_multiset::const_reference
- unordered_set/std::unordered_multiset::difference_type
- unordered_set/std::unordered_multiset::hasher
- unordered_set/std::unordered_multiset::iterator
- unordered_set/std::unordered_multiset::key_equal
- unordered_set/std::unordered_multiset::key_type
- unordered_set/std::unordered_multiset::local_iterator
- unordered_set/std::unordered_multiset::pointer
- unordered_set/std::unordered_multiset::reference
- unordered_set/std::unordered_multiset::size_type
- unordered_set/std::unordered_multiset::value_type
- unordered_set/std::unordered_multiset::begin
- unordered_set/std::unordered_multiset::bucket
- unordered_set/std::unordered_multiset::bucket_count
- unordered_set/std::unordered_multiset::bucket_size
- unordered_set/std::unordered_multiset::cbegin
- unordered_set/std::unordered_multiset::cend
- unordered_set/std::unordered_multiset::clear
- unordered_set/std::unordered_multiset::count
- unordered_set/std::unordered_multiset::emplace
- unordered_set/std::unordered_multiset::emplace_hint
- unordered_set/std::unordered_multiset::empty
- unordered_set/std::unordered_multiset::end
- unordered_set/std::unordered_multiset::equal_range
- unordered_set/std::unordered_multiset::erase
- unordered_set/std::unordered_multiset::find
- unordered_set/std::unordered_multiset::get_allocator
- unordered_set/std::unordered_multiset::hash_function
- unordered_set/std::unordered_multiset::insert
- unordered_set/std::unordered_multiset::key_eq
- unordered_set/std::unordered_multiset::load_factor
- unordered_set/std::unordered_multiset::max_bucket_count
- unordered_set/std::unordered_multiset::max_load_factor
- unordered_set/std::unordered_multiset::max_size
- unordered_set/std::unordered_multiset::rehash
- unordered_set/std::unordered_multiset::size
- unordered_set/std::unordered_multiset::swap
dev_langs:
- C++
helpviewer_keywords:
- unordered_multiset class
ms.assetid: 70c8dfc5-492a-4af2-84f5-1aa9cb04b71c
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 4df02938056e6a49c71de0ce594cf7eeb84208f6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="unorderedmultiset-class"></a>unordered_multiset, classe
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable constituée d'éléments de type `const Key`. La séquence est triée par ordre faible avec une fonction de hachage, qui partitionne la séquence en un ensemble trié de sous-séquences appelées compartiments. Dans chaque compartiment, une fonction de comparaison détermine si des paires d'éléments possèdent un ordre équivalent. Chaque élément sert à la fois de clé de tri et de valeur. La séquence est représentée de façon à permettre la recherche, l'insertion et la suppression d'un élément arbitraire à l'aide d'un certain nombre d'opérations qui peut être indépendant du nombre d'éléments de la séquence (temps constant), du moins lorsque les compartiments sont de longueur à peu près équivalente. Dans le pire des cas, lorsque tous les éléments se trouvent dans un compartiment, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (temps linéaire). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key>>  
class unordered_multiset;  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Key`|Type de clé.|  
|`Hash`|Type d'objet de la fonction de hachage.|  
|`Pred`|Type d’objet de fonction de comparaison d’égalité.|  
|`Alloc`|Classe allocator.|  
  
## <a name="members"></a>Membres  
  
|||  
|-|-|  
|Définition de types|Description|  
|[allocator_type](#allocator_type)|Type d'un allocateur pour la gestion du stockage.|  
|[const_iterator](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[const_local_iterator](#const_local_iterator)|Type d’un itérateur de compartiment constant pour la séquence contrôlée.|  
|[const_pointer](#const_pointer)|Type d'un pointeur constant vers un élément.|  
|[const_reference](#const_reference)|Type d'une référence constante à un élément.|  
|[difference_type](#difference_type)|Type d'une distance signée entre deux éléments.|  
|[hasher](#hasher)|Type de la fonction de hachage.|  
|[iterator](#iterator)|Type d'un itérateur pour la séquence contrôlée.|  
|[key_equal](#key_equal)|Type de la fonction de comparaison.|  
|[key_type](#key_type)|Type d'une clé de tri.|  
|[local_iterator](#local_iterator)|Type d'un itérateur de compartiment pour la séquence contrôlée.|  
|[pointer](#pointer)|Type d'un pointeur vers un élément.|  
|[reference](#reference)|Type d'une référence à un élément.|  
|[size_type](#size_type)|Type d'une distance non signée entre deux éléments.|  
|[value_type](#value_type)|Type d’un élément.|  
  
|||  
|-|-|  
|Fonction membre|Description|  
|[begin](#begin)|Désigne le début de la séquence contrôlée.|  
|[compartiment](#bucket)|Obtient le numéro du compartiment pour une valeur de clé.|  
|[bucket_count](#bucket_count)|Obtient le nombre de compartiments.|  
|[bucket_size](#bucket_size)|Obtient la taille d'un compartiment.|  
|[cbegin](#cbegin)|Désigne le début de la séquence contrôlée.|  
|[cend](#cend)|Désigne la fin de la séquence contrôlée.|  
|[clear](#clear)|Supprime tous les éléments.|  
|[count](#count)|Recherche le nombre d’éléments qui correspondent à une clé spécifiée.|  
|[emplace](#emplace)|Ajoute un élément construit sur place.|  
|[emplace_hint](#emplace_hint)|Ajoute un élément construit sur place, avec un indicateur.|  
|[empty](#empty)|Vérifie l'absence d'éléments.|  
|[end](#end)|Désigne la fin de la séquence contrôlée.|  
|[equal_range](#equal_range)|Recherche une plage qui correspond à une clé spécifiée.|  
|[erase](#erase)|Supprime les éléments placés aux positions spécifiées.|  
|[find](#find)|Recherche un élément qui correspond à une clé spécifiée.|  
|[get_allocator](#get_allocator)|Obtient l’objet allocateur stocké.|  
|[hash_function](#hash)|Obtient l'objet de fonction de hachage stocké.|  
|[insert](#insert)|Ajoute des éléments.|  
|[key_eq](#key_eq)|Obtient l'objet de fonction de comparaison stocké.|  
|[load_factor](#load_factor)|Compte le nombre moyen d'éléments par compartiment.|  
|[max_bucket_count](#max_bucket_count)|Obtient le nombre maximal de compartiments.|  
|[max_load_factor](#max_load_factor)|Obtient ou définit le nombre maximal d’éléments par compartiment.|  
|[max_size](#max_size)|Obtient ou définit la taille maximale de la séquence contrôlée.|  
|[rehash)](#rehash)|Régénère la table de hachage.|  
|[size](#size)|Compte le nombre d'éléments.|  
|[swap](#swap)|Échange le contenu de deux conteneurs.|  
|[classe unordered_multiset](#unordered_multiset)|Construit un objet conteneur.|  
  
|||  
|-|-|  
|Opérateur|Description|  
|[unordered_multiset::operator=](#op_eq)|Copie une table de hachage.|  
  
## <a name="remarks"></a>Notes  
 L’objet trie la séquence qu’il contrôle en appelant deux objets stockés, un objet de fonction de comparaison de type [unordered_multiset::key_equal](#key_equal) et un objet de fonction de hachage de type [unordered_multiset::hasher](#hasher). Pour accéder au premier objet stocké, appelez la fonction membre [unordered_multiset::key_eq](#key_eq)`()`. Pour accéder au second objet stocké, appelez la fonction membre [unordered_multiset::hash_function](#hash)`()`. Pour toutes les valeurs `X` et `Y` de type `Key`, l'appel `key_eq()(X, Y)` retourne true uniquement si les valeurs des deux arguments ont un classement équivalent. L'appel `hash_function()(keyval)` génère une distribution des valeurs de type `size_t`. Contrairement à la classe de modèle [unordered_set](../standard-library/unordered-set-class.md), un objet de classe de modèle `unordered_multiset` ne garantit pas que `key_eq()(X, Y)` a toujours la valeur false pour deux éléments quelconques de la séquence contrôlée. Il n'est pas nécessaire que les clés soient uniques.  
  
 L'objet stocke également un facteur de charge maximale, qui spécifie le nombre moyen maximal d'éléments souhaité par compartiment. Si après l’insertion d’un élément, [unordered_multiset::load_factor](#load_factor)`()` dépasse le facteur de charge maximale, le conteneur augmente le nombre de compartiments et reconstruit la table de hachage si nécessaire.  
  
 L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction de comparaison, de l'ordre d'insertion, du facteur de charge maximale et du nombre de compartiments. En général, il n'est pas possible de prévoir l'ordre des éléments de la séquence contrôlée. Toutefois, vous avez la garantie que tous les sous-ensembles d'éléments dont le classement est équivalent sont adjacents dans la séquence contrôlée.  
  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un objet allocateur stocké de type [unordered_multiset::allocator_type](#allocator_type). Un tel objet allocateur doit avoir la même interface externe qu'un objet de classe de modèle `allocator`. Notez que l'objet allocateur stocké n'est pas copié lorsque l'objet conteneur est assigné.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<unordered_set>  
  
 **Espace de noms :** std  
  
##  <a name="allocator_type"></a>  unordered_multiset::allocator_type  
 Type d’un allocateur pour la gestion du stockage.  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Alloc`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_allocator_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Myset c1;   
  
    Myset::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="begin"></a>  unordered_multiset::begin  
 Désigne le début de la séquence contrôlée ou un compartiment.  
  
```  
iterator begin();

const_iterator begin() const;

 
local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`nbucket`|Numéro de compartiment.|  
  
### <a name="remarks"></a>Notes  
 Les deux premières fonctions membres retournent un itérateur vers l'avant qui pointe vers le premier élément de la séquence (ou juste après la fin d'une séquence vide). Les deux dernières fonctions membres retournent un itérateur vers l'avant qui pointe vers le premier élément du compartiment `nbucket` (ou juste après la fin d'un compartiment vide).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_begin.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect first two items " [c] [b]"   
    Myset::iterator it2 = c1.begin();   
    std::cout << " [" << *it2 << "]";   
    ++it2;   
    std::cout << " [" << *it2 << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[c] [b]  
[a]  
```  
  
##  <a name="bucket"></a>  unordered_multiset::bucket  
 Obtient le numéro du compartiment pour une valeur de clé.  
  
```  
size_type bucket(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 keyval  
 Valeur de clé à mapper.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le numéro de compartiment correspondant actuellement à la valeur de clé `keyval`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Myset::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="bucket_count"></a>  unordered_multiset::bucket_count  
 Obtient le nombre de compartiments.  
  
```  
size_type bucket_count() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre actuel de comportements.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="bucket_size"></a>  unordered_multiset::bucket_size  
 Obtient la taille d’un compartiment.  
  
```  
size_type bucket_size(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `nbucket`  
 Numéro de compartiment.  
  
### <a name="remarks"></a>Notes  
 Les fonctions membres retournent la taille du compartiment numéro `nbucket`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_bucket_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Myset::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="cbegin"></a>  unordered_multiset::cbegin  
 Retourne un itérateur `const` qui traite le premier élément d'une plage.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur forward `const` qui pointe vers le premier élément de la plage, ou vers l'emplacement situé juste après la fin d'une plage vide (pour une plage vide : `cbegin() == cend()`).  
  
### <a name="remarks"></a>Notes  
 Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.  
  
 Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans cet exemple, il est supposé que `Container` est un conteneur modifiable (autre que `const`) de tout type, prenant en charge `begin()` et `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  unordered_multiset::cend  
 Retourne un itérateur `const` qui traite l'emplacement situé immédiatement après le dernier élément d'une plage.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur forward `const` qui pointe juste après la fin de la plage.  
  
### <a name="remarks"></a>Notes  
 `cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.  
  
 Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans cet exemple, `Container` est supposé être un conteneur modifiable (autre que `const`) de type indéfini prenant en charge `end()` et `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 La valeur retournée par `cend` ne doit pas être déréférencée.  
  
##  <a name="clear"></a>  unordered_multiset::clear  
 Supprime tous les éléments.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre appelle [unordered_multiset::erase](#erase)`(` [unordered_multiset::begin](#begin)`(),` [unordered_multiset::end](#end)`())`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_clear.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="const_iterator"></a>  unordered_multiset::const_iterator  
 Type d'un itérateur constant pour la séquence contrôlée.  
  
```  
typedef T1 const_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d'itérateur vers l'avant constant pour la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T1`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_const_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="const_local_iterator"></a>  unordered_multiset::const_local_iterator  
 Type d’un itérateur de compartiment constant pour la séquence contrôlée.  
  
```  
typedef T5 const_local_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d’itérateur de constante vers l’avant pour un compartiment. Il est décrit ici comme un synonyme du type défini par l’implémentation `T5`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_const_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a]  
```  
  
##  <a name="const_pointer"></a>  unordered_multiset::const_pointer  
 Type d'un pointeur constant vers un élément.  
  
```  
typedef Alloc::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir de pointeur constant à un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_const_pointer.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::const_pointer p = &*it;   
        std::cout << " [" << *p << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="const_reference"></a>  unordered_multiset::const_reference  
 Type d'une référence constante à un élément.  
  
```  
typedef Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir de référence constante à un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_const_reference.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::const_reference ref = *it;   
        std::cout << " [" << ref << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="count"></a>  unordered_multiset::count  
 Recherche le nombre d’éléments qui correspondent à une clé spécifiée.  
  
```  
size_type count(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à rechercher.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre d’éléments dans la plage délimitée par [unordered_multiset::equal_range](#equal_range)`(keyval)`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "count('A') == " << c1.count('A') << std::endl;   
    std::cout << "count('b') == " << c1.count('b') << std::endl;   
    std::cout << "count('C') == " << c1.count('C') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
count('A') == 0  
count('b') == 1  
count('C') == 0  
```  
  
##  <a name="difference_type"></a>  unordered_multiset::difference_type  
 Type d'une distance signée entre deux éléments.  
  
```  
typedef T3 difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type d'entier signé décrit un objet qui peut représenter la différence entre les adresses de deux éléments quelconques dans la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T3`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_difference_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    std::cout << "end()-begin() == " << diff << std::endl;   
  
// compute negative difference   
    diff = 0;   
    for (Myset::const_iterator it = c1.end();   
        it != c1.begin(); --it)   
        --diff;   
    std::cout << "begin()-end() == " << diff << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
end()-begin() == 3  
begin()-end() == -3  
```  
  
##  <a name="emplace"></a>  unordered_multiset::emplace  
 Insère un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée).  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`args`|Les arguments transférés pour construire un élément à insérer dans la classe unordered_multiset.|  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur vers l’élément qui vient d’être inséré.  
  
### <a name="remarks"></a>Remarques  
 Aucune référence aux éléments conteneurs n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.  
  
 Durant l’insertion, si une exception est levée mais qu’elle ne se produit pas dans la fonction de hachage du conteneur, le conteneur n’est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini.  
  
 Pour obtenir un exemple de code, consultez [multiset::emplace](../standard-library/multiset-class.md#emplace).  
  
##  <a name="emplace_hint"></a>  unordered_multiset::emplace_hint  
 Insère un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée) avec un indicateur de positionnement.  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`args`|Les arguments transférés pour construire un élément à insérer dans la classe unordered_multiset.|  
|`where`|Indicateur concernant l’emplacement où commencer à rechercher le point d’insertion correct.|  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur vers l’élément qui vient d’être inséré.  
  
### <a name="remarks"></a>Remarques  
 Aucune référence aux éléments conteneurs n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.  
  
 Durant l’insertion, si une exception est levée mais qu’elle ne se produit pas dans la fonction de hachage du conteneur, le conteneur n’est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini.  
  
 Pour obtenir un exemple de code, consultez [set::emplace_hint](../standard-library/set-class.md#emplace_hint).  
  
##  <a name="empty"></a>  unordered_multiset::empty  
 Vérifie l'absence d'éléments.  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la valeur true pour une séquence contrôlée vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_empty.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="end"></a>  unordered_multiset::end  
 Désigne la fin de la séquence contrôlée.  
  
```  
iterator end();
const_iterator end() const;

 
    local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `nbucket`  
 Numéro de compartiment.  
  
### <a name="remarks"></a>Notes  
 Les deux premières fonctions membres retournent un itérateur vers l'avant qui pointe juste après la fin de la séquence. Les deux dernières fonctions membres retournent un itérateur vers l'avant qui pointe juste après la fin du compartiment `nbucket`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_end.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect last two items " [a] [b]"   
    Myset::iterator it2 = c1.end();   
    --it2;   
    std::cout << " [" << *it2 << "]";   
    --it2;   
    std::cout << " [" << *it2 << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));   
    --lit;   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a] [b]  
[a]  
```  
  
##  <a name="equal_range"></a>  unordered_multiset::equal_range  
 Recherche une plage qui correspond à une clé spécifiée.  
  
```  
std::pair<iterator, iterator>  
    equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>  
    equal_range(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à rechercher.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une paire d’itérateurs `X` tel que `[X.first, X.second)` délimite uniquement les éléments de la séquence contrôlée qui ont un classement équivalent à `keyval`. Si aucun de ces éléments n’existe, les deux itérateurs sont `end()`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_equal_range.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// display results of failed search   
    std::pair<Myset::iterator, Myset::iterator> pair1 =   
        c1.equal_range('x');   
    std::cout << "equal_range('x'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << *pair1.first << "]";   
    std::cout << std::endl;   
  
// display results of successful search   
    pair1 = c1.equal_range('b');   
    std::cout << "equal_range('b'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << *pair1.first << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
equal_range('x'):  
equal_range('b'): [b]  
```  
  
##  <a name="erase"></a>  unordered_multiset::erase  
 Supprime un élément ou une plage d’éléments dans une classe unordered_multiset aux positions spécifiées ou supprime les éléments qui correspondent à une clé spécifiée.  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>Paramètres  
 `Where`  
 Position de l’élément à supprimer.  
  
 `First`  
 Position du premier élément à supprimer.  
  
 `Last`  
 Position juste après le dernier élément à supprimer.  
  
 `Key`  
 Valeur de clé des éléments à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour les deux premières fonctions membres, un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un élément à la fin de la classe unordered_multiset si aucun élément de ce type n’existe.  
  
 Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés de la classe unordered_multiset.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir un exemple de code, consultez [set::erase](../standard-library/set-class.md#erase).  
  
##  <a name="find"></a>  unordered_multiset::find  
 Recherche un élément qui correspond à une clé spécifiée.  
  
```  
const_iterator find(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à rechercher.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne [unordered_multiset::equal_range](#equal_range)`(keyval).first`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_find.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// try to find and fail   
    std::cout << "find('A') == "   
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;   
  
// try to find and succeed   
    Myset::iterator it = c1.find('b');   
    std::cout << "find('b') == "   
        << std::boolalpha << (it != c1.end())   
        << ": [" << *it << "]" << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
find('A') == false  
find('b') == true: [b]  
```  
  
##  <a name="get_allocator"></a>  unordered_multiset::get_allocator  
 Obtient l’objet allocateur stocké.  
  
```  
Alloc get_allocator() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne l’objet d’allocateur stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_get_allocator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Myset c1;   
  
    Myset::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="hash"></a>  unordered_multiset::hash_function  
 Obtient l'objet de fonction de hachage stocké.  
  
```  
Hash hash_function() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne l’objet de fonction de hachage stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_hash_function.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="hasher"></a>  unordered_multiset::hasher  
 Type de la fonction de hachage.  
  
```  
typedef Hash hasher;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Hash`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_hasher.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="insert"></a>  unordered_multiset::insert  
 Insère un élément ou une plage d'éléments dans une classe unordered_multiset.  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Val`|Valeur d'un élément à insérer dans la classe unordered_multiset.|  
|`Where`|Emplacement où commencer à rechercher le point d'insertion correct.|  
|`ValTy`|Paramètre de modèle qui spécifie le type d’argument que la classe unordered_multiset peut utiliser pour construire un élément de [value_type](../standard-library/map-class.md#value_type) et effectue un transfert parfait de `Val` comme argument.|  
|`First`|Position du premier élément à copier.|  
|`Last`|Position juste au-delà du dernier élément à copier.|  
|`InputIterator`|Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](../standard-library/map-class.md#value_type).|  
|`IList`|[initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.|  
  
### <a name="return-value"></a>Valeur de retour  
 Les fonctions membres d'insertion à un élément, (1) et (2), retournent un itérateur vers l'emplacement où le nouvel élément a été inséré dans la classe unordered_multiset.  
  
 Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe vers l'emplacement où le nouvel élément a été inséré dans la classe unordered_multiset.  
  
### <a name="remarks"></a>Notes  
 Aucun pointeur ou référence n'est invalidé par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.  
  
 Durant l'insertion d'un seul élément, si une exception est levée mais qu'elle ne se produit pas dans la fonction de hachage du conteneur, l'état du conteneur n'est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.  
  
 L’objet [value_type](../standard-library/map-class.md#value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe set, `unordered_multiset<V>::value_type` est de type `const V`.  
  
 La fonction membre de plage (5) insère la séquence de valeurs d'éléments dans une classe unordered_multiset qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; ainsi, `Last` n'est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `m.insert(v.begin(), v.end());` insère tous les éléments de `v` dans `m`.  
  
 La fonction membre de liste d’initialiseurs (6) utilise un objet [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans l’objet unordered_multiset.  
  
 Pour l’insertion d’un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée), consultez [unordered_multiset::emplace](#emplace) et [unordered_multiset::emplace_hint](#emplace_hint).  
  
 Pour obtenir un exemple de code, consultez [multiset::insert](../standard-library/multiset-class.md#insert).  
  
##  <a name="iterator"></a>  unordered_multiset::iterator  
 Type qui fournit un [itérateur vers l’avant](../standard-library/forward-iterator-tag-struct.md) constant capable de lire des éléments dans une classe unordered_multiset.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple [begin](../standard-library/multiset-class.md#begin) qui illustre comment déclarer et utiliser un **itérateur**.  
  
##  <a name="key_eq"></a>  unordered_multiset::key_eq  
 Obtient l'objet de fonction de comparaison stocké.  
  
```  
Pred key_eq() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne l’objet de fonction de comparaison stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_key_eq.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="key_equal"></a>  unordered_multiset::key_equal  
 Type de la fonction de comparaison.  
  
```  
typedef Pred key_equal;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Pred`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_key_equal.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    Myset::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="key_type"></a>  unordered_multiset::key_type  
 Type d'une clé de tri.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Key`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_key_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Myset::key_type key = 'd';   
    Myset::value_type val = key;   
    c1.insert(val);   
  
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[d] [c] [b] [a]  
```  
  
##  <a name="load_factor"></a>  unordered_multiset::load_factor  
 Compte le nombre moyen d'éléments par compartiment.  
  
```  
float load_factor() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne `(float)`[unordered_multiset::size](#size)`() / (float)`[unordered_multiset::bucket_count](#bucket_count)`()`, le nombre moyen d’éléments par compartiment.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
##  <a name="local_iterator"></a>  unordered_multiset::local_iterator  
 Type d'un itérateur de compartiment.  
  
```  
typedef T4 local_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d'itérateur vers l'avant pour un compartiment. Il est décrit ici comme un synonyme du type défini par l'implémentation `T4`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << *lit << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[a]  
```  
  
##  <a name="max_bucket_count"></a>  unordered_multiset::max_bucket_count  
 Obtient le nombre maximal de compartiments.  
  
```  
size_type max_bucket_count() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre maximal de compartiments actuellement autorisés.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_max_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="max_load_factor"></a>  unordered_multiset::max_load_factor  
 Obtient ou définit le nombre maximal d’éléments par compartiment.  
  
```  
float max_load_factor() const;

 
void max_load_factor(float factor);
```  
  
### <a name="parameters"></a>Paramètres  
 `factor`  
 Nouveau facteur de charge maximale.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre retourne le facteur de charge maximale stockée. La seconde fonction membre retourne le facteur de charge maximale stockée avec `factor`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_max_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="max_size"></a>  unordered_multiset::max_size  
 Obtient ou définit la taille maximale de la séquence contrôlée.  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence la plus longue que l'objet peut contrôler.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_max_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    std::cout << "max_size() == " << c1.max_size() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
max_size() == 4294967295  
```  
  
##  <a name="op_eq"></a>  unordered_multiset::operator=  
 Copie une table de hachage.  
  
```  
unordered_multiset& operator=(const unordered_multiset& right);

unordered_multiset& operator=(unordered_multiset&& right);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`right`|Objet [unordered_multiset](../standard-library/unordered-multiset-class.md) copié dans l’objet `unordered_multiset`.|  
  
### <a name="remarks"></a>Notes  
 Après avoir supprimé les éléments existants dans un objet `unordered_multiset`, `operator=` copie ou déplace le contenu de `right` dans l’objet `unordered_multiset`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// unordered_multiset_operator_as.cpp  
// compile with: /EHsc  
#include <unordered_set>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   unordered_multiset<int> v1, v2, v3;  
   unordered_multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>  unordered_multiset::pointer  
 Type d'un pointeur vers un élément.  
  
```  
typedef Alloc::pointer pointer;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir de pointeur vers un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_pointer.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::key_type key = *it;   
        Myset::pointer p = &key;   
        std::cout << " [" << *p << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="reference"></a>  unordered_multiset::reference  
 Type d'une référence à un élément.  
  
```  
typedef Alloc::reference reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet qui peut servir de référence à un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_reference.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Myset::key_type key = *it;   
        Myset::reference ref = key;   
        std::cout << " [" << ref << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
```  
  
##  <a name="rehash"></a>  unordered_multiset::rehash  
 Régénère la table de hachage.  
  
```  
void rehash(size_type nbuckets);
```  
  
### <a name="parameters"></a>Paramètres  
 `nbuckets`  
 Nombre de compartiments demandés.  
  
### <a name="remarks"></a>Notes  
 La fonction membre modifie le nombre de compartiments pour qu’il soit au moins égal à `nbuckets` et régénère la table de hachage en fonction des besoins.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_rehash.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_load_factor() == 0.1  
```  
  
##  <a name="size"></a>  unordered_multiset::size  
 Compte le nombre d'éléments.  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_size.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert('d');   
    c1.insert('e');   
  
// display contents " [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c] [b] [a]  
size == 0  
empty() == true  
  
 [e] [d]  
size == 2  
empty() == false  
```  
  
##  <a name="size_type"></a>  unordered_multiset::size_type  
 Type d'une distance non signée entre deux éléments.  
  
```  
typedef T2 size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type d'entier non signé décrit un objet qui peut représenter la longueur de n'importe quelle séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T2`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_size_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::size_type sz = c1.size();   
  
    std::cout << "size == " << sz << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
size == 0  
```  
  
##  <a name="swap"></a>  unordered_multiset::swap  
 Échange le contenu de deux conteneurs.  
  
```  
void swap(unordered_multiset& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `right`  
 Conteneur avec lequel faire l’échange.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange les séquences contrôlées entre `*this` et `right`. Si [unordered_multiset::get_allocator](#get_allocator)`() == right.get_allocator()`, elle le fait en un temps constant, elle lève une exception seulement dans le cas de la copie de l’objet traits stocké de type `Tr`, et n’invalide aucune référence, ni aucun pointeur ou itérateur, qui désigne des éléments dans les deux séquences contrôlées. Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_swap.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    Myset c2;   
  
    c2.insert('d');   
    c2.insert('e');   
    c2.insert('f');   
  
    c1.swap(c2);   
  
// display contents " [f] [e] [d]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[f] [e] [d]  
[c] [b] [a]  
```  
  
##  <a name="unordered_multiset"></a>  unordered_multiset::unordered_multiset  
 Construit un objet conteneur.  
  
```  
unordered_multiset(
    const unordered_multiset& Right);

explicit unordered_multiset(
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());

unordered_multiset(
    unordered_multiset&& Right);

unordered_set(
    initializer_list<Type> IList);

unordered_set(
    initializer_list<Typ> IList,  
    size_type Bucket_count);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,   
    const Key& Key);

unordered_set(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,   
    const Key& Key,   
    const Allocator& Al);

template <class InputIterator>  
unordered_multiset(
 InputIterator First,   
    InputIterator Last,  
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`InputIterator`|Type d'itérateur.|  
|`Al`|Objet allocateur à stocker.|  
|`Comp`|Objet de fonction de comparaison à stocker.|  
|`Hash`|Objet de fonction de hachage à stocker.|  
|`Bucket_count`|Nombre minimal de compartiments.|  
|`Right`|Conteneur à copier.|  
|`IList`|initializer_list depuis laquelle effectuer la copie.|  
  
### <a name="remarks"></a>Notes  
 Le premier constructeur spécifie une copie de la séquence contrôlée par `Right`. Le deuxième constructeur spécifie une séquence vide contrôlée. Le troisième constructeur insère la séquence de valeurs d'éléments `[First, Last)`. Le quatrième constructeur spécifie une copie de la séquence en déplaçant `Right`.  
  
 Tous les constructeurs initialisent également plusieurs valeurs stockées. Pour le constructeur de copie, les valeurs sont obtenues à partir de `Right`. Sinon :  
  
 Le nombre minimal de compartiments est l'argument `Bucket_count`, s'il existe ; sinon c'est une valeur par défaut décrite ici comme valeur `N0` définie par l'implémentation.  
  
 L'objet de fonction de hachage est l'argument `Hash`, s'il existe ; sinon c'est `Hash()`.  
  
 L'objet de fonction de comparaison est l'argument `Comp`, s'il existe ; sinon c'est `Comp()`.  
  
 L'objet allocateur est l'argument `Al`, s'il existe ; sinon, c'est `Alloc()`.  
  
##  <a name="value_type"></a>  unordered_multiset::value_type  
 Type d’un élément.  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Ce type décrit un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_set__unordered_multiset_value_type.cpp   
// compile with: /EHsc   
#include <unordered_set>   
#include <iostream>   
  
typedef std::unordered_multiset<char> Myset;   
int main()   
    {   
    Myset c1;   
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
// display contents " [c] [b] [a]"   
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Myset::key_type key = 'd';   
    Myset::value_type val = key;   
    c1.insert(val);   
  
    for (Myset::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << *it << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c] [b] [a]  
[d] [c] [b] [a]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [<unordered_set>](../standard-library/unordered-set.md)   
 [Conteneurs](../cpp/containers-modern-cpp.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)


