---
title: unordered_multiset, classe
description: Référence d’API pour la classe de conteneur de la bibliothèque standard C++ `unordered_multiset` , qui décrit un objet utilisé pour le stockage et la récupération des données d’une collection dans laquelle les valeurs des éléments contenus n’ont pas besoin d’être uniques et dans lesquelles elles servent de valeurs de clés. Les données ne sont pas triées automatiquement.
ms.date: 9/10/2020
f1_keywords:
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
- unordered_set/std::unordered_multiset::contains
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
- unordered_set/std::unordered_multiset::hash_function
helpviewer_keywords:
- std::unordered_multiset
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::contains
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
- std::unordered_multiset::unordered_multiset
- std::unordered_multiset::operator=
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash_function
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
ms.assetid: 70c8dfc5-492a-4af2-84f5-1aa9cb04b71c
ms.openlocfilehash: 0730f4eb6ba8e625c2c40cecddc4f689ec775d17
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352776"
---
# <a name="unordered_multiset-class"></a>unordered_multiset, classe

Le modèle de classe décrit un objet qui contrôle une séquence de longueur variable d’éléments de type `const Key` . La séquence est triée par ordre faible avec une fonction de hachage, qui partitionne la séquence en un ensemble trié de sous-séquences appelées compartiments. Dans chaque compartiment, une fonction de comparaison détermine si des paires d'éléments possèdent un ordre équivalent. Chaque élément sert à la fois de clé de tri et de valeur. La séquence est représentée de façon à permettre la recherche, l'insertion et la suppression d'un élément arbitraire à l'aide d'un certain nombre d'opérations qui peut être indépendant du nombre d'éléments de la séquence (temps constant), du moins lorsque les compartiments sont de longueur à peu près équivalente. Dans le pire des cas, lorsque tous les éléments se trouvent dans un compartiment, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (temps linéaire). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<Key>>
class unordered_multiset;
```

### <a name="parameters"></a>Paramètres

*Essentiel*\
Type de clé.

*Format*\
Type d’objet de la fonction de hachage.

*Prédit*\
Type d’objet de fonction de comparaison d’égalité.

*Utilis*\
Classe allocator.

## <a name="members"></a>Membres

|Définition de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type d’un allocateur pour la gestion du stockage.|
|[const_iterator](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[const_local_iterator](#const_local_iterator)|Type d’un itérateur de compartiment constant pour la séquence contrôlée.|
|[const_pointer](#const_pointer)|Type d'un pointeur constant vers un élément.|
|[const_reference](#const_reference)|Type d'une référence constante à un élément.|
|[difference_type](#difference_type)|Type d'une distance signée entre deux éléments.|
|[Hasher](#hasher)|Type de la fonction de hachage.|
|[répétiteur](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[key_equal](#key_equal)|Type de la fonction de comparaison.|
|[key_type](#key_type)|Type d'une clé de tri.|
|[local_iterator](#local_iterator)|Type d'un itérateur de compartiment pour la séquence contrôlée.|
|[dirigé](#pointer)|Type d'un pointeur vers un élément.|
|[reference](#reference)|Type d'une référence à un élément.|
|[size_type](#size_type)|Type d'une distance non signée entre deux éléments.|
|[value_type](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|-|-|
|[commencer](#begin)|Désigne le début de la séquence contrôlée.|
|[Compartiment](#bucket)|Obtient le numéro du compartiment pour une valeur de clé.|
|[bucket_count](#bucket_count)|Obtient le nombre de compartiments.|
|[bucket_size](#bucket_size)|Obtient la taille d'un compartiment.|
|[cbegin](#cbegin)|Désigne le début de la séquence contrôlée.|
|[cend](#cend)|Désigne la fin de la séquence contrôlée.|
|[clear](#clear)|Supprime tous les éléments.|
|[contient](#contains)<sup>c++ 20</sup>|Vérifie s’il existe un élément avec la clé spécifiée.|
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
|[rehash](#rehash)|Régénère la table de hachage.|
|[size](#size)|Compte le nombre d'éléments.|
|[swap](#swap)|Échange le contenu de deux conteneurs.|
|[unordered_multiset](#unordered_multiset)|Construit un objet conteneur.|

|Opérateur|Description|
|-|-|
|[unordered_multiset :: Operator =](#op_eq)|Copie une table de hachage.|

## <a name="remarks"></a>Notes

L’objet trie la séquence qu’il contrôle en appelant deux objets stockés, un objet de fonction de comparaison de type [unordered_multiset::key_equal](#key_equal) et un objet de fonction de hachage de type [unordered_multiset::hasher](#hasher). Pour accéder au premier objet stocké, appelez la fonction membre [unordered_multiset :: key_eq](#key_eq) `()` ; et vous accédez au deuxième objet stocké en appelant la fonction membre [unordered_multiset :: hash_function](#hash) `()` . Pour toutes les valeurs `X` et `Y` de type `Key`, l'appel `key_eq()(X, Y)` retourne true uniquement si les valeurs des deux arguments ont un classement équivalent. L'appel `hash_function()(keyval)` génère une distribution des valeurs de type `size_t`. Contrairement à la [classe de unordered_set](../standard-library/unordered-set-class.md)de modèle de classe, un objet de type `unordered_multiset` ne garantit pas que `key_eq()(X, Y)` a toujours la valeur false pour deux éléments quelconques de la séquence contrôlée. Il n'est pas nécessaire que les clés soient uniques.

L'objet stocke également un facteur de charge maximale, qui spécifie le nombre moyen maximal d'éléments souhaité par compartiment. Si vous insérez un élément, [unordered_multiset :: load_factor](#load_factor) `()` dépasse le facteur de charge maximale, le conteneur augmente le nombre de compartiments et reconstruit la table de hachage en fonction des besoins.

L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction de comparaison, de l'ordre d'insertion, du facteur de charge maximale et du nombre de compartiments. En général, il n'est pas possible de prévoir l'ordre des éléments de la séquence contrôlée. Toutefois, vous avez la garantie que tous les sous-ensembles d'éléments dont le classement est équivalent sont adjacents dans la séquence contrôlée.

L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un objet allocateur stocké de type [unordered_multiset::allocator_type](#allocator_type). Un tel objet allocateur doit avoir la même interface externe qu’un objet de type `allocator` . Notez que l'objet allocateur stocké n'est pas copié lorsque l'objet conteneur est assigné.

## <a name="requirements"></a>Spécifications

**En-tête :**\<unordered_set>

**Espace de noms :** std

## <a name="unordered_multisetallocator_type"></a><a name="allocator_type"></a> unordered_multiset :: allocator_type

Type d’un allocateur pour la gestion du stockage.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Alloc`.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetbegin"></a><a name="begin"></a> unordered_multiset :: Begin

