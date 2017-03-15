---
title: unordered_map, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_map
- std::unordered_map
- unordered_map/std::unordered_map
- std::unordered_map::allocator_type
- unordered_map/std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_pointer
- std::unordered_map::const_reference
- unordered_map/std::unordered_map::const_reference
- std::unordered_map::difference_type
- unordered_map/std::unordered_map::difference_type
- std::unordered_map::hasher
- unordered_map/std::unordered_map::hasher
- std::unordered_map::iterator
- unordered_map/std::unordered_map::iterator
- std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_equal
- std::unordered_map::key_type
- unordered_map/std::unordered_map::key_type
- std::unordered_map::local_iterator
- unordered_map/std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- unordered_map/std::unordered_map::mapped_type
- std::unordered_map::pointer
- unordered_map/std::unordered_map::pointer
- std::unordered_map::reference
- unordered_map/std::unordered_map::reference
- std::unordered_map::size_type
- unordered_map/std::unordered_map::size_type
- std::unordered_map::value_type
- unordered_map/std::unordered_map::value_type
- std::unordered_map::at
- unordered_map/std::unordered_map::at
- std::unordered_map::begin
- unordered_map/std::unordered_map::begin
- std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket
- std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- unordered_map/std::unordered_map::bucket_size
- std::unordered_map::cbegin
- unordered_map/std::unordered_map::cbegin
- std::unordered_map::cend
- unordered_map/std::unordered_map::cend
- std::unordered_map::clear
- unordered_map/std::unordered_map::clear
- std::unordered_map::count
- unordered_map/std::unordered_map::count
- std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace
- std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::emplace_hint
- std::unordered_map::empty
- unordered_map/std::unordered_map::empty
- std::unordered_map::end
- unordered_map/std::unordered_map::end
- std::unordered_map::equal_range
- unordered_map/std::unordered_map::equal_range
- std::unordered_map::erase
- unordered_map/std::unordered_map::erase
- std::unordered_map::find
- unordered_map/std::unordered_map::find
- std::unordered_map::get_allocator
- unordered_map/std::unordered_map::get_allocator
- std::unordered_map::hash_function
- unordered_map/std::unordered_map::hash_function
- std::unordered_map::insert
- unordered_map/std::unordered_map::insert
- std::unordered_map::key_eq
- unordered_map/std::unordered_map::key_eq
- std::unordered_map::load_factor
- unordered_map/std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_load_factor
- std::unordered_map::max_size
- unordered_map/std::unordered_map::max_size
- std::unordered_map::rehash
- unordered_map/std::unordered_map::rehash
- std::unordered_map::size
- unordered_map/std::unordered_map::size
- std::unordered_map::swap
- unordered_map/std::unordered_map::swap
- std::unordered_map::unordered_map
- unordered_map/std::unordered_map::unordered_map
dev_langs:
- C++
helpviewer_keywords:
- unordered_map class
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 82ef90b457ea875cc9237ad4aae73202c13ad4ea
ms.lasthandoff: 02/24/2017

---
# <a name="unorderedmap-class"></a>unordered_map, classe
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable constituée d'éléments de type `std::pair<const Key, Ty>`. La séquence est triée par ordre faible avec une fonction de hachage, qui partitionne la séquence en un ensemble trié de sous-séquences appelées compartiments. Dans chaque compartiment, une fonction de comparaison détermine si des paires d'éléments possèdent un ordre équivalent. Chaque élément stocke deux objets, une clé de tri et une valeur. La séquence est représentée de façon à permettre la recherche, l'insertion et la suppression d'un élément arbitraire à l'aide d'un certain nombre d'opérations qui peut être indépendant du nombre d'éléments de la séquence (temps constant), du moins lorsque les compartiments sont de longueur à peu près équivalente. Dans le pire des cas, lorsque tous les éléments se trouvent dans un compartiment, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (temps linéaire). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Key,  
    class Ty,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<std::pair<const Key, Ty>>>  
