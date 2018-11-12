---
title: algorithm (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 6011aad0ef86bc0e633687a6d8e017e9b12771c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528724"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)

Définit les fonctions de modèle de conteneur STL/CLR qui exécutent des algorithmes.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<cliext/algorithm >

**Namespace :** cliext

## <a name="declarations"></a>Déclarations

|Fonction|Description|
|--------------|-----------------|
|[adjacent_find (STL/CLR)](#adjacent_find)|Recherche deux éléments adjacents qui sont égaux.|
|[binary_search (STL/CLR)](#binary_search)|Teste si une séquence triée contient une valeur donnée.|
|[copy (STL/CLR)](#copy)|Copie les valeurs d’une plage source à une plage de destination, en effectuant une itération dans la direction vers l’avant.|
|[copy_backward (STL/CLR)](#copy_backward)|Copie les valeurs d’une plage source à une plage de destination, en effectuant une itération dans la direction descendante.|
|[count (STL/CLR)](#count)|Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.|
|[count_if (STL/CLR)](#count_if)|Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une condition spécifiée.|
|[equal (STL/CLR)](#equal)|Compare deux plages, élément par élément.|
|[equal_range (STL/CLR)](#equal_range)|Recherche une séquence ordonnée de valeurs et retourne des deux positions qui délimitent une sous-séquence de valeurs qui sont toujours égaux à un élément donné.|
|[fill (STL/CLR)](#fill)|Affecte la même nouvelle valeur à chaque élément d'une plage spécifiée.|
|[fill_n (STL/CLR)](#fill_n)|Attribue une nouvelle valeur à un nombre spécifié d’éléments d’une plage commençant par un élément particulier.|
|[find (STL/CLR)](#find)|Retourne la position de la première occurrence d’une valeur spécifiée.|
|[find_end (STL/CLR)](#find_end)|Retourne la dernière sous-séquence d’une plage qui est identique à une séquence spécifiée.|
|[find_first_of (STL/CLR)](#find_first_of)|Recherche dans une plage pour la première occurrence de l’un d’une plage d’éléments de donnée.|
|[find_if (STL/CLR)](#find_if)|Retourne la position du premier élément dans une séquence de valeurs, où l’élément satisfait à une condition spécifiée.|
|[for_each (STL/CLR)](#for_each)|Applique un objet de fonction spécifié à chaque élément dans une séquence de valeurs et retourne l’objet de fonction.|
|[generate (STL/CLR)](#generate)|Assigne les valeurs générées par un objet de fonction à chaque élément dans une séquence de valeurs.|
|[generate_n (STL/CLR)](#generate_n)|Assigne les valeurs générées par un objet de fonction à un nombre spécifié d’éléments.|
|[includes (STL/CLR)](#includes)|Teste si une plage triée contient tous les éléments dans une autre plage triée.|
|[inplace_merge (STL/CLR)](#inplace_merge)|Combine les éléments de deux plages triées consécutives dans une même plage triée.|
|[iter_swap (STL/CLR)](#iter_swap)|Échange deux valeurs référencées par une paire d'itérateurs spécifiés.|
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|Compare deux séquences, élément par élément, identifiant la séquence qui est le plus petit des deux.|
|[lower_bound (STL/CLR)](#lower_bound)|Recherche la position du premier élément dans une séquence ordonnée de valeurs qui a une valeur supérieure ou égale à une valeur spécifiée.|
|[make_heap (STL/CLR)](#make_heap)|Convertit les éléments d’une plage spécifiée dans un segment de mémoire où le premier élément sur le tas est le plus grand.|
|[max (STL/CLR)](#max))|Compare deux objets et retourne la plus grande des deux.|
|[max_element (STL/CLR)](#max_element)|Recherche l’élément le plus grand dans une séquence spécifique de valeurs.|
|[fusion (STL/CLR)](#merge))|Combine tous les éléments de deux plages sources triées dans une plage de destination unique, triées.|
|[min (STL/CLR)](#min)|Compare deux objets et retourne le plus petit des deux.|
|[min_element (STL/CLR)](#min_element)|Recherche le plus petit élément dans une séquence spécifique de valeurs.|
|[mismatch (STL/CLR)](#mismatch)|Compare deux plages, élément par élément et retourne la première position où se trouve une différence.|
|[next_permutation (STL/CLR)](#next_permutation)|Réorganise les éléments dans une plage afin que l’ordre d’origine est remplacée par la permutation lexicographique suivante supérieure si elle existe.|
|[nth_element (STL/CLR)](#nth_element)|Partitionne une séquence d’éléments, en recherchant le `n`-ième élément de la séquence afin que tous les éléments le précédant lui soient inférieur ou égal à celui-ci et tous les éléments qui le suivent sont supérieurs ou égaux.|
|[partial_sort (STL/CLR)](#partial_sort)|Réorganise un nombre spécifié d’éléments plus petits dans une plage dans un ordre non décroissant.|
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|Copie les éléments d’une plage source dans une plage de destination telles que les éléments à partir de la plage source sont classés.|
|[partition (STL/CLR)](#partition)|Réorganise les éléments dans une plage de telle sorte que les éléments qui satisfont un prédicat unaire qui précèdent ceux qui n’y répondent pas.|
|[pop_heap (STL/CLR)](#pop_heap)|Déplace l’élément le plus grand du début d’un segment à la fin et crée ensuite un nouveau segment de mémoire à partir des éléments restants.|
|[prev_permutation (STL/CLR)](#prev_permutation)|Réorganise une séquence d’éléments afin que l’ordre d’origine est remplacée par la permutation lexicographique précédente supérieure si elle existe.|
|[push_heap (STL/CLR)](#push_heap)|Ajoute un élément qui se trouve à la fin d'une plage à un tas existant, constitué des éléments précédents de la plage.|
|[random_shuffle (STL/CLR)](#random_shuffle)|Réorganise une séquence de `N` éléments dans une plage en `N`! dispositions possibles, sélectionnées de manière aléatoire.|
|[remove (STL/CLR)](#remove)|Supprime une valeur spécifiée à partir d’une plage donnée sans porter atteinte à l’ordre des éléments restants et retourne la fin d’une nouvelle plage exempte de la valeur spécifiée.|
|[remove_copy (STL/CLR)](#remove_copy)|Copie les éléments d’une plage source dans une plage de destination, à ceci près que les éléments d’une valeur spécifiée ne sont pas copiés, sans porter atteinte à l’ordre des éléments restants.|
|[remove_copy_if (STL/CLR)](#remove_copy_if)|Copie les éléments d’une plage source à une plage de destination, à l’exception de ceux qui satisfont un prédicat, sans porter atteinte à l’ordre des éléments restants.|
|[remove_if (STL/CLR)](#remove_if)|Supprime les éléments qui satisfont un prédicat dans une plage donnée sans porter atteinte à l’ordre des éléments restants. .|
|[replace (STL/CLR)](#replace)|Remplace les éléments d’une plage qui correspond à une valeur spécifiée avec une nouvelle valeur.|
|[replace_copy (STL/CLR)](#replace_copy)|Copie les éléments d’une plage source à une plage de destination, en remplaçant les éléments qui correspondent à une valeur spécifiée avec une nouvelle valeur.|
|[replace_copy_if (STL/CLR)](#replace_copy_if)|Examine tous les éléments d'une plage source et les remplace s'ils répondent à un prédicat, tout en copiant le résultat dans une nouvelle plage de destination.|
|[replace_if (STL/CLR)](#replace_if)|Examine tous les éléments d’une plage et les remplace s’ils répondent à un prédicat spécifié.|
|[reverse (STL/CLR)](#reverse)|Inverse l'ordre des éléments d'une plage.|
|[reverse_copy (STL/CLR)](#reverse_copy)|Inverse l’ordre des éléments dans une plage source tout en les copiant dans une plage de destination.|
|[rotate (STL/CLR)](#rotate)|Échange les éléments de deux plages adjacentes.|
|[rotate_copy (STL/CLR)](#rotate_copy)|Échange les éléments de deux plages adjacentes au sein d'une plage source et copie le résultat dans une plage de destination.|
|[search (STL/CLR)](#search_)|Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.|
|[search_n (STL/CLR)](#search_n)|Recherche la première sous-séquence d’une plage dont un nombre spécifié d’éléments ont une valeur particulière ou une relation à cette valeur, selon un prédicat binaire spécifié.|
|[set_difference (STL/CLR)](#set_difference)|Regroupe tous les éléments qui appartiennent à une plage source triée, mais pas à une autre plage source triée, en une même plage de destination triée. Un critère de tri peut être spécifié par un prédicat binaire.|
|[set_intersection (STL/CLR)](#set_intersection)|Regroupe tous les éléments de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|Regroupe tous les éléments qui appartiennent à l'une de deux plages sources triées (mais pas aux deux) au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[set_union (STL/CLR)](#set_union))|Regroupe tous les éléments qui appartiennent au moins à l'une de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[sort (STL/CLR)](#sort)|Réorganise les éléments d’une plage spécifiée, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.|
|[sort_heap (STL/CLR)](#sort_heap)|Convertit un tas en une plage triée.|
|[stable_partition (STL/CLR)](#stable_partition)|Classe les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas, et l’ordre relatif des éléments équivalents doit être conservé.|
|[stable_sort (STL/CLR)](#stable_sort)|Classe les éléments d’une plage spécifiée dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire, et conserve l’ordre relatif des éléments équivalents.|
|[swap (STL/CLR)](#swap)|Échange les valeurs des éléments de deux types d'objets, en assignant le contenu du premier objet au deuxième objet, et le contenu du deuxième au premier.|
|[swap_ranges (STL/CLR)](#swap_ranges)|Échange les éléments d'une plage avec ceux d'une autre plage de taille égale.|
|[transform (STL/CLR)](#transform)|Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination.|
|[unique (STL/CLR)](#unique)|Supprime les éléments en double adjacents dans une plage spécifiée.|
|[unique_copy (STL/CLR)](#unique_copy)|Copie les éléments d'une plage source dans une plage de destination, à l'exception des éléments en double adjacents.|
|[upper_bound (STL/CLR)](#upper_bound)|Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.|

## <a name="members"></a>Membres

## <a name="adjacent_find"></a> adjacent_find (STL/CLR)

Recherche deux éléments adjacents qui ont la même valeur ou qui répondent à une condition spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `adjacent_find`. Pour plus d’informations, consultez [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find).

## <a name="binary_search"></a> binary_search (STL/CLR)

Teste si un élément d’une plage triée est égal à une valeur spécifiée ou équivalent, selon une condition spécifiée par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `binary_search`. Pour plus d’informations, consultez [binary_search](../standard-library/algorithm-functions.md#binary_search).

## <a name="copy"></a> copie (STL/CLR)

Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions, du haut vers le bas.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `copy`. Pour plus d’informations, consultez [copie](../standard-library/algorithm-functions.md#copy).

## <a name="copy_backward"></a> copy_backward (STL/CLR)

Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions vers le haut.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `copy_backward`. Pour plus d’informations, consultez [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

## <a name="count"></a> nombre (STL/CLR)

Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `count`. Pour plus d’informations, consultez [nombre](../standard-library/algorithm-functions.md#count).

## <a name="count_if"></a> count_if (STL/CLR)

Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une condition spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `count_if`. Pour plus d’informations, consultez [count_if](../standard-library/algorithm-functions.md#count_if).

## <a name="equal"></a> égal (STL/CLR)

Compare deux plages, élément par élément, à la recherche d’une égalité ou d’une équivalence, selon une condition spécifiée par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `equal`. Pour plus d’informations, consultez [égal](../standard-library/algorithm-functions.md#equal).

## <a name="equal_range"></a> equal_range (STL/CLR)

Recherche une paire de positions dans une plage triée. La première inférieure ou équivalente à la position d’un élément spécifié, et la deuxième supérieure à la position de cet élément. L’équivalence ou le tri utilisés pour établir des positions dans la séquence peuvent être spécifiés par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `equal_range`. Pour plus d’informations, consultez [equal_range](../standard-library/algorithm-functions.md#equal_range).

## <a name="fill"></a> remplissage (STL/CLR)

Affecte la même nouvelle valeur à chaque élément d'une plage spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `fill`. Pour plus d’informations, consultez [remplissage](../standard-library/algorithm-functions.md#fill).

## <a name="fill_n"></a> fill_n (STL/CLR)

Attribue une nouvelle valeur à un nombre spécifié d’éléments d’une plage commençant par un élément particulier.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `fill_n`. Pour plus d’informations, consultez [fill_n](../standard-library/algorithm-functions.md#fill_n).

## <a name="find"></a> Find (STL/CLR)

Recherche la position de la première occurrence d'un élément d'une plage ayant une valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `find`. Pour plus d’informations, consultez [trouver](../standard-library/algorithm-functions.md#find).

## <a name="find_end"></a> find_end (STL/CLR)

Recherche dans une plage la dernière sous-séquence qui est identique à une séquence spécifiée ou qui est équivalente, selon une condition spécifiée par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `find_end`. Pour plus d’informations, consultez [find_end](../standard-library/algorithm-functions.md#find_end).

## <a name="find_first_of"></a> find_first_of (STL/CLR)

Recherche la première occurrence parmi plusieurs valeurs d’une plage cible, ou la première occurrence parmi plusieurs éléments qui sont équivalents, selon une condition spécifiée par un prédicat binaire, à un ensemble d’éléments spécifiés.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `find_first_of`. Pour plus d’informations, consultez [find_first_of](../standard-library/algorithm-functions.md#find_first_of).

## <a name="find_if"></a> find_if (STL/CLR)

Recherche la position de la première occurrence d'un élément d'une plage qui répond à une condition spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `find_if`. Pour plus d’informations, consultez [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a> for_each (STL/CLR)

Applique un objet de fonction spécifié à chaque élément d'une plage, du haut vers le bas, et retourne l'objet de la fonction.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `for_each`. Pour plus d’informations, consultez [for_each](../standard-library/algorithm-functions.md#for_each).

## <a name="generate"></a> Générer (STL/CLR)

Assigne les valeurs générées par un objet de fonction à chaque élément d'une plage.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `generate`. Pour plus d’informations, consultez [générer](../standard-library/algorithm-functions.md#generate).

## <a name="generate_n"></a> generate_n (STL/CLR)

Assigne les valeurs générées par un objet de fonction à un nombre spécifié d'éléments d'une plage, et retourne à la position située juste après la dernière valeur assignée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `generate_n`. Pour plus d’informations, consultez [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="includes"></a> inclut (STL/CLR)

Teste si une plage triée contient tous les éléments d’une autre plage triée. Le critère de tri ou d’équivalence entre les éléments peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `includes`. Pour plus d’informations, consultez [inclut](../standard-library/algorithm-functions.md#includes).

## <a name="inplace_merge"></a> inplace_merge (STL/CLR)

Regroupe les éléments de deux plages triées consécutives au sein d’une même plage triée. Le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `inplace_merge` pour plus d’informations, consultez [inplace_merge](../standard-library/algorithm-functions.md#inplace_merge).

## <a name="iter_swap"></a> iter_swap (STL/CLR)

Échange deux valeurs référencées par une paire d'itérateurs spécifiés.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `iter_swap`. Pour plus d’informations, consultez [iter_swap](../standard-library/algorithm-functions.md#iter_swap).

## <a name="lexicographical_compare"></a> lexicographical_compare (STL/CLR)

Compare deux séquences, élément par élément, pour déterminer lequel est inférieur à l'autre.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `lexicographical_compare`. Pour plus d’informations, consultez [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare).

## <a name="lower_bound"></a> lower_bound (STL/CLR)

Recherche la position du premier élément dans une plage ordonnée qui a une valeur inférieure ou équivalente à une valeur spécifiée, où le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `lower_bound`. Pour plus d’informations, consultez [lower_bound](../standard-library/algorithm-functions.md#lower_bound).

## <a name="make_heap"></a> make_heap (STL/CLR)

Convertit les éléments d’une plage spécifiée en un tas, dans lequel le premier élément est le plus grand, et pour lequel un critère de tri peut être spécifié à l’aide d’un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `make_heap`. Pour plus d’informations, consultez [make_heap](../standard-library/algorithm-functions.md#make_heap).

## <a name="max"></a> max (STL/CLR)

Compare deux objets et retourne le plus grand des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `max`. Pour plus d’informations, consultez [max](../standard-library/algorithm-functions.md#max).

## <a name="max_element"></a> max_element (STL/CLR)

Recherche la première occurrence du plus grand élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `max_element`. Pour plus d’informations, consultez [max_element](../standard-library/algorithm-functions.md#max_element).

## <a name="merge"></a> fusion (STL/CLR)

Regroupe tous les éléments de deux plages sources triées au sein d’une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `merge`. Pour plus d’informations, consultez [fusion](../standard-library/algorithm-functions.md#merge).

## <a name="min"></a> min (STL/CLR)

Compare deux objets et retourne le plus petit des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `min`. Pour plus d’informations, consultez [min](../standard-library/algorithm-functions.md#min).

## <a name="min_element"></a> min_element (STL/CLR)

Recherche la première occurrence du plus petit élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `min_element`. Pour plus d’informations, consultez [min_element](../standard-library/algorithm-functions.md#min_element).

## <a name="mismatch"></a> incompatibilité (STL/CLR)

Compare deux plages, élément par élément, à la recherche d’une égalité ou d’une équivalence, selon une condition spécifiée par un prédicat binaire, et recherche la première position où se trouve une différence.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `mismatch`. Pour plus d’informations, consultez [incompatibilité](../standard-library/algorithm-functions.md#mismatch).

## <a name="next_permutation"></a> next_permutation (STL/CLR)

Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `next_permutation`. Pour plus d’informations, consultez [next_permutation](../standard-library/algorithm-functions.md#next_permutation).

## <a name="nth_element"></a> nth_element (STL/CLR)

Partitionne une plage d’éléments, en recherchant le `n`-ième élément de la séquence dans la plage afin que tous les éléments le précédant lui soient inférieur ou égal à celui-ci et tous les éléments qui suivent dans la séquence sont supérieur ou égal à celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `nth_element`. Pour plus d’informations, consultez [nth_element](../standard-library/algorithm-functions.md#nth_element).

## <a name="partial_sort"></a> partial_sort (STL/CLR)

Réorganise un nombre spécifié d’éléments plus petits au sein d’une plage, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `partial_sort`. Pour plus d’informations, consultez [partial_sort](../standard-library/algorithm-functions.md#partial_sort).

## <a name="partial_sort_copy"></a> partial_sort_copy (STL/CLR)

Copie les éléments d’une plage source dans une plage de destination. Les éléments sources sont triés par ordre croissant ou selon un autre prédicat binaire spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `partial_sort_copy`. Pour plus d’informations, consultez [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).

## <a name="partition"></a> partition (STL/CLR)

Répartit les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `partition`. Pour plus d’informations, consultez [partition](../standard-library/algorithm-functions.md#partition).

## <a name="pop_heap"></a> pop_heap (STL/CLR)

Retire le plus grand élément du début du tas et le place à l'avant-dernière position de la plage, puis forme un nouveau tas à partir des éléments restants.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `pop_heap`. Pour plus d’informations, consultez [pop_heap](../standard-library/algorithm-functions.md#pop_heap).

## <a name="prev_permutation"></a> prev_permutation (STL/CLR)

Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `prev_permutation`. Pour plus d’informations, consultez [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).

## <a name="push_heap"></a> push_heap (STL/CLR)

Ajoute un élément qui se trouve à la fin d'une plage à un tas existant, constitué des éléments précédents de la plage.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `push_heap`. Pour plus d’informations, consultez [push_heap](../standard-library/algorithm-functions.md#push_heap).

## <a name="random_shuffle"></a> random_shuffle (STL/CLR)

Réorganise une séquence de `N` éléments dans une plage en `N`! dispositions possibles, sélectionnées de manière aléatoire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `random_shuffle`. Pour plus d’informations, consultez [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

## <a name="remove"></a> Supprimer (STL/CLR)

Élimine une valeur spécifiée d'une plage donnée sans modifier l'ordre des éléments restants, et retourne la fin d'une nouvelle plage exempte de la valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `remove`. Pour plus d’informations, consultez [supprimer](../standard-library/algorithm-functions.md#remove).

## <a name="remove_copy"></a> remove_copy (STL/CLR)

Copie les éléments d'une plage source vers une plage de destination. Les éléments ayant une valeur spécifiée ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `remove_copy`. Pour plus d’informations, consultez [remove_copy](../standard-library/algorithm-functions.md#remove_copy).

## <a name="remove_copy_if"></a> remove_copy_if (STL/CLR)

Copie les éléments d'une plage source vers une plage de destination. Les éléments répondant à un prédicat ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `remove_copy_if`. Pour plus d’informations, consultez [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).

## <a name="remove_if"></a> remove_if (STL/CLR)

Élimine d’une plage donnée les éléments qui répondent à un prédicat, sans modifier l’ordre des éléments restants et en retournant la fin d’une nouvelle plage exempte de la valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `remove_if`. Pour plus d’informations, consultez [remove_if](../standard-library/algorithm-functions.md#remove_if).

## <a name="replace"></a> Replace (STL/CLR)

Examine tous les éléments d'une plage et les remplace s'ils correspondent à une valeur spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `replace`. Pour plus d’informations, consultez [remplacer](../standard-library/algorithm-functions.md#replace).

## <a name="replace_copy"></a> replace_copy (STL/CLR)

Examine tous les éléments d'une plage source et les remplace s'ils correspondent à une valeur spécifiée, tout en copiant le résultat dans une nouvelle plage de destination.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `replace_copy`. Pour plus d’informations, consultez [replace_copy](../standard-library/algorithm-functions.md#replace_copy).

## <a name="replace_copy_if"></a> replace_copy_if (STL/CLR)

Examine tous les éléments d'une plage source et les remplace s'ils répondent à un prédicat, tout en copiant le résultat dans une nouvelle plage de destination.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `replace_copy_if`. Pour plus d’informations, consultez [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).

## <a name="replace_if"></a> replace_if (STL/CLR)

Examine tous les éléments d’une plage et les remplace s’ils répondent à un prédicat spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `replace_if`. Pour plus d’informations, consultez [replace_if](../standard-library/algorithm-functions.md#replace_if).

## <a name="reverse"></a> Reverse (STL/CLR)

Inverse l'ordre des éléments d'une plage.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `reverse`. Pour plus d’informations, consultez [inverse](../standard-library/algorithm-functions.md#reverse).

## <a name="reverse_copy"></a> reverse_copy (STL/CLR)

Inverse l’ordre des éléments dans une plage source tout en les copiant dans une plage de destination.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `reverse_copy`. Pour plus d’informations, consultez [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).

## <a name="rotate"></a> faire pivoter (STL/CLR)

Échange les éléments de deux plages adjacentes.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `rotate`. Pour plus d’informations, consultez [pivoter](../standard-library/algorithm-functions.md#rotate).

## <a name="rotate_copy"></a> rotate_copy (STL/CLR)

Échange les éléments de deux plages adjacentes au sein d'une plage source et copie le résultat dans une plage de destination.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `rotate_copy`. Pour plus d’informations, consultez [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy).

## <a name="search_"></a> recherche (STL/CLR)

Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `search`. Pour plus d’informations, consultez [recherche](../standard-library/algorithm-functions.md#search).

## <a name="search_n"></a> search_n (STL/CLR)

Recherche la première sous-séquence d’une plage dont un nombre spécifié d’éléments ont une valeur particulière ou une relation à cette valeur, selon un prédicat binaire spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `search_n`. Pour plus d’informations, consultez [search_n](../standard-library/algorithm-functions.md#search_n).

## <a name="set_difference"></a> set_difference (STL/CLR)

Regroupe tous les éléments qui appartiennent à une plage source triée, mais pas à une autre plage source triée, en une même plage de destination triée. Un critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `set_difference`. Pour plus d’informations, consultez [set_difference](../standard-library/algorithm-functions.md#set_difference).

## <a name="set_intersection"></a> set_intersection (STL/CLR)

Regroupe tous les éléments de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `set_intersection`. Pour plus d’informations, consultez [set_intersection](../standard-library/algorithm-functions.md#set_intersection).

## <a name="set_symmetric_difference"></a> set_symmetric_difference (STL/CLR)

Regroupe tous les éléments qui appartiennent à l'une de deux plages sources triées (mais pas aux deux) au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `set_symmetric_difference`. Pour plus d’informations, consultez [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference).

## <a name="set_union"></a> set_union (STL/CLR)

Regroupe tous les éléments qui appartiennent au moins à l'une de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `set_union`. Pour plus d’informations, consultez [set_union](../standard-library/algorithm-functions.md#set_union).

## <a name="sort"></a> tri (STL/CLR)

Réorganise les éléments d’une plage spécifiée, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `sort`. Pour plus d’informations, consultez [tri](../mfc/reference/cmfclistctrl-class.md#sort).

## <a name="sort_heap"></a> sort_heap (STL/CLR)

Convertit un tas en une plage triée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `sort_heap`. Pour plus d’informations, consultez [sort_heap](../standard-library/algorithm-functions.md#sort_heap).

## <a name="stable_partition"></a> stable_partition (STL/CLR)

Classe les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas, et l’ordre relatif des éléments équivalents doit être conservé.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `stable_partition`. Pour plus d’informations, consultez [stable_partition](../standard-library/algorithm-functions.md#stable_partition).

## <a name="stable_sort"></a> stable_sort (STL/CLR)

Classe les éléments d’une plage spécifiée dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire, et conserve l’ordre relatif des éléments équivalents.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `stable_sort`. Pour plus d’informations, consultez [stable_sort](../standard-library/algorithm-functions.md#stable_sort).

## <a name="swap"></a> swap (STL/CLR)

Échange les valeurs des éléments de deux types d'objets, en assignant le contenu du premier objet au deuxième objet, et le contenu du deuxième au premier.

### <a name="syntax"></a>Syntaxe

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `swap`. Pour plus d’informations, consultez [échange](../standard-library/algorithm-functions.md#swap).

## <a name="swap_ranges"></a> swap_ranges (STL/CLR)

Échange les éléments d'une plage avec ceux d'une autre plage de taille égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `swap_ranges`. Pour plus d’informations, consultez [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges).

## <a name="transform"></a> transformation (STL/CLR)

Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `transform`. Pour plus d’informations, consultez [transformer](../standard-library/algorithm-functions.md#transform).

## <a name="unique"></a> unique (STL/CLR)

Supprime les éléments en double adjacents dans une plage spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `unique`. Pour plus d’informations, consultez [unique](../standard-library/algorithm-functions.md#unique).

## <a name="unique_copy"></a> unique_copy (STL/CLR)

Copie les éléments d'une plage source dans une plage de destination, à l'exception des éléments en double adjacents.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `unique_copy`. Pour plus d’informations, consultez [unique_copy](../standard-library/algorithm-functions.md#unique_copy).

## <a name="upper_bound"></a> upper_bound (STL/CLR)

Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Notes

Cette fonction comporte comme la fonction de bibliothèque Standard C++ `upper_bound`. Pour plus d’informations, consultez [upper_bound](../standard-library/algorithm-functions.md#upper_bound).