Désigne le début de la séquence contrôlée ou un compartiment.

```cpp
iterator begin();

const_iterator begin() const;

local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>Paramètres

*nbucket*\
Numéro de compartiment.

### <a name="remarks"></a>Notes

Les deux premières fonctions membres retournent un itérateur vers l'avant qui pointe vers le premier élément de la séquence (ou juste après la fin d'une séquence vide). Les deux dernières fonctions membres retournent un itérateur vers l’avant qui pointe vers le premier élément d’un compartiment *nbucket* (ou juste après la fin d’un compartiment vide).

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect first two items "[c] [b]"
    Myset::iterator it2 = c1.begin();
    std::cout << "[" << *it2 << "] ";
    ++it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[c] [b]
[a]
```

## <a name="unordered_multisetbucket"></a><a name="bucket"></a> unordered_multiset :: compartiment

Obtient le numéro du compartiment pour une valeur de clé.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Paramètres

*keyval*\
Valeur de clé à mapper.

### <a name="remarks"></a>Notes

La fonction membre retourne le numéro de compartiment correspondant actuellement à la valeur de clé `keyval`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetbucket_count"></a><a name="bucket_count"></a> unordered_multiset :: bucket_count

Obtient le nombre de compartiments.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre actuel de comportements.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetbucket_size"></a><a name="bucket_size"></a> unordered_multiset :: bucket_size

Obtient la taille d’un compartiment.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Paramètres

*nbucket*\
Numéro de compartiment.

### <a name="remarks"></a>Notes