class unordered_map;  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Key`|Type de clé.|  
|`Ty`|Type mappé.|  
|`Hash`|Type d’objet de la fonction de hachage.|  
|`Pred`|Type d’objet de fonction de comparaison d’égalité.|  
|`Alloc`|Classe allocator.|  
  
## <a name="members"></a>Membres  
  
|||  
|-|-|  
|Définition de types|Description|  
|[unordered_map::allocator_type](#unordered_map__allocator_type)|Type d’un allocateur pour la gestion du stockage.|  
|[unordered_map::const_iterator](#unordered_map__const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[unordered_map::const_local_iterator](#unordered_map__const_local_iterator)|Type d’un itérateur de compartiment constant pour la séquence contrôlée.|  
|[unordered_map::const_pointer](#unordered_map__const_pointer)|Type d'un pointeur constant vers un élément.|  
|[unordered_map::const_reference](#unordered_map__const_reference)|Type d'une référence constante à un élément.|  
|[unordered_map::difference_type](#unordered_map__difference_type)|Type d'une distance signée entre deux éléments.|  
|[unordered_map::hasher](#unordered_map__hasher)|Type de la fonction de hachage.|  
|[unordered_map::iterator](#unordered_map__iterator)|Type d'un itérateur pour la séquence contrôlée.|  
|[unordered_map::key_equal](#unordered_map__key_equal)|Type de la fonction de comparaison.|  
|[unordered_map::key_type](#unordered_map__key_type)|Type d'une clé de tri.|  
|[unordered_map::local_iterator](#unordered_map__local_iterator)|Type d'un itérateur de compartiment pour la séquence contrôlée.|  
|[unordered_map::mapped_type](#unordered_map__mapped_type)|Type d'une valeur mappée associée à chaque clé.|  
|[unordered_map::pointer](#unordered_map__pointer)|Type d'un pointeur vers un élément.|  
|[unordered_map::reference](#unordered_map__reference)|Type d'une référence à un élément.|  
|[unordered_map::size_type](#unordered_map__size_type)|Type d'une distance non signée entre deux éléments.|  
|[unordered_map::value_type](#unordered_map__value_type)|Type d’un élément.|  
  
|||  
|-|-|  
|Fonction membre|Description|  
|[unordered_map::at](#unordered_map__at)|Recherche un élément avec la clé spécifiée.|  
|[unordered_map::begin](#unordered_map__begin)|Désigne le début de la séquence contrôlée.|  
|[unordered_map::bucket](#unordered_map__bucket)|Obtient le numéro du compartiment pour une valeur de clé.|  
|[unordered_map::bucket_count](#unordered_map__bucket_count)|Obtient le nombre de compartiments.|  
|[unordered_map::bucket_size](#unordered_map__bucket_size)|Obtient la taille d'un compartiment.|  
|[unordered_map::cbegin](#unordered_map__cbegin)|Désigne le début de la séquence contrôlée.|  
|[unordered_map::cend](#unordered_map__cend)|Désigne la fin de la séquence contrôlée.|  
|[unordered_map::clear](#unordered_map__clear)|Supprime tous les éléments.|  
|[unordered_map::count](#unordered_map__count)|Recherche le nombre d’éléments qui correspondent à une clé spécifiée.|  
|[unordered_map::emplace](#unordered_map__emplace)|Ajoute un élément construit sur place.|  
|[unordered_map::emplace_hint](#unordered_map__emplace_hint)|Ajoute un élément construit sur place, avec un indicateur.|  
|[unordered_map::empty](#unordered_map__empty)|Vérifie l'absence d'éléments.|  
|[unordered_map::end](#unordered_map__end)|Désigne la fin de la séquence contrôlée.|  
|[unordered_map::equal_range](#unordered_map__equal_range)|Recherche une plage qui correspond à une clé spécifiée.|  
|[unordered_map::erase](#unordered_map__erase)|Supprime les éléments placés aux positions spécifiées.|  
|[unordered_map::find](#unordered_map__find)|Recherche un élément qui correspond à une clé spécifiée.|  
|[unordered_map::get_allocator](#unordered_map__get_allocator)|Obtient l’objet allocateur stocké.|  
|[unordered_map::hash_function](#unordered_map__hash_function)|Obtient l'objet de fonction de hachage stocké.|  
|[unordered_map::insert](#unordered_map__insert)|Ajoute des éléments.|  
|[unordered_map::key_eq](#unordered_map__key_eq)|Obtient l'objet de fonction de comparaison stocké.|  
|[unordered_map::load_factor](#unordered_map__load_factor)|Compte le nombre moyen d'éléments par compartiment.|  
|[unordered_map::max_bucket_count](#unordered_map__max_bucket_count)|Obtient le nombre maximal de compartiments.|  
|[unordered_map::max_load_factor](#unordered_map__max_load_factor)|Obtient ou définit le nombre maximal d’éléments par compartiment.|  
|[unordered_map::max_size](#unordered_map__max_size)|Obtient ou définit la taille maximale de la séquence contrôlée.|  
|[unordered_map::rehash](#unordered_map__rehash)|Régénère la table de hachage.|  
|[unordered_map::size](#unordered_map__size)|Compte le nombre d'éléments.|  
|[unordered_map::swap](#unordered_map__swap)|Échange le contenu de deux conteneurs.|  
|[unordered_map::unordered_map](#unordered_map__unordered_map)|Construit un objet conteneur.|  
  
|||  
|-|-|  
|Opérateur|Description|  
|[unordered_map::operator[]](#unordered_map__operator_at)|Recherche ou insère un élément avec la clé spécifiée.|  
|[unordered_map::operator=](#unordered_map__operator_eq)|Copie une table de hachage.|  
  
## <a name="remarks"></a>Notes  
 L’objet trie la séquence qu’il contrôle en appelant deux objets stockés, un objet de fonction de comparaison de type [unordered_map::key_equal](#unordered_map__key_equal) et un objet de fonction de hachage de type [unordered_map::hasher](#unordered_map__hasher). Pour accéder au premier objet stocké, appelez la fonction membre [unordered_map::key_eq](#unordered_map__key_eq)`()`. Pour accéder au second objet stocké, appelez la fonction membre [unordered_map::hash_function](#unordered_map__hash_function)`()`. Pour toutes les valeurs `X` et `Y` de type `Key`, l'appel `key_eq()(X, Y)` retourne true uniquement si les valeurs des deux arguments ont un classement équivalent. L'appel `hash_function()(keyval)` génère une distribution des valeurs de type `size_t`. Contrairement à la classe de modèle [unordered_multimap](../standard-library/unordered-multimap-class.md), un objet de classe de modèle `unordered_map` garantit que `key_eq()(X, Y)` a toujours la valeur false pour deux éléments quelconques de la séquence contrôlée. Les clés sont uniques.  
  
 L'objet stocke également un facteur de charge maximale, qui spécifie le nombre moyen maximal d'éléments souhaité par compartiment. Si après l’insertion d’un élément, [unordered_map::load_factor](#unordered_map__load_factor)`()` dépasse le facteur de charge maximale, le conteneur augmente le nombre de compartiments et reconstruit la table de hachage si nécessaire.  
  
 L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction de comparaison, de l'ordre d'insertion, du facteur de charge maximale et du nombre de compartiments. En général, il n'est pas possible de prévoir l'ordre des éléments de la séquence contrôlée. Toutefois, vous avez la garantie que tous les sous-ensembles d'éléments dont le classement est équivalent sont adjacents dans la séquence contrôlée.  
  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un objet allocateur stocké de type [unordered_map::allocator_type](#unordered_map__allocator_type). Un tel objet allocateur doit avoir la même interface externe qu'un objet de classe de modèle `allocator`. Notez que l'objet allocateur stocké n'est pas copié lorsque l'objet conteneur est assigné.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<unordered_map>  
  
 **Espace de noms :** std  
  
##  <a name="a-nameunorderedmapallocatortypea--unorderedmapallocatortype"></a><a name="unordered_map__allocator_type"></a>  unordered_map::allocator_type  
 Type d’un allocateur pour la gestion du stockage.  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Alloc`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_allocator_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="a-nameunorderedmapata--unorderedmapat"></a><a name="unordered_map__at"></a>  unordered_map::at  
 Recherche un élément dans un unordered_map avec une valeur de clé spécifiée.  
  
```  
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|` key`|Valeur de clé à rechercher.|  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à la valeur de données de l'élément trouvé.  
  
### <a name="remarks"></a>Notes  
 Si la valeur de clé de l'argument est introuvable, la fonction lève un objet de classe `out_of_range`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// unordered_map_at.cpp  
// compile with: /EHsc  
#include <unordered_map>  
#include <iostream>  
  
typedef std::unordered_map<char, int> Mymap;   
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements  
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}  
```  
  
##  <a name="a-nameunorderedmapbegina--unorderedmapbegin"></a><a name="unordered_map__begin"></a>  unordered_map::begin  
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
// std__unordered_map__unordered_map_begin.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
#typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"   
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[c, 3] [b, 2]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmapbucketa--unorderedmapbucket"></a><a name="unordered_map__bucket"></a>  unordered_map::bucket  
 Obtient le numéro du compartiment pour une valeur de clé.  
  
```  
size_type bucket(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à mapper.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le numéro de compartiment correspondant actuellement à la valeur de clé `keyval`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_bucket.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys   
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="a-nameunorderedmapbucketcounta--unorderedmapbucketcount"></a><a name="unordered_map__bucket_count"></a>  unordered_map::bucket_count  
 Obtient le nombre de compartiments.  
  
```  
size_type bucket_count() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre actuel de comportements.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3][b, 2][a, 1]
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
  
##  <a name="a-nameunorderedmapbucketsizea--unorderedmapbucketsize"></a><a name="unordered_map__bucket_size"></a>  unordered_map::bucket_size  
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
// std__unordered_map__unordered_map_bucket_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys   
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="a-nameunorderedmapcbegina--unorderedmapcbegin"></a><a name="unordered_map__cbegin"></a>  unordered_map::cbegin  
 Retourne un itérateur `const` qui traite le premier élément d'une plage.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur forward `const` qui pointe vers le premier élément de la plage, ou vers l'emplacement situé juste après la fin d'une plage vide (pour une plage vide : `cbegin() == cend()`).  
  
### <a name="remarks"></a>Notes  
 Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.  
  
 Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement au mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans cet exemple, il est supposé que `Container` est un conteneur modifiable (autre que `const`) de tout type, prenant en charge `begin()` et `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-nameunorderedmapcenda--unorderedmapcend"></a><a name="unordered_map__cend"></a>  unordered_map::cend  
 Retourne un itérateur `const` qui traite l'emplacement situé immédiatement après le dernier élément d'une plage.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur forward `const` qui pointe juste après la fin de la plage.  
  
### <a name="remarks"></a>Notes  
 `cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.  
  
 Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement au mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans cet exemple, il est supposé que `Container` est un conteneur modifiable (autre que `const`) de tout type prenant en charge `end()` et `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator  
```  
  
 La valeur retournée par `cend` ne doit pas être déréférencée.  
  