Les fonctions membres retournent la taille du compartiment numéro *nbucket*.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetcbegin"></a><a name="cbegin"></a> unordered_multiset :: cbegin

Retourne un **`const`** itérateur qui traite le premier élément de la plage.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

**`const`** Itérateur d’accès en avant qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()` ).

### <a name="remarks"></a>Notes

Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `begin()` et `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator

auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="unordered_multisetcend"></a><a name="cend"></a> unordered_multiset :: CEND

Retourne un **`const`** itérateur qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

**`const`** Itérateur d’accès en avant qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `end()` et `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator

auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="unordered_multisetclear"></a><a name="clear"></a> unordered_multiset :: Clear

Supprime tous les éléments.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [unordered_multiset::erase](#erase)`(` [unordered_multiset::begin](#begin)`(),` [unordered_multiset::end](#end)`())`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetconst_iterator"></a><a name="const_iterator"></a> unordered_multiset :: const_iterator

Type d'un itérateur constant pour la séquence contrôlée.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir d'itérateur vers l'avant constant pour la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T1`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetconst_local_iterator"></a><a name="const_local_iterator"></a> unordered_multiset :: const_local_iterator

Type d’un itérateur de compartiment constant pour la séquence contrôlée.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir d’itérateur de constante vers l’avant pour un compartiment. Il est décrit ici comme un synonyme du type défini par l'implémentation `T5`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="unordered_multisetconst_pointer"></a><a name="const_pointer"></a> unordered_multiset :: const_pointer

Type d'un pointeur constant vers un élément.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir de pointeur constant à un élément de la séquence contrôlée.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::const_pointer p = &*it;
        std::cout << "[" << *p << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetconst_reference"></a><a name="const_reference"></a> unordered_multiset :: const_reference

Type d'une référence constante à un élément.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir de référence constante à un élément de la séquence contrôlée.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::const_reference ref = *it;
        std::cout << "[" << ref << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetcontains"></a><a name="contains"></a> unordered_multiset :: Contains

Vérifie s’il existe un élément avec la clé spécifiée dans le `unordered_multiset` .

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Paramètres

*DK*\
Type de la clé.

*essentiel*\
Valeur de clé de l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

`true` Si l’élément est trouvé dans le conteneur ; `false` sinon,.

### <a name="remarks"></a>Notes

`contains()` est nouveau dans C++ 20. Pour l’utiliser, spécifiez l’option de compilateur [/std : c + + latest](../build/reference/std-specify-language-standard-version.md) .

`template<class K> bool contains(const K& key) const` participe uniquement à la résolution de surcharge si `key_compare` est transparent.

### <a name="example"></a> Exemple

```cpp
// Requires /std:c++latest
#include <unordered_set>
#include <iostream>

int main()
{
    std::unordered_multiset<int> theUnorderedMultiset = { 1, 2, 3 };

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMultiset.contains(1) << '\n';
    std::cout << theUnorderedMultiset.contains(4) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="unordered_multisetcount"></a><a name="count"></a> unordered_multiset :: Count

Recherche le nombre d’éléments qui correspondent à une clé spécifiée.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Paramètres

*keyval*\
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d’éléments de la plage délimitée par [unordered_multiset :: equal_range](#equal_range) `(keyval)` .

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetdifference_type"></a><a name="difference_type"></a> unordered_multiset ::d ifference_type

Type d'une distance signée entre deux éléments.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Notes

Le type d'entier signé décrit un objet qui peut représenter la différence entre les adresses de deux éléments quelconques dans la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T3`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetemplace"></a><a name="emplace"></a> unordered_multiset :: emplace

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Les arguments transférés pour construire un élément à insérer dans la classe unordered_multiset.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

Aucune référence aux éléments de conteneur n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Durant l’insertion, si une exception est levée mais qu’elle ne se produit pas dans la fonction de hachage du conteneur, le conteneur n’est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini.

Pour obtenir un exemple de code, consultez [multiset::emplace](../standard-library/multiset-class.md#emplace).

## <a name="unordered_multisetemplace_hint"></a><a name="emplace_hint"></a> unordered_multiset :: emplace_hint

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée) avec un hint d’emplacement.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Les arguments transférés pour construire un élément à insérer dans la classe unordered_multiset.