##  <a name="a-nameunorderedmapcleara--unorderedmapclear"></a><a name="unordered_map__clear"></a>  unordered_map::clear  
 Supprime tous les éléments.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre appelle [unordered_map::erase](#unordered_map__erase)`(` [unordered_map::begin](#unordered_map__begin)`(),` [unordered_map::end](#unordered_map__end)`())`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_clear.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect   
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="a-nameunorderedmapconstiteratora--unorderedmapconstiterator"></a><a name="unordered_map__const_iterator"></a>  unordered_map::const_iterator  
 Type d'un itérateur constant pour la séquence contrôlée.  
  
```  
typedef T1 const_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d'itérateur vers l'avant constant pour la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T1`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_const_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapconstlocaliteratora--unorderedmapconstlocaliterator"></a><a name="unordered_map__const_local_iterator"></a>  unordered_map::const_local_iterator  
 Type d’un itérateur de compartiment constant pour la séquence contrôlée.  
  
```  
typedef T5 const_local_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d’itérateur de constante vers l’avant pour un compartiment. Il est décrit ici comme un synonyme du type défini par l’implémentation `T5`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_const_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmapconstpointera--unorderedmapconstpointer"></a><a name="unordered_map__const_pointer"></a>  unordered_map::const_pointer  
 Type d'un pointeur constant vers un élément.  
  
```  
typedef Alloc::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir de pointeur constant à un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_const_pointer.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapconstreferencea--unorderedmapconstreference"></a><a name="unordered_map__const_reference"></a>  unordered_map::const_reference  
 Type d'une référence constante à un élément.  
  
```  
typedef Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir de référence constante à un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_const_reference.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}

```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapcounta--unorderedmapcount"></a><a name="unordered_map__count"></a>  unordered_map::count  
 Recherche le nombre d’éléments qui correspondent à une clé spécifiée.  
  
```  
size_type count(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à rechercher.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre d’éléments dans la plage délimitée par [unordered_map::equal_range](#unordered_map__equal_range)`(keyval)`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}

```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
count('A') == 0  
count('b') == 1  
count('C') == 0  
```  
  
##  <a name="a-nameunorderedmapdifferencetypea--unorderedmapdifferencetype"></a><a name="unordered_map__difference_type"></a>  unordered_map::difference_type  
 Type d'une distance signée entre deux éléments.  
  
```  
typedef T3 difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type d'entier signé décrit un objet qui peut représenter la différence entre les adresses de deux éléments quelconques dans la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T3`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_difference_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference   
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference   
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
end()-begin() == 3  
begin()-end() == -3  
```  
  
##  <a name="a-nameunorderedmapemplacea--unorderedmapemplace"></a><a name="unordered_map__emplace"></a>  unordered_map::emplace  
 Insère un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée) dans un objet unordered_map.  
  
```  
template <class... Args>  
pair<iterator, bool>  emplace( Args&&... args);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`args`|Arguments transférés pour construire un élément à insérer dans la classe unordered_map, sauf si elle contient déjà un élément dont la valeur est ordonnée de façon équivalente.|  
  
### <a name="return-value"></a>Valeur de retour  
 Un objet `pair` dont le composant `bool` retourne true si une insertion a été effectuée et false si la classe `unordered_map` contenait déjà un élément dont la clé avait une valeur équivalente dans le classement, et dont le composant itérateur retourne l’adresse où un nouvel élément a été inséré ou l’emplacement où l’élément se trouvait déjà.  
  
 Pour accéder au composant itérateur d’une paire `pr` retournée par cette fonction membre, utilisez `pr.first` et, pour le déréférencer, utilisez `*(pr.first)`. Pour accéder au composant `bool` d’une paire `pr` retournée par cette fonction membre, utilisez `pr.second`.  
  
### <a name="remarks"></a>Notes  
 Aucun itérateur ni aucune référence ne sont invalidés par cette fonction.  
  
 Durant l’insertion, si une exception est levée mais qu’elle ne se produit pas dans la fonction de hachage du conteneur, le conteneur n’est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini.  
  
 Pour obtenir un exemple de code, consultez [map::emplace](../standard-library/map-class.md#map__emplace).  
  
##  <a name="a-nameunorderedmapemplacehinta--unorderedmapemplacehint"></a><a name="unordered_map__emplace_hint"></a>  unordered_map::emplace_hint  
 Insère un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée) avec un indicateur de positionnement.  
  
```  
template <class... Args>  
iterator emplace_hint(const_iterator where, Args&&... args);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`args`|Arguments transférés pour construire un élément à insérer dans la classe unordered_map, sauf si celle-ci contient déjà cet élément ou, plus généralement, si elle contient déjà un élément dont la clé est ordonnée de façon équivalente.|  
|`where`|Indicateur concernant l’emplacement où commencer à rechercher le point d’insertion correct.|  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur vers le nouvel élément inséré.  
  
 Si l’insertion a échoué parce que l’élément existe déjà, retourne un itérateur vers l’élément existant.  
  
### <a name="remarks"></a>Notes  
 Aucune référence n’est invalidée par cette fonction.  
  
 Durant l’insertion, si une exception est levée mais qu’elle ne se produit pas dans la fonction de hachage du conteneur, le conteneur n’est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini.  
  
 Le [value_type](../standard-library/map-class.md#map__value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.  
  
 Pour obtenir un exemple de code, consultez [map::emplace_hint](../standard-library/map-class.md#map__emplace_hint).  
  
##  <a name="a-nameunorderedmapemptya--unorderedmapempty"></a><a name="unordered_map__empty"></a>  unordered_map::empty  
 Vérifie l'absence d'éléments.  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la valeur true pour une séquence contrôlée vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_empty.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect   
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="a-nameunorderedmapenda--unorderedmapend"></a><a name="unordered_map__end"></a>  unordered_map::end  
 Désigne la fin de la séquence contrôlée.  
  
```  
iterator end();
const_iterator end() const; 
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`nbucket`|Numéro de compartiment.|  
  
### <a name="remarks"></a>Notes  
 Les deux premières fonctions membres retournent un itérateur vers l'avant qui pointe juste après la fin de la séquence. Les deux dernières fonctions membres retournent un itérateur vers l'avant qui pointe juste après la fin du compartiment `nbucket`.  
  
##  <a name="a-nameunorderedmapequalrangea--unorderedmapequalrange"></a><a name="unordered_map__equal_range"></a>  unordered_map::equal_range  
 Recherche une plage qui correspond à une clé spécifiée.  
  
```  
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à rechercher.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne une paire d’itérateurs `X` tel que `[X.first, X.second)` délimite uniquement les éléments de la séquence contrôlée qui ont un classement équivalent à `keyval`. Si aucun de ces éléments n’existe, les deux itérateurs sont `end()`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_equal_range.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search   
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search   
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}

```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
equal_range('x'):  
equal_range('b'): [b, 2]  
```  
  
##  <a name="a-nameunorderedmaperasea--unorderedmaperase"></a><a name="unordered_map__erase"></a>  unordered_map::erase  
 Supprime un élément ou une plage d’éléments dans une classe unordered_map aux positions spécifiées ou supprime les éléments qui correspondent à une clé spécifiée.  
  
```  
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
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
 Pour les deux premières fonctions membres, un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un élément à la fin de la classe map si aucun élément de ce type n’existe.  
  
 Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés de la classe unordered_map.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir un exemple de code, consultez [map::erase](../standard-library/map-class.md#map__erase).  
  
##  <a name="a-nameunorderedmapfinda--unorderedmapfind"></a><a name="unordered_map__find"></a>  unordered_map::find  
 Recherche un élément qui correspond à une clé spécifiée.  
  
```  
const_iterator find(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `keyval`  
 Valeur de clé à rechercher.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne [unordered_map::equal_range](#unordered_map__equal_range)`(keyval).first`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_find.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail   
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed   
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}

```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
find('A') == false  
find('b') == true: [b, 2]  
```  
  
##  <a name="a-nameunorderedmapgetallocatora--unorderedmapgetallocator"></a><a name="unordered_map__get_allocator"></a>  unordered_map::get_allocator  
 Obtient l’objet allocateur stocké.  
  
```  
Alloc get_allocator() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne l’objet d’allocateur stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_get_allocator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}

```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="a-nameunorderedmaphashfunctiona--unorderedmaphashfunction"></a><a name="unordered_map__hash_function"></a>  unordered_map::hash_function  
 Obtient l'objet de fonction de hachage stocké.  
  
```  
Hash hash_function() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne l’objet de fonction de hachage stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_hash_function.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="a-nameunorderedmaphashera--unorderedmaphasher"></a><a name="unordered_map__hasher"></a>  unordered_map::hasher  
 Type de la fonction de hachage.  
  
```  
typedef Hash hasher;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Hash`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_hasher.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}

```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="a-nameunorderedmapinserta--unorderedmapinsert"></a><a name="unordered_map__insert"></a>  unordered_map::insert  
 Insère un élément ou une plage d'éléments dans une classe unordered_map.  
  
```  
// (1) single element  
pair<iterator, bool> insert(    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Val`|Valeur d'un élément à insérer dans la classe unordered_map sauf si elle contient déjà un élément dont la clé est classée de manière équivalente.|  
|`Where`|Emplacement où commencer à rechercher le point d'insertion correct.|  
|`ValTy`|Paramètre de modèle qui spécifie le type d’argument que la classe unordered_map peut utiliser pour construire un élément de [value_type](../standard-library/map-class.md#map__value_type) et effectue un transfert parfait de `Val` comme argument.|  
|`First`|Position du premier élément à copier.|  
|`Last`|Position juste au-delà du dernier élément à copier.|  
|`InputIterator`|Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](../standard-library/map-class.md#map__value_type).|  
|`IList`|[initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.|  
  
### <a name="return-value"></a>Valeur de retour  
 Les fonctions membres à un élément, (1) et (2), retournent une [paire](../standard-library/pair-structure.md) dont le composant `bool` a la valeur true si une insertion a été effectuée, et false si la classe unordered_map contenait déjà un élément dont la clé avait une valeur équivalente dans le classement. Le composant itérateur de la paire de valeurs de retour pointe sur l'élément nouvellement inséré si le composant `bool` a la valeur true ou sur l'élément existant si le composant `bool` a la valeur false.  
  
 Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe sur la position où le nouvel élément a été inséré dans la classe unordered_map ou, si un élément avec une clé équivalente existe déjà, sur l'élément existant.  
  
### <a name="remarks"></a>Notes  
 Aucun itérateur, pointeur ou référence n'est invalidé par cette fonction.  
  
 Durant l'insertion d'un seul élément, si une exception est levée mais qu'elle ne se produit pas dans la fonction de hachage du conteneur, l'état du conteneur n'est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.  
  
 Pour accéder au composant itérateur d’un objet `pair``pr` retourné par les fonctions membres à un élément, utilisez `pr.first`. Pour déréférencer l’itérateur dans la paire retournée, utilisez `*pr.first`, qui vous donne un élément. Pour accéder au composant `bool`, utilisez `pr.second`. Pour obtenir un exemple, voir l'exemple de code plus loin dans cet article.  
  
 Le [value_type](../standard-library/map-class.md#map__value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe map, `map<K, V>::value_type` est `pair<const K, V>`. La valeur d'un élément est une paire ordonnée dans laquelle le premier composant est égal à la valeur de clé et le second composant est égal à la valeur de données de l'élément.  
  
 La fonction membre de plage (5) insère la séquence de valeurs d'éléments dans une classe unordered_map qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; ainsi, `Last` n'est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `m.insert(v.begin(), v.end());` tente d'insérer tous les éléments de `v` dans `m`. Seuls les éléments qui ont des valeurs uniques dans la plage sont insérés. Les doublons sont ignorés. Pour savoir quels éléments sont rejetés, utilisez les versions à un élément de `insert`.  
  
 La fonction membre de liste d’initialiseurs (6) utilise un objet [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans l’objet unordered_map.  
  
 Pour l’insertion d’un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée), consultez [unordered_map::emplace](#unordered_map__emplace) et [unordered_map::emplace_hint](#unordered_map__emplace_hint).  
  
 Pour obtenir un exemple de code, consultez [map::insert](../standard-library/map-class.md#map__insert).  
  
##  <a name="a-nameunorderedmapiteratora--unorderedmapiterator"></a><a name="unordered_map__iterator"></a>  unordered_map::iterator  
 Type d'un itérateur pour la séquence contrôlée.  
  
```  
typedef T0 iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d’itérateur forward pour la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T0`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapkeyeqa--unorderedmapkeyeq"></a><a name="unordered_map__key_eq"></a>  unordered_map::key_eq  
 Obtient l'objet de fonction de comparaison stocké.  
  
```  
Pred key_eq() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne l’objet de fonction de comparaison stocké.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_key_eq.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::key_equal cmpfn = c1.key_eq();   
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
  
##  <a name="a-nameunorderedmapkeyequala--unorderedmapkeyequal"></a><a name="unordered_map__key_equal"></a>  unordered_map::key_equal  
 Type de la fonction de comparaison.  
  
```  
typedef Pred key_equal;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Pred`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_key_equal.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::key_equal cmpfn = c1.key_eq();   
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
  
##  <a name="a-nameunorderedmapkeytypea--unorderedmapkeytype"></a><a name="unordered_map__key_type"></a>  unordered_map::key_type  
 Type d'une clé de tri.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Key`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_key_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmaploadfactora--unorderedmaploadfactor"></a><a name="unordered_map__load_factor"></a>  unordered_map::load_factor  
 Compte le nombre moyen d'éléments par compartiment.  
  
```  
float load_factor() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne `(float)`[unordered_map::size](#unordered_map__size)`() / (float)`[unordered_map::bucket_count](#unordered_map__bucket_count)`()`, le nombre moyen d’éléments par compartiment.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="a-nameunorderedmaplocaliteratora--unorderedmaplocaliterator"></a><a name="unordered_map__local_iterator"></a>  unordered_map::local_iterator  
 Type d'un itérateur de compartiment.  
  
```  
typedef T4 local_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir d'itérateur vers l'avant pour un compartiment. Il est décrit ici comme un synonyme du type défini par l'implémentation `T4`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << lit->first << ", " << lit->second << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmapmappedtypea--unorderedmapmappedtype"></a><a name="unordered_map__mapped_type"></a>  unordered_map::mapped_type  
 Type d'une valeur mappée associée à chaque clé.  
  
```  
typedef Ty mapped_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle `Ty`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_mapped_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapmaxbucketcounta--unorderedmapmaxbucketcount"></a><a name="unordered_map__max_bucket_count"></a>  unordered_map::max_bucket_count  
 Obtient le nombre maximal de compartiments.  
  
```  
size_type max_bucket_count() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre maximal de compartiments actuellement autorisés.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_max_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="a-nameunorderedmapmaxloadfactora--unorderedmapmaxloadfactor"></a><a name="unordered_map__max_load_factor"></a>  unordered_map::max_load_factor  
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
// std__unordered_map__unordered_map_max_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="a-nameunorderedmapmaxsizea--unorderedmapmaxsize"></a><a name="unordered_map__max_size"></a>  unordered_map::max_size  
 Obtient ou définit la taille maximale de la séquence contrôlée.  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence la plus longue que l'objet peut contrôler.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_max_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    std::cout << "max_size() == " << c1.max_size() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
max_size() == 536870911  
```  
  
##  <a name="a-nameunorderedmapoperatorata--unorderedmapoperator"></a><a name="unordered_map__operator_at"></a>  unordered_map::operator[]  
 Recherche ou insère un élément avec la clé spécifiée.  
  
```  
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Keyval`|Valeur de clé à rechercher ou à insérer.|  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à la valeur de données de l'élément inséré.  
  
### <a name="remarks"></a>Notes  
 Si la valeur de clé d’argument est introuvable, elle est insérée avec la valeur par défaut du type de données.  
  
 `operator[]` peut être utilisé pour insérer des éléments dans un objet map *m* en utilisant *m*[_ *Key*] = `DataValue` ; où `DataValue` est la valeur du `mapped_type` de l’élément avec une valeur de clé de \_ *Key*.  
  
 Lorsque vous utilisez `operator[]` pour insérer des éléments, la référence retournée n'indique pas si l'insertion va modifier un élément existant ou en créer un nouveau. Les fonctions membres [find](../standard-library/map-class.md#map__find) et [insert](../standard-library/map-class.md#map__insert) peuvent être utilisées pour déterminer si un élément avec une clé spécifiée est déjà présent avant une insertion.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_operator_sub.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
#include <string>  
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// try to find and fail   
    std::cout << "c1['A'] == " << c1['A'] << std::endl;   
  
// try to find and succeed   
    std::cout << "c1['a'] == " << c1['a'] << std::endl;   
  
// redisplay contents   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// insert by moving key  
    std::unordered_map<string, int> c2;  
    std::string str("abc");  
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;  
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;  
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
c1['A'] == 0  
c1['a'] == 1  
 [c, 3] [b, 2] [A, 0] [a, 1]  
c2[move(str)] == 0  
c2["abc"] == 1  
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre détermine l’itérateur `where` comme valeur de retour de [unordered_map::insert](#unordered_map__insert)`(` [unordered_map::value_type](#unordered_map__value_type)`(keyval, Ty())`. (Elle insère un élément avec la clé spécifiée si aucun élément de ce type n'existe). Elle retourne ensuite une référence à `(*where).second`.  
  
##  <a name="a-nameunorderedmapoperatoreqa--unorderedmapoperator"></a><a name="unordered_map__operator_eq"></a>  unordered_map::operator=  
 Remplace les éléments de ce unordered_map à l’aide des éléments provenant d’un autre unordered_map.  
  
```  
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|` right`|unordered_map dont la fonction opérateur assigne le contenu.|  
  
### <a name="remarks"></a>Notes  
 La première version copie tous les éléments de ` right` vers cet objet unordered_map.  
  
 La seconde version déplace tous les éléments de ` right` vers cet objet unordered_map.  
  
 Les éléments qui se trouvent dans ce unordered_map avant l’exécution de `operator`= sont ignorés.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// unordered_map_operator_as.cpp  
// compile with: /EHsc  
#include <unordered_map>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   unordered_map<int, int> v1, v2, v3;  
   unordered_map<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="a-nameunorderedmappointera--unorderedmappointer"></a><a name="unordered_map__pointer"></a>  unordered_map::pointer  
 Type d'un pointeur vers un élément.  
  
```  
typedef Alloc::pointer pointer;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet pouvant servir de pointeur vers un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_pointer.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::pointer p = &*it;   
        std::cout << " [" << p->first << ", " << p->second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapreferencea--unorderedmapreference"></a><a name="unordered_map__reference"></a>  unordered_map::reference  
 Type d'une référence à un élément.  
  
```  
typedef Alloc::reference reference;  
```  
  
### <a name="remarks"></a>Notes  
 Le type décrit un objet qui peut servir de référence à un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_reference.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::reference ref = *it;   
        std::cout << " [" << ref.first << ", " << ref.second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmaprehasha--unorderedmaprehash"></a><a name="unordered_map__rehash"></a>  unordered_map::rehash  
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
// std__unordered_map__unordered_map_rehash.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="a-nameunorderedmapsizea--unorderedmapsize"></a><a name="unordered_map__size"></a>  unordered_map::size  
 Compte le nombre d'éléments.  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne la longueur de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert(Mymap::value_type('d', 4));   
    c1.insert(Mymap::value_type('e', 5));   
  
// display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="a-nameunorderedmapsizetypea--unorderedmapsizetype"></a><a name="unordered_map__size_type"></a>  unordered_map::size_type  
 Type d'une distance non signée entre deux éléments.  
  
```  
typedef T2 size_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type d'entier non signé décrit un objet qui peut représenter la longueur de n'importe quelle séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T2`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_size_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::size_type sz = c1.size();   
  
    std::cout << "size == " << sz << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
size == 0  
```  
  
##  <a name="a-nameunorderedmapswapa--unorderedmapswap"></a><a name="unordered_map__swap"></a>  unordered_map::swap  
 Échange le contenu de deux conteneurs.  
  
```  
void swap(unordered_map& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `right`  
 Conteneur avec lequel faire l’échange.  
  
### <a name="remarks"></a>Notes  
 La fonction membre échange les séquences contrôlées entre `*this` et `right`. Si [unordered_map::get_allocator](#unordered_map__get_allocator)`() == right.get_allocator()`, elle le fait en un temps constant, elle lève une exception seulement dans le cas de la copie de l’objet traits stocké de type `Tr`, et n’invalide aucune référence, ni aucun pointeur ou itérateur, qui désigne des éléments dans les deux séquences contrôlées. Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    Mymap c2;   
  
    c2.insert(Mymap::value_type('d', 4));   
    c2.insert(Mymap::value_type('e', 5));   
    c2.insert(Mymap::value_type('f', 6));   
  
    c1.swap(c2);   
  
// display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmapunorderedmapa--unorderedmapunorderedmap"></a><a name="unordered_map__unordered_map"></a>  unordered_map::unordered_map  
 Construit un objet conteneur.  
  
```  
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,  
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,   
    size_type Bucket_count,  
    const Hash& Hash,  
    KeyEqual& Equal  
    const Allocator& Al);

template <class InIt>  
unordered_map(
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
|`Al`|Objet allocateur à stocker.|  
|`Comp`|Objet de fonction de comparaison à stocker.|  
|`Hash`|Objet de fonction de hachage à stocker.|  
|`Bucket_count`|Nombre minimal de compartiments.|  
|`Right`|Conteneur à copier.|  
|`First`||  
|`Last`||  
|`IList`|initializer_list qui contient les éléments à copier.|  
  
### <a name="remarks"></a>Notes  
 Le premier constructeur spécifie une copie de la séquence contrôlée par `right`. Le deuxième constructeur spécifie une séquence vide contrôlée. Le troisième constructeur insère la séquence de valeurs d'éléments `[first, last)`. Le quatrième constructeur spécifie une copie de la séquence en déplaçant `right`.  
  
 Tous les constructeurs initialisent également plusieurs valeurs stockées. Pour le constructeur de copie, les valeurs sont obtenues à partir de `Right`. Sinon :  
  
 Le nombre minimal de compartiments est l'argument `Bucket_count`, s'il existe ; sinon c'est une valeur par défaut décrite ici comme valeur `N0` définie par l'implémentation.  
  
 L'objet de fonction de hachage est l'argument `Hash`, s'il existe ; sinon c'est `Hash()`.  
  
 L'objet de fonction de comparaison est l'argument `Comp`, s'il existe ; sinon c'est `Pred()`.  
  
 L'objet allocateur est l'argument `Al`, s'il existe ; sinon, c'est `Alloc()`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_construct.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
#include <initializer_list>  
  
using namespace std;  
  
using Mymap = unordered_map<char, int>;  
  
int main()  
{  
    Mymap c1;  
  
    c1.insert(Mymap::value_type('a', 1));  
    c1.insert(Mymap::value_type('b', 2));  
    c1.insert(Mymap::value_type('c', 3));  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c2(8,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >());  
  
    c2.insert(Mymap::value_type('d', 4));  
    c2.insert(Mymap::value_type('e', 5));  
    c2.insert(Mymap::value_type('f', 6));  
  
    // display contents " [f 6] [e 5] [d 4]"   
    for (const auto& c : c2) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c3(c1.begin(),  
        c1.end(),  
        8,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >());  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c3) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c4(move(c3));  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c4) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
    cout << endl;  
  
    // Construct with an initializer_list  
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });  
    for (const auto& c : c5) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size  
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
    cout << endl;  
  
    // Initializer_list plus size and hash  
    unordered_map<int, char, hash<char>> c7(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },   
        4,   
        hash<char>()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size, hash, and key_equal  
    unordered_map<int, char, hash<char>, equal_to<char>> c8(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },   
        4,   
        hash<char>(),   
        equal_to<char>()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size, hash, key_equal, and allocator  
    unordered_map<int, char, hash<char>, equal_to<char>> c9(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },  
        4,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
}  
```  
  
```Output  
 [a, 1] [b, 2] [c, 3]
 [d, 4] [e, 5] [f, 6]
 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]

 [5, g] [6, h] [7, i] [8, j]
 [a, 1] [b, 2] [c, 3]

 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]
 ```  
  
##  <a name="a-nameunorderedmapvaluetypea--unorderedmapvaluetype"></a><a name="unordered_map__value_type"></a>  unordered_map::value_type  
 Type d’un élément.  
  
```  
typedef std::pair<const Key, Ty> value_type;  
```  
  
### <a name="remarks"></a>Notes  
 Ce type décrit un élément de la séquence contrôlée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// std__unordered_map__unordered_map_value_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect   
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [<unordered_map>](../standard-library/unordered-map.md)   
 [Conteneurs](../cpp/containers-modern-cpp.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)