*Cela*\
Indicateur concernant l’emplacement où commencer à rechercher le point d’insertion correct.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’élément qui vient d’être inséré.

### <a name="remarks"></a>Notes

Aucune référence aux éléments de conteneur n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Durant l’insertion, si une exception est levée mais qu’elle ne se produit pas dans la fonction de hachage du conteneur, le conteneur n’est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini.

Pour obtenir un exemple de code, consultez [set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="unordered_multisetempty"></a><a name="empty"></a> unordered_multiset :: Empty

Vérifie l'absence d'éléments.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetend"></a><a name="end"></a> unordered_multiset :: fin

Désigne la fin de la séquence contrôlée.

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>Paramètres

*nbucket*\
Numéro de compartiment.

### <a name="remarks"></a>Notes

Les deux premières fonctions membres retournent un itérateur vers l'avant qui pointe juste après la fin de la séquence. Les deux dernières fonctions membres retournent un itérateur vers l’avant qui pointe juste après la fin du compartiment *nbucket*.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect last two items "[a] [b]"
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << "[" << *it2 << "] ";
    --it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a] [b]
[a]
```

## <a name="unordered_multisetequal_range"></a><a name="equal_range"></a> unordered_multiset :: equal_range

Recherche une plage qui correspond à une clé spécifiée.

```cpp
std::pair<iterator, iterator>
    equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
    equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Paramètres

*keyval*\
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne une paire d’itérateurs `X` qui `[X.first, X.second)` délimite uniquement les éléments de la séquence contrôlée qui ont un classement équivalent avec *keyVal*. Si aucun de ces éléments n’existe, les deux itérateurs sont `end()`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="unordered_multiseterase"></a><a name="erase"></a> unordered_multiset :: Erase

Supprime un élément ou une plage d’éléments dans une classe unordered_multiset aux positions spécifiées ou supprime les éléments qui correspondent à une clé spécifiée.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Paramètres

*Cela*\
Position de l’élément à supprimer.

*Premier*\
Position du premier élément à supprimer.

*Famille*\
Position juste après le dernier élément à supprimer.

*Essentiel*\
Valeur de clé des éléments à supprimer.

### <a name="return-value"></a>Valeur de retour

Pour les deux premières fonctions membres, un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un élément à la fin de la classe unordered_multiset si aucun élément de ce type n’existe.

Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés de la classe unordered_multiset.

### <a name="remarks"></a>Notes

Pour obtenir un exemple de code, consultez [set::erase](../standard-library/set-class.md#erase).

## <a name="unordered_multisetfind"></a><a name="find"></a> unordered_multiset :: find

Recherche un élément qui correspond à une clé spécifiée.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Paramètres

*keyval*\
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne [unordered_multiset :: equal_range](#equal_range) `(keyval).first` .

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << *it << "] " << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="unordered_multisetget_allocator"></a><a name="get_allocator"></a> unordered_multiset :: get_allocator

Obtient l’objet allocateur stocké.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne l’objet d’allocateur stocké.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisethash_function"></a><a name="hash"></a> unordered_multiset :: hash_function

Obtient l'objet de fonction de hachage stocké.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne l’objet de fonction de hachage stocké.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisethasher"></a><a name="hasher"></a> unordered_multiset :: Hasher

Type de la fonction de hachage.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Hash`.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetinsert"></a><a name="insert"></a> unordered_multiset :: Insert

Insère un élément ou une plage d'éléments dans une classe unordered_multiset.

```cpp
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

*Multiples*\
Valeur d'un élément à insérer dans la classe unordered_multiset.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct.

*ValTy*\
Paramètre de modèle qui spécifie le type d’argument que l’unordered_multiset peut utiliser pour construire un élément de [Value_type](../standard-library/map-class.md#value_type), et parfait-transfère la valeur *Val* en tant qu’argument.

*Premier*\
Position du premier élément à copier.

*Famille*\
Position juste au-delà du dernier élément à copier.

*InputIterator*\
Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](../standard-library/map-class.md#value_type).

*IList*\
[Initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.

### <a name="return-value"></a>Valeur de retour

Les fonctions membres d'insertion à un élément, (1) et (2), retournent un itérateur vers l'emplacement où le nouvel élément a été inséré dans la classe unordered_multiset.

Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe vers l'emplacement où le nouvel élément a été inséré dans la classe unordered_multiset.

### <a name="remarks"></a>Notes

Aucun pointeur ou référence n'est invalidé par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Durant l'insertion d'un seul élément, si une exception est levée mais qu'elle ne se produit pas dans la fonction de hachage du conteneur, l'état du conteneur n'est pas modifié. Si l'exception est levée dans la fonction de hachage, le résultat n'est pas défini. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.

Le [value_type](../standard-library/map-class.md#value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe set, `unordered_multiset<V>::value_type` est du type `const V`.

La fonction membre de plage (5) insère la séquence de valeurs d’éléments dans un unordered_multiset qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; par conséquent, *Last* n’est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `m.insert(v.begin(), v.end());` insère tous les éléments de `v` dans `m`.

La fonction membre de liste d’initialiseurs (6) utilise un objet [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans l’objet unordered_multiset.

Pour l’insertion d’un élément construit sur place (aucune opération de copie ni de déplacement n’est effectuée), consultez [unordered_multiset::emplace](#emplace) et [unordered_multiset::emplace_hint](#emplace_hint).

Pour obtenir un exemple de code, consultez [multiset::insert](../standard-library/multiset-class.md#insert).

## <a name="unordered_multisetiterator"></a><a name="iterator"></a> unordered_multiset :: Iterator

Type qui fournit un [itérateur vers l’avant](../standard-library/forward-iterator-tag-struct.md) constant capable de lire des éléments dans une classe unordered_multiset.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a> Exemple

Consultez l’exemple [begin](../standard-library/multiset-class.md#begin) pour savoir comment déclarer et utiliser **iterator**.

## <a name="unordered_multisetkey_eq"></a><a name="key_eq"></a> unordered_multiset :: key_eq

Obtient l'objet de fonction de comparaison stocké.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne l’objet de fonction de comparaison stocké.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetkey_equal"></a><a name="key_equal"></a> unordered_multiset :: key_equal

Type de la fonction de comparaison.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Pred`.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetkey_type"></a><a name="key_type"></a> unordered_multiset :: key_type

Type d'une clé de tri.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Key`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="unordered_multisetload_factor"></a><a name="load_factor"></a> unordered_multiset :: load_factor

Compte le nombre moyen d'éléments par compartiment.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne `(float)` [unordered_multiset :: Size](#size) `() / (float)` [unordered_multiset :: bucket_count](#bucket_count) `()` , le nombre moyen d’éléments par compartiment.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetlocal_iterator"></a><a name="local_iterator"></a> unordered_multiset :: local_iterator

Type d'un itérateur de compartiment.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir d'itérateur vers l'avant pour un compartiment. Il est décrit ici comme un synonyme du type défini par l'implémentation `T4`.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="unordered_multisetmax_bucket_count"></a><a name="max_bucket_count"></a> unordered_multiset :: max_bucket_count

Obtient le nombre maximal de compartiments.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre maximal de compartiments actuellement autorisés.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetmax_load_factor"></a><a name="max_load_factor"></a> unordered_multiset :: max_load_factor

Obtient ou définit le nombre maximal d’éléments par compartiment.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>Paramètres

*factorisés*\
Nouveau facteur de charge maximale.

### <a name="remarks"></a>Notes

La première fonction membre retourne le facteur de charge maximale stockée. La deuxième fonction membre remplace le facteur de charge maximale stocké par *Factor*.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetmax_size"></a><a name="max_size"></a> unordered_multiset :: max_size

Obtient ou définit la taille maximale de la séquence contrôlée.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence la plus longue que l’objet peut contrôler.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetoperator"></a><a name="op_eq"></a> unordered_multiset :: Operator =

Copie une table de hachage.

```cpp
unordered_multiset& operator=(const unordered_multiset& right);

unordered_multiset& operator=(unordered_multiset&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet [unordered_multiset](../standard-library/unordered-multiset-class.md) copié dans l’objet `unordered_multiset`.

### <a name="remarks"></a>Notes

Après l’effacement des éléments existants dans un `unordered_multiset` , `operator=` copie ou déplace le contenu de *droite* dans le `unordered_multiset` .

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetpointer"></a><a name="pointer"></a> unordered_multiset ::p ointer

Type d'un pointeur vers un élément.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir de pointeur vers un élément de la séquence contrôlée.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << "[" << *p << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetreference"></a><a name="reference"></a> unordered_multiset :: référence

Type d'une référence à un élément.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Notes

Le type décrit un objet qui peut servir de référence à un élément de la séquence contrôlée.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << "[" << ref << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetrehash"></a><a name="rehash"></a> unordered_multiset :: rehash

Régénère la table de hachage.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Paramètres

*nbuckets*\
Nombre de compartiments demandés.

### <a name="remarks"></a>Notes

La fonction membre modifie le nombre de compartiments pour qu’elle soit au moins *nbuckets* et reconstruit la table de hachage en fonction des besoins.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetsize"></a><a name="size"></a> unordered_multiset :: Size

Compte le nombre d'éléments.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetsize_type"></a><a name="size_type"></a> unordered_multiset :: size_type

Type d'une distance non signée entre deux éléments.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Notes

Le type d'entier non signé décrit un objet qui peut représenter la longueur de n'importe quelle séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l'implémentation `T2`.

### <a name="example"></a> Exemple

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

## <a name="unordered_multisetswap"></a><a name="swap"></a> unordered_multiset :: swap

Échange le contenu de deux conteneurs.

```cpp
void swap(unordered_multiset& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Conteneur avec lequel faire l’échange.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre **`*this`** et *Right*. Si [unordered_multiset :: get_allocator](#get_allocator) `() == right.get_allocator()` , elle le fait en temps constant, elle lève une exception uniquement en raison de la copie de l’objet de traits stocké de type `Tr` , et n’invalide aucune référence, pointeur ou itérateur qui désignent des éléments dans les deux séquences contrôlées. Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.

### <a name="example"></a> Exemple

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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents "[f] [e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="unordered_multisetunordered_multiset"></a><a name="unordered_multiset"></a> unordered_multiset :: unordered_multiset

Construit un objet conteneur.

```cpp
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

*InputIterator*\
Type d'itérateur.

*&*\
Objet allocateur à stocker.

*Conformes*\
Objet de fonction de comparaison à stocker.

*Format*\
Objet de fonction de hachage à stocker.

*Bucket_count*\
Nombre minimal de compartiments.

*Oui*\
Conteneur à copier.

*IList*\
initializer_list depuis laquelle effectuer la copie.

### <a name="remarks"></a>Notes

Le premier constructeur spécifie une copie de la séquence contrôlée par *Right*. Le deuxième constructeur spécifie une séquence vide contrôlée. Le troisième constructeur insère la séquence de valeurs d'éléments `[First, Last)`. Le quatrième constructeur spécifie une copie de la séquence en se déplaçant vers la *droite*.

Tous les constructeurs initialisent également plusieurs valeurs stockées. Pour le constructeur de copie, les valeurs sont obtenues à partir de *Right*. Sinon :

Le nombre minimal de compartiments est l’argument *Bucket_count*, le cas échéant ; dans le cas contraire, il s’agit d’une valeur par défaut décrite ici comme valeur définie par l’implémentation `N0` .

L’objet de fonction de hachage est le *hachage*d’argument, s’il existe ; dans le cas contraire, il s’agit de `Hash()` .

L’objet de fonction de comparaison est l’argument *COMP*, s’il est présent ; dans le cas contraire, il s’agit de `Comp()` .

L’objet Allocator est l’argument *al*, s’il est présent ; dans le cas contraire, il s’agit de `Alloc()` .

## <a name="unordered_multisetvalue_type"></a><a name="value_type"></a> unordered_multiset :: value_type

Type d’un élément.

```cpp
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

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="see-also"></a>Voir aussi

[<unordered_set>](../standard-library/unordered-set.md)\
[Recipie](./stl-containers.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
