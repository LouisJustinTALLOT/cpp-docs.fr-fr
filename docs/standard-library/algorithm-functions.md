---
title: '&lt;algorithm&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.openlocfilehash: 5fdb5a89bc475cf2d6a358768b84b8542da5e0e8
ms.sourcegitcommit: d94714522428834a02ede6e6884572f0f6ca9824
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597562"
---
# <a name="ltalgorithmgt-functions"></a>&lt;algorithm&gt;, fonctions

||||
|-|-|-|
|[move](#alg_move)|[adjacent_find](#adjacent_find)|[all_of](#all_of)|
|[any_of](#any_of)|[binary_search](#binary_search)|[copy](#copy)|
|[copy_backward](#copy_backward)|[copy_if](#copy_if)|[copy_n](#copy_n)|
|[count](#count)|[count_if](#count_if)|[equal](#equal)|
|[equal_range](#equal_range)|[fill](#fill)|[fill_n](#fill_n)|
|[find](#find)|[find_end](#find_end)|[find_first_of](#find_first_of)|
|[find_if](#find_if)|[find_if_not](#find_if_not)|[for_each](#for_each)|
|[generate](#generate)|[generate_n](#generate_n)|[includes](#includes)|
|[inplace_merge](#inplace_merge)|[is_heap](#is_heap)|[is_heap_until](#is_heap_until)|
|[is_partitioned](#is_partitioned)|[is_permutation](#is_permutation)|[is_sorted](#is_sorted)|
|[is_sorted_until](#is_sorted_until)|[iter_swap](#iter_swap)|[lexicographical_compare](#lexicographical_compare)|
|[lower_bound](#lower_bound)|[make_heap](#make_heap)|[max](#max)|
|[max_element](#max_element)|[merge](#merge)|[min](#min)|
|[min_element](#min_element)|[minmax](#minmax)|[minmax_element](#minmax_element)|
|[mismatch](#mismatch)|[move_backward](#move_backward)|[next_permutation](#next_permutation)|
|[none_of](#none_of)|[nth_element](#nth_element)|[partial_sort](#partial_sort)|
|[partial_sort_copy](#partial_sort_copy)|[partition](#partition)|[partition_copy](#partition_copy)|
|[partition_point](#partition_point)|[pop_heap](#pop_heap)|[prev_permutation](#prev_permutation)|
|[push_heap](#push_heap)|[random_shuffle](#random_shuffle)|[remove](#remove)|
|[remove_copy](#remove_copy)|[remove_copy_if](#remove_copy_if)|[remove_if](#remove_if)|
|[replace](#replace)|[replace_copy](#replace_copy)|[replace_copy_if](#replace_copy_if)|
|[replace_if](#replace_if)|[reverse](#reverse)|[reverse_copy](#reverse_copy)|
|[rotate](#rotate)|[rotate_copy](#rotate_copy)|[search](#search)|
|[search_n](#search_n)|[set_difference](#set_difference)|[set_intersection](#set_intersection)|
|[set_symmetric_difference](#set_symmetric_difference)|[set_union](#set_union)|[sort](#sort)|
|[sort_heap](#sort_heap)|[stable_partition](#stable_partition)|[stable_sort](#stable_sort)|
|[shuffle](#shuffle)|[swap](#swap)|[swap_ranges](#swap_ranges)|
|[transform](#transform)|[unique](#unique)|[unique_copy](#unique_copy)|
|[upper_bound](#upper_bound)|

## <a name="adjacent_find"></a>  adjacent_find

Recherche deux éléments adjacents qui ont la même valeur ou qui répondent à une condition spécifiée.

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*comp*<br/>
Prédicat binaire indiquant la condition à satisfaire par les valeurs des éléments adjacents de la plage dans laquelle s’effectue la recherche.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant jusqu’au premier élément de la paire adjacente dont les éléments sont égaux entre eux (dans la première version) ou répondent à la condition spécifiée par le prédicat binaire (dans la seconde version), à condition que cette paire d’éléments soit trouvée. Sinon, un itérateur qui pointe vers *dernière* est retourné.

### <a name="remarks"></a>Notes

L'algorithme `adjacent_find` est un algorithme de séquence sans mutation. La plage dans laquelle s'effectue la recherche doit être valide. Tous les pointeurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible depuis la première par incrémentation. La complexité temporelle de l'algorithme est linéaire pour le nombre d'éléments contenus dans la plage.

`operator==`, qui sert à déterminer la correspondance entre des éléments, doit imposer une relation d'équivalence entre ses opérandes.

### <a name="example"></a>Exemple

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
   return elem1 * 2 == elem2;
}

int main()
{
   using namespace std;
   list <int> L;
   list <int>::iterator Iter;
   list <int>::iterator result1, result2;

   L.push_back( 50 );
   L.push_back( 40 );
   L.push_back( 10 );
   L.push_back( 20 );
   L.push_back( 20 );

   cout << "L = ( " ;
   for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
      cout << *Iter << " ";
   cout << ")" << endl;

   result1 = adjacent_find( L.begin( ), L.end( ) );
   if ( result1 == L.end( ) )
      cout << "There are not two adjacent elements that are equal."
           << endl;
   else
      cout << "There are two adjacent elements that are equal."
           << "\n They have a value of "
           <<  *( result1 ) << "." << endl;

   result2 = adjacent_find( L.begin( ), L.end( ), twice );
   if ( result2 == L.end( ) )
      cout << "There are not two adjacent elements where the "
           << " second is twice the first." << endl;
   else
      cout << "There are two adjacent elements where "
           << "the second is twice the first."
           << "\n They have values of " << *(result2++);
      cout << " & " << *result2 << "." << endl;
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>  all_of

Retourne **true** lorsqu’une condition est remplie pour chaque élément dans la plage donnée.

```cpp
template<class InputIterator, class Predicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    BinaryPredicatecomp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début de la recherche d’une condition. L’itérateur marque le début d’une plage d’éléments.

*last*<br/>
Itérateur d’entrée qui indique la fin d’une plage d’éléments dans laquelle rechercher une condition.

*comp*<br/>
Condition à vérifier. Il s’agit d’un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire par l’élément vérifié. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si la condition est détectée au niveau de chaque élément dans la plage spécifiée, et **false** si la condition n’est pas détectée au moins une fois.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si, pour chaque `N` dans la plage `[0,Last - first)`, le prédicat `comp(*(_First + N))` est **true**.

## <a name="any_of"></a>  any_of

Retourne **true** lorsqu’une condition est remplie au moins une fois dans la plage d’éléments spécifiée.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début de la recherche d’une condition dans une plage d’éléments.

*last*<br/>
Itérateur d’entrée qui indique la fin d’une plage d’éléments dans laquelle rechercher une condition.

*comp*<br/>
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur. Le prédicat définit la condition à satisfaire par l’élément vérifié. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si la condition est détectée au moins une fois dans la plage spécifiée, **false** si la condition n’est jamais détectée.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si, pour certains `N` dans la plage

`[0, last - first)`, le prédicat `comp(*(first + N))` a la valeur true.

## <a name="binary_search"></a>  binary_search

Teste si un élément d’une plage triée est égal à une valeur spécifiée ou équivalent, selon une condition spécifiée par un prédicat binaire.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator,  class Type,  class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*valeur*<br/>
Valeur qui doit correspondre à la valeur de l’élément ou qui doit satisfaire la condition avec la valeur d’élément spécifiée par le prédicat binaire.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si un élément est trouvé dans la plage est égal ou équivalente à la valeur spécifiée ; sinon, **false**.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Les plages triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `binary_search` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

Les plages sources ne sont pas modifiées par `binary_search`.

Les types valeur des itérateurs vers l’avant doivent être comparables en termes d’infériorité pour être triés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. De cette façon, les éléments non équivalents sont ordonnés

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire sinon, avec le nombre d’étapes proportionnel à (`last` - `first`).

### <a name="example"></a>Exemple

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    list <int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

## <a name="copy"></a>  copy

Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions, du haut vers le bas.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la plage source.

*last*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la plage source.

*destBeg*<br/>
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Un itérateur de sortie qui traite la position juste après le dernier élément dans la plage de destination, autrement dit, l’itérateur `result` + (*dernière* - *premier*).

### <a name="remarks"></a>Notes

La plage source doit être valide et il doit y avoir suffisamment d'espace au niveau de la destination pour contenir tous les éléments qui sont copiés.

Étant donné que l’algorithme copie les éléments sources dans l’ordre en commençant par le premier élément, la plage de destination peut chevaucher la plage source fournie le *dernière* position de la plage source n’est pas contenue dans la destination plage. `copy` peut être utilisé pour décaler des éléments vers la gauche mais pas sur la droite, sauf s’il en existe aucun chevauchement entre les plages source et destination. Pour décaler vers la droite d’un nombre quelconque de positions, utilisez l’algorithme [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

L'algorithme `copy` modifie uniquement les valeurs sur lesquelles pointent les itérateurs, assignant de nouvelles valeurs aux éléments dans la plage de destination. Il ne peut pas être utilisé pour créer de nouveaux éléments et ne peut pas insérer directement d'éléments dans un conteneur vide.

### <a name="example"></a>Exemple

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 10 * i );

   int ii;
   for ( ii = 0 ; ii <= 10 ; ii++ )
      v2.push_back( 3 * ii );

   cout << "v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To copy the first 3 elements of v1 into the middle of v2
   copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

   cout << "v2 with v1 insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To shift the elements inserted into v2 two positions
   // to the left
   copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

   cout << "v2 with shifted insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a>  copy_backward

Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions vers le haut.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel se rapportant à la position du premier élément dans la plage source.

*last*<br/>
Itérateur bidirectionnel se rapportant à la position située immédiatement après l'élément final dans la plage source.

*destEnd*<br/>
Itérateur bidirectionnel se rapportant à la position située immédiatement après l'élément final dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Un itérateur de sortie qui traite la position juste après le dernier élément dans la plage de destination, autrement dit, l’itérateur *destEnd* -(*dernière* - *premier*).

### <a name="remarks"></a>Notes

La plage source doit être valide et il doit y avoir suffisamment d'espace au niveau de la destination pour contenir tous les éléments qui sont copiés.

L'algorithme `copy_backward` impose des exigences plus strictes que celles de l'algorithme de copie. Ses itérateurs d'entrée et de sortie doivent être bidirectionnels.

Les algorithmes `copy_backward` et [move_backward](../standard-library/algorithm-functions.md#move_backward) sont les seuls algorithmes de la bibliothèque C++ Standard qui désignent la plage de sortie avec un itérateur pointant vers la fin de la plage de destination.

Étant donné que l’algorithme copie les éléments sources dans l’ordre en commençant par le dernier élément, la plage de destination peut chevaucher la plage source fournie le *premier* position de la plage source n’est pas contenue dans la destination plage. `copy_backward` peut être utilisé pour décaler des éléments vers la droite mais pas vers la gauche, à moins qu'il n'y ait aucun chevauchement entre la plage source et celle de destination. Pour décaler vers la gauche d’un nombre quelconque de positions, utilisez l’algorithme [copy](../standard-library/algorithm-functions.md#copy).

L'algorithme `copy_backward` modifie uniquement les valeurs sur lesquelles pointent les itérateurs, assignant de nouvelles valeurs aux éléments dans la plage de destination. Il ne peut pas être utilisé pour créer de nouveaux éléments et ne peut pas insérer directement d'éléments dans un conteneur vide.

### <a name="example"></a>Exemple

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 5 ; ++i )
      v1.push_back( 10 * i );

   int ii;
   for ( ii = 0 ; ii <= 10 ; ++ii )
      v2.push_back( 3 * ii );

   cout << "v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To copy_backward the first 3 elements of v1 into the middle of v2
   copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

   cout << "v2 with v1 insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To shift the elements inserted into v2 two positions
   // to the right
   copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

   cout << "v2 with shifted insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

## <a name="copy_if"></a>  copy_if

Dans une plage d’éléments, copie les éléments qui sont **true** pour la condition spécifiée.

```cpp
template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début d’une plage dans laquelle rechercher la condition.

*last*<br/>
Itérateur d’entrée qui indique la fin de la plage.

*dest*<br/>
Itérateur de sortie qui indique la destination des éléments copiés.

*_Pred*<br/>
Condition pour laquelle chaque élément de la plage est vérifié. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur. Un prédicat accepte un argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Un itérateur de sortie est égal à *dest* incrémenté une fois pour chaque élément qui répond à la condition. En d’autres termes, la valeur de retour moins *dest* est égal au nombre d’éléments copiés.

### <a name="remarks"></a>Notes

La fonction de modèle évalue

`if (pred(*_First + N)) * dest++ = *(_First + N))`

une fois pour chaque `N` de la plage `[0, last - first)`, pour les valeurs strictement croissantes de `N` en commençant par la valeur la plus petite. Si *dest* et *première* désignent des régions de stockage, *dest* ne doit pas être dans la plage `[ first, last )`.

## <a name="copy_n"></a>  copy_n

Copie un nombre spécifié d'éléments.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d'entrée qui indique l'emplacement à partir duquel les éléments doivent être copiés.

*count*<br/>
Type entier signé ou non signé spécifiant le nombre d'éléments à copier.

*dest*<br/>
Itérateur de sortie qui indique l'emplacement où les éléments doivent être copiés.

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur de sortie indiquant où les éléments ont été copiés. Il est identique à la valeur retournée du troisième paramètre, *dest*.

### <a name="remarks"></a>Notes

La fonction de modèle évalue `*(dest + N) = *(first + N))` une fois pour chaque `N` dans la plage `[0, count)`, pour les valeurs strictement croissantes de `N` en commençant par la valeur la plus basse. Elle retourne ensuite `dest + N`. Si *dest* et *première* désignent des régions de stockage, *dest* ne doit pas être dans la plage `[first, last)`.

## <a name="count"></a>  count

Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée ciblant la position du premier élément de la plage à traverser.

*last*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la plage à traverser.

*Val*<br/>
Valeur des éléments à compter.

### <a name="return-value"></a>Valeur de retour

Le type de différence de la `InputIterator` qui compte le nombre d’éléments dans la plage [ *première*, *dernière* ) ayant une valeur *val*.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Cet algorithme est généralisé pour compter les éléments qui satisfont un prédicat avec la fonction de modèle [count_if](../standard-library/algorithm-functions.md#count_if).

### <a name="example"></a>Exemple

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a>  count_if

Retourne le nombre d’éléments d’une plage dont les valeurs satisfont une condition spécifiée.

```cpp
template<class InputIterator, class Predicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d'entrée qui traite la position du premier élément de la plage à rechercher.

*last*<br/>
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage à rechercher.

*_Pred*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire si un élément doit être compté. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments qui satisfont la condition spécifiée par le prédicat.

### <a name="remarks"></a>Notes

Cette fonction de modèle est une généralisation de l’algorithme [count](../standard-library/algorithm-functions.md#count) et remplace le prédicat « est égal à une valeur spécifique » par un autre prédicat.

### <a name="example"></a>Exemple

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a>  equal

Compare deux plages, élément par élément, à la recherche d’une égalité ou d’une équivalence, selon une condition spécifiée par un prédicat binaire.

Utilisez `std::equal` quand vous comparez des éléments de différents types de conteneurs (par exemple `vector` et `list`) ou différents types d’éléments, ou quand vous devez comparer des sous-plages de conteneurs. Sinon, quand vous comparez des éléments du même type dans le même type de conteneur, utilisez l’`operator==` de non-membre fourni pour chaque conteneur.

Utilisez les surcharges à double portée dans le code C++14, car les surcharges qui ne prennent qu'un seul itérateur pour la deuxième plage ne détecteront pas les différences si la deuxième plage est plus longue que la première et provoqueront un comportement non défini si la deuxième plage est plus courte que la première.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    BinaryPredicate Comp); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    InputIterator2  Last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    InputIterator2  Last2,
    BinaryPredicate Comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d'entrée qui traite la position du premier élément de la première plage à tester.

*last1*<br/>
Itérateur d'entrée qui traite la position qui suit le dernier élément de la première plage à tester.

*first2*<br/>
Itérateur d'entrée qui traite la position du premier élément de la deuxième plage à tester.

*first2*<br/>
Itérateur d'entrée qui traite la position qui suit le dernier élément de la deuxième plage à tester.

*Comp.*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si et seulement si les plages sont identiques ou équivalentes sous le prédicat binaire en cas de comparaison élément par élément ; sinon, **false**.

### <a name="remarks"></a>Notes

La plage dans laquelle s'effectue la recherche doit être valide. Tous les itérateurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible depuis la première par incrémentation.

Si les deux plages sont de longueur égale, la complexité temporelle de l'algorithme est linéaire quant au nombre d'éléments contenus dans la plage. Sinon, la fonction retourne immédiatement **false**.

Ni le `operator==`, ni le prédicat défini par l'utilisateur ne doit obligatoirement imposer une relation d'équivalence qui est symétrique, réflexive et transitive entre ses opérandes.

### <a name="example"></a>Exemple

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}
```

## <a name="equal_range"></a>  equal_range

Dans une plage ordonnée définie, recherche la sous-plage dans laquelle tous les éléments sont équivalents à une valeur donnée.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val);

template<class ForwardIterator, class Type, class Predicate>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val,
    Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*Val*<br/>
Valeur recherchée dans la plage ordonnée.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre.

### <a name="return-value"></a>Valeur de retour

Une paire d’itérateurs qui spécifient une sous-plage contenue dans la plage de recherche, dans lequel tous les éléments sont équivalents à *val* selon la logique définie par le prédicat binaire utilisé (soit *comp* ou la valeur par défaut, moins-que).

Si aucun élément dans la plage n’est équivalentes aux *val*, la paire retournée d’itérateurs sont égale et spécifient le point où *val* peut être inséré sans porter atteinte à l’ordre de la plage.

### <a name="remarks"></a>Notes

Le premier itérateur de la paire retournée par l’algorithme est [lower_bound](../standard-library/algorithm-functions.md#lower_bound) et le deuxième est [upper_bound](../standard-library/algorithm-functions.md#upper_bound).

La plage doit être triée selon le prédicat fourni à `equal_range`. Par exemple, si vous comptez utiliser le prédicat Supérieur à, la plage doit être triée par ordre décroissant.

Éléments de la sous-plage éventuellement vide définie par la paire d’itérateurs retournés par `equal_range` équivaut à *val* selon la logique définie par le prédicat utilisé.

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire sinon, avec le nombre d’étapes proportionnel à (*dernière* - *premier*).

### <a name="example"></a>Exemple

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T val )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), val );

    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T val, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), val, pred );

    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}
```

## <a name="fill"></a>  fill

Affecte la même nouvelle valeur à chaque élément d'une plage spécifiée.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage à traverser.

*last*<br/>
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage à traverser.

*Val*<br/>
La valeur à affecter aux éléments dans la plage [ *première*, *dernière*).

### <a name="remarks"></a>Notes

La plage de destination doit être valide. Tous les pointeurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible à partir de la première par incrémentation. La complexité est linéaire par rapport à la taille de la plage.

### <a name="example"></a>Exemple

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Fill the last 5 positions with a value of 2
   fill( v1.begin( ) + 5, v1.end( ), 2 );

   cout << "Modified v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a>  fill_n

Attribue une nouvelle valeur à un nombre spécifié d’éléments d’une plage commençant par un élément particulier.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator First,
    Size Count,
    const Type& Val);
```

### <a name="parameters"></a>Paramètres

*Premier*<br/>
Itérateur de sortie ciblant la position du premier élément de la plage à affecter la valeur *Val*.

*Nombre*<br/>
Type entier signé ou non signé spécifiant le nombre d’éléments auxquels attribuer une valeur.

*Val*<br/>
La valeur à affecter aux éléments dans la plage [ *première*, *First + Count*).

### <a name="return-value"></a>Valeur de retour

Un itérateur vers l’élément qui suit le dernier élément rempli si *nombre* > égal à zéro, sinon le premier élément.

### <a name="remarks"></a>Notes

La plage de destination doit être valide. Tous les pointeurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible à partir de la première par incrémentation. La complexité est linéaire par rapport à la taille de la plage.

### <a name="example"></a>Exemple

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector <int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << "  vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}
```

## <a name="find"></a>  find

Recherche la position de la première occurrence d'un élément d'une plage ayant une valeur spécifiée.

```cpp
template<class InputIterator, class T>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const T& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d'entrée qui traite la position du premier élément de la plage où effectuer la recherche de la valeur spécifiée.

*last*<br/>
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage où effectuer la recherche de la valeur spécifiée.

*Val*<br/>
Valeur à rechercher.

### <a name="return-value"></a>Valeur de retour

Itérateur d'entrée qui traite la première occurrence de la valeur spécifiée dans la plage où effectuer la recherche. Si aucun élément n’est trouvé avec une valeur équivalente, retourne *dernière*.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Pour obtenir un exemple de code avec `find()`, consultez [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="find_end"></a>  find_end

Recherche dans une plage la dernière sous-séquence qui est identique à une séquence spécifiée ou qui est équivalente, selon une condition spécifiée par un prédicat binaire.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2,
    Pred Comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*first2*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last2*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*Comp.*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l'avant qui traite la position du premier élément de la dernière sous-séquence dans [First1, Last1) qui correspond à la séquence spécifiée [First2, Last2).

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

### <a name="example"></a>Exemple

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for a match to L1 under identity
   vector <int>::iterator result1;
   result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a match of L1 in v1 that begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent to those\n in v2 under the binary "
           << "predicate twice and that begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a>  find_first_of

Recherche la première occurrence parmi plusieurs valeurs d’une plage cible, ou la première occurrence parmi plusieurs éléments qui sont équivalents, selon une condition spécifiée par un prédicat binaire, à un ensemble d’éléments spécifiés.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1  first1,
    ForwardIterator1 Last1,
    ForwardIterator2  first2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1  first1,
    ForwardIterator1 Last1,
    ForwardIterator2  first2,
    ForwardIterator2 Last2,
    BinaryPredicate  comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*first2*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la correspondance.

*last2*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la correspondance.

*comp*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la position du premier élément de la première sous-séquence qui correspond à la séquence spécifiée ou qui est équivalente au sens spécifié par un prédicat binaire.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

### <a name="example"></a>Exemple

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 3 ; ii <= 4 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for first match to L1 under identity
   vector <int>::iterator result1;
   result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is at least one match of L1 in v1"
           << "\n and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent\n to those in v2 under the binary "
           << "predicate twice\n and the first one begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="find_if"></a>  find_if

Recherche la position de la première occurrence d'un élément d'une plage qui répond à une condition spécifiée.

```cpp
template<class InputIterator, class Predicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d'entrée qui traite la position du premier élément de la plage à rechercher.

*last*<br/>
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage à rechercher.

*Pred*<br/>
Objet de fonction de prédicat défini par l’utilisateur ou [expression lambda](../cpp/lambda-expressions-in-cpp.md) qui définit la condition à satisfaire par l’élément recherché. Un prédicat accepte un seul argument et retourne **true** (satisfaite) ou **false** (ne pas satisfaite). La signature de *pred* doit être efficacement `bool pred(const T& arg);`, où `T` est un type auquel `InputIterator` peut être converti implicitement quand il est déréférencé. Le **const** mot clé s’affiche uniquement pour montrer que l’objet de fonction ou une expression lambda ne devez pas modifier l’argument.

### <a name="return-value"></a>Valeur de retour

Itérateur d’entrée qui fait référence au premier élément dans la plage qui satisfait la condition spécifiée par le prédicat (le prédicat retourne **true**). Si aucun élément n’est trouvé pour satisfaire le prédicat, retourne *dernière*.

### <a name="remarks"></a>Notes

Cette fonction de modèle est une généralisation de l’algorithme [find](../standard-library/algorithm-functions.md#find) et remplace le prédicat « est égal à une valeur spécifique » par un autre prédicat. Pour l’opposé logique (rechercher le premier élément qui ne satisfait pas le prédicat), consultez [find_if_not](../standard-library/algorithm-functions.md#find_if_not).

### <a name="example"></a>Exemple

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}
```

## <a name="find_if_not"></a>  find_if_not

Retourne le premier élément d'une plage spécifiée qui ne répond pas à une condition.

```cpp
template<class InputIterator, class Predicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d'entrée qui traite la position du premier élément de la plage à rechercher.

*last*<br/>
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage à rechercher.

*Pred*<br/>
Objet de fonction de prédicat défini par l’utilisateur ou [expression lambda](../cpp/lambda-expressions-in-cpp.md) qui définit la condition à ne pas satisfaire par l’élément recherché. Un prédicat accepte un seul argument et retourne **true** (satisfaite) ou **false** (ne pas satisfaite). La signature de *pred* doit être efficacement `bool pred(const T& arg);`, où `T` est un type auquel `InputIterator` peut être converti implicitement quand il est déréférencé. Le **const** mot clé s’affiche uniquement pour montrer que l’objet de fonction ou une expression lambda ne devez pas modifier l’argument.

### <a name="return-value"></a>Valeur de retour

Itérateur d’entrée qui fait référence au premier élément dans la plage qui ne satisfait pas la condition spécifiée par le prédicat (le prédicat retourne **false**). Si tous les éléments répondent au prédicat (le prédicat retourne **true** pour chaque élément), retourne *dernière*.

### <a name="remarks"></a>Notes

Cette fonction de modèle est une généralisation de l’algorithme [find](../standard-library/algorithm-functions.md#find) et remplace le prédicat « est égal à une valeur spécifique » par un autre prédicat. Pour l’opposé logique (rechercher le premier élément qui satisfait le prédicat), consultez [find_if](../standard-library/algorithm-functions.md#find_if).

Pour obtenir un exemple de code facilement adaptable à `find_if_not()`, consultez [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a>  for_each

Applique un objet de fonction spécifié à chaque élément d'une plage, du haut vers le bas, et retourne l'objet de la fonction.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée ciblant la position du premier élément de la plage à traiter.

*last*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la plage à traiter.

*_Func*<br/>
Objet de fonction défini par l’utilisateur appliqué à chaque élément de la plage.

### <a name="return-value"></a>Valeur de retour

Copie de l’objet de fonction une fois qu’il a été appliqué à tous les éléments de la plage.

### <a name="remarks"></a>Notes

L’algorithme `for_each` est très souple et autorise la modification de chaque élément d’une plage de différentes façons spécifiées par l’utilisateur. Vous pouvez réutiliser des fonctions modélisées sous une forme modifiée en passant des paramètres différents. Les fonctions définies par l’utilisateur peuvent accumuler des informations dans un état interne que l’algorithme peut retourner après le traitement de tous les éléments de la plage.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire au maximum ( *dernière* -  *premier*) comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
   Type Factor;   // The value to multiply by
public:
   // Constructor initializes the value to multiply by
   MultValue ( const Type& val ) : Factor ( val ) {
   }

   // The function call for the element to be multiplied
   void operator( ) ( Type& elem ) const
   {
      elem *= Factor;
   }
};

// The function object to determine the average
class Average
{
private:
   long num;      // The number of elements
   long sum;      // The sum of the elements
public:
   // Constructor initializes the value to multiply by
   Average( ) : num ( 0 ) , sum ( 0 )
   {
   }

   // The function call to process the next elment
   void operator( ) ( int elem ) \
   {
      num++;      // Increment the element count
      sum += elem;   // Add the value to the partial sum
   }

   // return Average
   operator double( )
   {
      return  static_cast <double> (sum) /
      static_cast <double> (num);
   }
};

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   // Constructing vector v1
   int i;
   for ( i = -4 ; i <= 2 ; i++ )
   {
      v1.push_back(  i );
   }

   cout << "Original vector  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Using for_each to multiply each element by a Factor
   for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

   cout << "Multiplying the elements of the vector v1\n "
        <<  "by the factor -2 gives:\n v1mod1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // The function object is templatized and so can be
   // used again on the elements with a different Factor
   for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

   cout << "Multiplying the elements of the vector v1mod\n "
        <<  "by the factor 5 gives:\n v1mod2 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // The local state of a function object can accumulate
   // information about a sequence of actions that the
   // return value can make available, here the Average
   double avemod2 = for_each ( v1.begin( ), v1.end( ),
      Average( ) );
   cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
        << avemod2 << "." << endl;
}
```

```Output
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="generate"></a>  generate

Assigne les valeurs générées par un objet de fonction à chaque élément d'une plage.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator _Gen);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage auquel les valeurs doivent être attribuées.

*last*<br/>
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage auquel les valeurs doivent être attribuées.

*_Gen*<br/>
Objet de fonction qui est appelé sans argument qui permet de générer les valeurs à assigner à chacun des éléments de la plage.

### <a name="remarks"></a>Notes

L'objet de fonction est appelé pour chaque élément de la plage et n'a pas besoin de retourner la même valeur à chaque appel. Il peut, par exemple, lire un fichier ou référencer et modifier un état local. Le type de résultat du générateur doit être convertible dans le type de valeur des itérateurs de transfert pour la plage.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire, avec exactement ( `last`  -   `first`) appels au générateur demandé.

### <a name="example"></a>Exemple

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
   using namespace std;

   // Assigning random values to vector integer elements
   vector <int> v1 ( 5 );
   vector <int>::iterator Iter1;
   deque <int> deq1 ( 5 );
   deque <int>::iterator d1_Iter;

   generate ( v1.begin( ), v1.end( ), rand );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Assigning random values to deque integer elements
   generate ( deq1.begin( ), deq1.end( ), rand );

   cout << "Deque deq1 is ( " ;
   for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
      cout << *d1_Iter << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a>  generate_n

Assigne les valeurs générées par un objet de fonction à un nombre spécifié d'éléments d'une plage et retourne à la position située juste après la dernière valeur assignée.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator First,
    Diff Count,
    Generator Gen);
```

### <a name="parameters"></a>Paramètres

*Premier*<br/>
Itérateur de sortie se rapportant à la position du premier élément dans la plage auquel les valeurs doivent être assignées.

*Nombre*<br/>
Type entier signé ou non signé spécifiant le nombre d'éléments auxquels une valeur doit être assignée par la fonction de générateur.

*Gen*<br/>
Objet de fonction qui est appelé sans argument qui permet de générer les valeurs à assigner à chacun des éléments de la plage.

### <a name="remarks"></a>Notes

L'objet de fonction est appelé pour chaque élément de la plage et n'a pas besoin de retourner la même valeur à chaque appel. Il peut, par exemple, lire un fichier ou référencer et modifier un état local. Le type de résultat du générateur doit être convertible dans le type de valeur des itérateurs de transfert pour la plage.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire, avec exactement `Count` appels au générateur requis.

### <a name="example"></a>Exemple

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}
```

## <a name="includes"></a>  includes

Teste si une plage triée contient tous les éléments d’une autre plage triée. Le critère de tri ou d’équivalence entre les éléments peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément de la première de deux plages sources triées à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*last1*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la première de deux plages sources triées à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément de la deuxième de deux plages sources triées consécutives à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*last2*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la deuxième de deux plages sources triées consécutives à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si la première plage triée contient tous les éléments de la deuxième ; sinon, **false**.

### <a name="remarks"></a>Notes

Une autre façon d’interpréter ce test est de déterminer si la deuxième plage source est un sous-ensemble de la première plage source.

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Les plages sources triées doivent chacune être organisées comme une condition préalable à l’application de l’algorithme includes selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

Les plages sources ne sont pas modifiées par l’algorithme `merge`.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Plus précisément, l’algorithme vérifie si tous les éléments de la première plage triée sous un prédicat binaire spécifié sont ordonnés de la même façon que ceux de la deuxième plage triée.

La complexité de l’algorithme est linéaire avec au maximum 2 \* (( *last1 - first1*)-(* last2 - first2 *)) - 1 comparaisons pour des plages sources non vides.

### <a name="example"></a>Exemple

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b;
   vector <int>::iterator Iter1a,  Iter1b;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -2 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-2 ; ii <= 3 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        << "binary predicate less than is v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b );
   vector <int>::iterator Iter2a,  Iter2b;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
   v2a.pop_back( );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is v2a = ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is v2b = ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ;
   vector <int>::iterator Iter3a, Iter3b;
   reverse (v3a.begin( ), v3a.end( ) );
   v3a.pop_back( );
   v3a.pop_back( );
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3a = ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3b = ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To test for inclusion under an asscending order
   // with the default binary predicate less <int>( )
   bool Result1;
   Result1 = includes ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ) );
   if ( Result1 )
      cout << "All the elements in vector v1b are "
           << "contained in vector v1a." << endl;
   else
      cout << "At least one of the elements in vector v1b "
           << "is not contained in vector v1a." << endl;

   // To test for inclusion under descending
   // order specify binary predicate greater<int>( )
   bool Result2;
   Result2 = includes ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ), greater <int>( ) );
   if ( Result2 )
      cout << "All the elements in vector v2b are "
           << "contained in vector v2a." << endl;
   else
      cout << "At least one of the elements in vector v2b "
           << "is not contained in vector v2a." << endl;

   // To test for inclusion under a user
   // defined binary predicate mod_lesser
   bool Result3;
   Result3 = includes ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), mod_lesser );
   if ( Result3 )
      cout << "All the elements in vector v3b are "
           << "contained under mod_lesser in vector v3a."
           << endl;
   else
      cout << "At least one of the elements in vector v3b is "
           << " not contained under mod_lesser in vector v3a."
           << endl;
}
```

```Output
Original vector v1a with range sorted by the
binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is  not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>  inplace_merge

Regroupe les éléments de deux plages triées consécutives au sein d’une même plage triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Predicate>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la première de deux plages triées consécutives à regrouper en une seule plage et trier.

*Milieu*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la deuxième de deux plages triées consécutives à regrouper en une seule plage et trier.

*last*<br/>
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la deuxième de deux plages triées consécutives à regrouper en une seule plage et trier.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Les plages triées consécutives référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Les plages triées consécutives doivent chacune être organisées comme une condition préalable à l’application de l’algorithme `inplace_merge` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées. L’opération est stable, car l’ordre relatif des éléments de chaque plage est préservé. Quand il existe des éléments équivalents dans les deux plages sources, l’élément de la première plage précède celui de la deuxième dans la plage regroupée.

La complexité dépend de la mémoire disponible, car l’algorithme alloue de la mémoire à une mémoire tampon temporaire. Si la mémoire disponible est suffisante, le meilleur des cas sont linéaire avec (*dernière* - *première*) - 1 comparaisons ; si aucune mémoire auxiliaire n’est disponible, le pire des cas sont *N*journal (*N*), où *N* = (*dernière* - *premier*).

### <a name="example"></a>Exemple

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2, Iter3;

   // Constructing vector v1 with default less-than ordering
   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =-5 ; ii <= 0 ; ii++ )
   {
      v1.push_back(  ii  );
   }

   cout << "Original vector v1 with subranges sorted by the\n "
        <<  "binary predicate less than is  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Constructing vector v2 with ranges sorted by greater
   vector <int> v2 ( v1 );
   vector <int>::iterator break2;
   break2 = find ( v2.begin( ), v2.end( ), -5 );
   sort ( v2.begin( ), break2 , greater<int>( ) );
   sort ( break2 , v2.end( ), greater<int>( ) );
   cout << "Original vector v2 with subranges sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Constructing vector v3 with ranges sorted by mod_lesser
   vector <int> v3 ( v1 );
   vector <int>::iterator break3;
   break3 = find ( v3.begin( ), v3.end( ), -5 );
   sort ( v3.begin( ), break3 , mod_lesser );
   sort ( break3 , v3.end( ), mod_lesser );
   cout << "Original vector v3 with subranges sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;

   vector <int>::iterator break1;
   break1 = find (v1.begin( ), v1.end( ), -5 );
   inplace_merge ( v1.begin( ), break1, v1.end( ) );
   cout << "Merged inplace with default order,\n vector v1mod = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To merge inplace in descending order, specify binary
   // predicate greater<int>( )
   inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
   cout << "Merged inplace with binary predicate greater specified,\n "
        << "vector v2mod = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Applying a user defined (UD) binary predicate mod_lesser
   inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "
        << "vector v3mod = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
binary predicate less than is  v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a>  is_heap

Retourne **true** si les éléments dans la plage spécifiée forment un segment de mémoire.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire qui indique le début d’une plage dans laquelle rechercher un tas.

*last*<br/>
Itérateur d’accès aléatoire qui indique la fin d’une plage.

*comp*<br/>
Condition à vérifier pour ordonner des éléments. Un prédicat binaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si les éléments dans la plage spécifiée forment un tas, **false** s’ils ne le font pas.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`.

La deuxième fonction de modèle retourne

`is_heap_until(first, last, comp) == last`.

## <a name="is_heap_until"></a>  is_heap_until

Retourne un itérateur pointant vers le premier élément dans la plage [ `begin`, `end`) qui ne satisfait pas la condition d’ordonnancement du tas ou *fin* si la plage forme un tas.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator begin,
    RandomAccessIterator end);

template<class RandomAccessIterator, class BinaryPredicate>
RandomAccessIterator is_heap_until(
    RandomAccessIterator begin,
    RandomAccessIterator end,
    BinaryPredicate compare);
```

### <a name="parameters"></a>Paramètres

*begin*<br/>
Itérateur à accès aléatoire qui spécifie le premier élément d'une plage dans laquelle effectuer la recherche d'un tas.

*end*<br/>
Itérateur à accès aléatoire qui spécifie le dernier élément de la plage où effectuer la recherche d'un tas.

*compare*<br/>
Prédicat binaire qui spécifie la condition d'ordonnancement faible strict qui définit un tas. Le prédicat par défaut lorsque *comparer* n’est pas spécifié est `std::less<>`.

### <a name="return-value"></a>Valeur de retour

Retourne *fin* si la plage spécifiée forme un tas ou contient un élément au maximum. Sinon, retourne un itérateur pointant vers le premier élément trouvé qui ne remplit pas la condition de tas.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne le dernier itérateur `next` dans `[ begin , end ]` où `[ begin , next)` est un tas ordonné par l’objet de fonction `std::less<>`. Si la distance `end - begin < 2`, la fonction retourne *fin*.

La deuxième fonction de modèle se comporte comme la première, sauf qu'elle utilise le prédicat `compare` à la place du prédicat `std::less<>` comme condition d'ordonnancement du tas.

## <a name="is_partitioned"></a>  is_partitioned

Retourne **true** si tous les éléments dans la plage donnée qui testent **true** pour une condition se trouvent avant les éléments qui testent **false**.

```cpp
template<class InputIterator, class BinaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début de la recherche d’une condition dans une plage.

*last*<br/>
Itérateur d’entrée qui indique la fin d’une plage.

*comp*<br/>
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire par l’élément recherché. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne true lorsque tous les éléments dans la plage donnée qui testent **true** pour une condition se trouvent avant les éléments qui testent **false**, sinon retourne **false**.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si tous les éléments de `[` `first ,` `last )` sont partitionnés par *comp*; autrement dit, tous les éléments `X` dans `[` `first ,` `last )` pour lequel `comp (X)` est true se produisent avant tous les éléments `Y` pour lequel `comp (Y)` est **false**.

## <a name="is_permutation"></a>  is_permutation

Retourne la valeur true si les deux plages contiennent les mêmes éléments, même s'ils ne sont pas dans le même ordre. Utilisez les surcharges à double portée dans le code C++14, car les surcharges qui ne prennent qu'un seul itérateur pour la deuxième plage ne détecteront pas les différences si la deuxième plage est plus longue que la première et provoqueront un comportement non défini si la deuxième plage est plus courte que la première.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    Predicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2,
    Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur vers l'avant qui fait référence au premier élément de la plage.

*last1*<br/>
Itérateur vers l'avant qui fait référence à l'élément qui suit le dernier élément de la plage.

*first2*<br/>
Itérateur vers l'avant qui fait référence au premier élément d'une deuxième plage, utilisé à des fins de comparaison.

*last2*<br/>
Itérateur vers l'avant qui fait référence à l'élément qui suit le dernier élément d'une deuxième plage, utilisé à des fins de comparaison.

*Pred*<br/>
Un prédicat qui teste l’équivalence et retourne un **bool**.

### <a name="return-value"></a>Valeur de retour

**true** lorsque les plages peuvent être réorganisées pour être identiques en fonction du prédicat de comparaison ; sinon, **false**.

### <a name="remarks"></a>Notes

`is_permutation` a une complexité quadratique dans le pire des cas.

La première fonction avec modèle part du principe qu’il existe autant d’éléments dans la plage commençant par *First2* qu’il y a dans la plage désignée par [ `First1`, `Last1`). S'il y a plus d'éléments dans la deuxième plage, ils sont ignorés ; s'il y en a moins, le comportement est non défini. La troisième fonction de modèle (C++14 et versions ultérieures) ne part pas de ce principe.  Les deux renvoient **true** uniquement si, pour chaque élément X dans la plage désignée par [ `First1`, `Last1`) il existe autant d’éléments Y dans la même plage pour lesquels X == Y qu’il existe dans la plage commençant par *First2* ou [ `First2, Last2).` ici, `operator==` doit effectuer une comparaison par paire entre ses opérandes.

Les deuxième et quatrième fonctions avec modèle ont le même comportement, hormis le fait qu'elles remplacent `operator==(X, Y)` par `Pred(X, Y)`. Pour se comporter correctement, le prédicat doit être symétrique, réflexif et transitif.

### <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser `is_permutation` :

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}
```

## <a name="is_sorted"></a>  is_sorted

Retourne **true** si les éléments dans la plage spécifiée sont dans un ordre trié.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant qui indique où commence la plage à vérifier.

*last*<br/>
Itérateur vers l’avant qui indique la fin d’une plage.

*comp*<br/>
Condition à vérifier pour déterminer un ordre entre deux éléments. Un prédicat accepte un seul argument et retourne **true** ou **false**. Il effectue la même tâche que `operator<`.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne [is_sorted_until](#is_sorted_until)`( first, last ) == last`. Le `operator<` fonction compare l’ordre.

La deuxième fonction de modèle retourne `is_sorted_until( first, last , comp ) == last`. Le *comp* fonction de prédicat compare l’ordre.

## <a name="is_sorted_until"></a>  is_sorted_until

Retourne un `ForwardIterator` défini sur le dernier élément qui se trouve dans l’ordre trié d’une plage spécifiée.

La deuxième version vous permet de fournir un `BinaryPredicate` fonction qui retourne **true** lorsque deux éléments donnés sont triés, et **false** dans le cas contraire.

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);
template<class ForwardIterator, class BinaryPredicate>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant qui indique où commence la plage à vérifier.

*last*<br/>
Itérateur vers l’avant qui indique la fin d’une plage.

*comp*<br/>
Condition à vérifier pour déterminer un ordre entre deux éléments. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne un `ForwardIterator` défini sur le dernier élément dans un ordre trié. La séquence triée commence à partir de *premier*.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne le dernier itérateur `next` de `[` `first ,` `last ]` pour que `[` `first , next)` soit une séquence triée par `operator<`. Si `distance()` `< 2` la fonction retourne *dernière*.

La deuxième fonction de modèle se comporte de la même façon, sauf qu’elle remplace `operator<(X, Y)` par `comp (X, Y)`.

## <a name="iter_swap"></a>  iter_swap

Échange deux valeurs référencées par une paire d'itérateurs spécifiés.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Un des itérateurs vers l’avant dont la valeur est à échanger.

*right*<br/>
Le deuxième des itérateurs vers l’avant dont la valeur est à échanger.

### <a name="remarks"></a>Notes

`swap` doit être utilisé en priorité par rapport à i**ter_swap**, qui a été inclus dans la norme C++ pour la compatibilité descendante. Si `Fit1` et `Fit2` sont des itérateurs vers l’avant, puis `iter_swap` ( `Fit1`, `Fit2` ), est équivalent à `swap` ( \* `Fit1`, \* `Fit2` ).

Les types valeur des itérateurs vers l’avant/d’entrée doivent avoir la même valeur.

### <a name="example"></a>Exemple

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) { m_nVal =
   rhs.m_nVal; return *this; }
   bool operator<( const CInt& rhs ) const
      { return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt(" << rhs.m_nVal << ")";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   CInt c1 = 5, c2 = 1, c3 = 10;
   deque<CInt> deq1;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Exchanging first and last elements with iter_swap
   iter_swap ( deq1.begin( ), --deq1.end( ) );

   cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Swapping back first and last elements with swap
   swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

   cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Swapping a vector element with a deque element
   vector <int> v1;
   vector <int>::iterator Iter1;
   deque <int> deq2;
   deque <int>::iterator d2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 4 ; ii <= 5 ; ii++ )
   {
      deq2.push_back( ii );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Deque deq2 is ( " ;
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
      cout << *d2_Iter << " ";
   cout << ")." << endl;

   iter_swap ( v1.begin( ), deq2.begin( ) );

   cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
      cout << *d2_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
vector v1 is: v1 = ( 4 1 2 3 ).
& deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a>  lexicographical_compare

Compare deux séquences, élément par élément, pour déterminer lequel est inférieur à l'autre.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1  first1,
    InputIterator1 Last1,
    InputIterator2  first2,
    InputIterator2 Last2  );

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool lexicographical_compare(
    InputIterator1  first1,
    InputIterator1 Last1,
    InputIterator2  first2,
    InputIterator2 Last2,
    BinaryPredicate  comp  );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément de la première plage à comparer.

*last1*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la première plage à comparer.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément de la deuxième plage à comparer.

*last2*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la deuxième plage à comparer.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si la première plage est inférieure à la deuxième plage d’un point de vue lexicographique ; sinon **false**.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre séquences les compare élément par élément jusqu’à ce que :

- Elle trouve deux éléments correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les séquences.

- Aucune inégalité n’est trouvée, mais une séquence a plus d’éléments que l’autre et la séquence la plus courte est considérée comme inférieure à la séquence la plus longue.

- Aucune inégalité n’est trouvée et les séquences ont le même nombre d’éléments, par conséquent, les séquences sont égales et le résultat de la comparaison a la valeur false.

### <a name="example"></a>Exemple

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   int ii;
   for ( ii = 0 ; ii <= 6 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Self lexicographical_comparison of v1 under identity
   bool result1;
   result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                  v1.begin( ), v1.end( ) );
   if ( result1 )
      cout << "Vector v1 is lexicographically_less than v1." << endl;
   else
      cout << "Vector v1 is not lexicographically_less than v1." << endl;

   // lexicographical_comparison of v1 and L2 under identity
   bool result2;
   result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                  L1.begin( ), L1.end( ) );
   if ( result2 )
      cout << "Vector v1 is lexicographically_less than L1." << endl;
   else
      cout << "Vector v1 is lexicographically_less than L1." << endl;

   bool result3;
   result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                  v2.begin( ), v2.end( ), twice );
   if ( result3 )
      cout << "Vector v1 is lexicographically_less than v2 "
           << "under twice." << endl;
   else
      cout << "Vector v1 is not lexicographically_less than v2 "
           << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a>  lower_bound

Recherche la position du premier élément d’une plage triée dont la valeur est supérieure ou équivalente à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*valeur*<br/>
Valeur dont la première position ou la première position possible est recherchée dans la plage ordonnée.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant situé à la position du premier élément d’une plage triée dont la valeur est supérieure ou égale à une valeur spécifiée, où l’équivalence est spécifiée par un prédicat binaire.

### <a name="remarks"></a>Notes

Le plage source triée référencée doit être valide ; tous les itérateurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Une plage triée est une condition préalable à l’utilisation de `lower_bound` et son ordre est identique à celui spécifié par un prédicat binaire.

La plage n’est pas modifiée par l’algorithme `lower_bound`.

Les types valeur des itérateurs vers l’avant doivent être comparables en termes d’infériorité pour être ordonnés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. De cette façon, les éléments non équivalents sont ordonnés

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire sinon, avec le nombre d’étapes proportionnel à (`last - first`).

### <a name="example"></a>Exemple

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back(  i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back(  ii  );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate  mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3,  mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a>  make_heap

Convertit les éléments d’une plage spécifiée en un tas, dans lequel le premier élément est le plus grand, et pour lequel un critère de tri peut être spécifié à l’aide d’un prédicat binaire.

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à convertir en tas.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à convertir en tas.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La complexité est linéaire et nécessite 3 \* (* nom - prénom *) comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with default less than ordering
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with greater than ordering
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater-than heaped version of v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="max"></a>  max

Compare deux objets et retourne le plus grand des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate comp);
template<class Type>
constexpr Type& max (
    initializer_list<Type> );
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Premier des deux objets comparés.

*right*<br/>
Second des deux objets comparés.

*comp*<br/>
Prédicat binaire utilisé pour comparer deux objets.

*_IList*<br/>
Liste d'initialiseurs qui contient les objets à comparer.

### <a name="return-value"></a>Valeur de retour

Le plus grand des deux objets, sauf si aucun n'est plus grand que l'autre ; dans ce cas, retourne le premier des deux objets. Dans le cas d'une initializer_list, retourne le plus grand des objets dans la liste.

### <a name="remarks"></a>Notes

L'algorithme `max` est inhabituel, dans la mesure où les objets sont passés comme paramètres. La plupart des algorithmes de la bibliothèque C++ Standard opèrent sur une plage d’éléments dont la position est spécifiée par des itérateurs passés comme paramètres. Si vous avez besoin d’une fonction qui opère sur une plage d’éléments, utilisez plutôt [max_element](../standard-library/algorithm-functions.md#max_element). Visual Studio 2017 permet **constexpr** sur les surcharges qui prennent un objet initializer_list.

### <a name="example"></a>Exemple

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = -elem1;
   if ( elem2 < 0 )
      elem2 = -elem2;
   return elem1 < elem2;
};

int main()
{
   int a = 6, b = -7;
   // Return the integer with the larger absolute value
   const int& result1 = max(a, b, abs_greater);
   // Return the larger integer
   const int& result2 = max(a, b);

   cout << "Using integers 6 and -7..." << endl;
   cout << "The integer with the greater absolute value is: "
        << result1 << "." << endl;
   cout << "The integer with the greater value is: "
        << result2 << "." << endl;
   cout << endl;

// Comparing the members of an initializer_list
const int& result3 = max({ a, b });
const int& result4 = max({ a, b }, abs_greater);

cout << "Comparing the members of an initializer_list..." << endl;
cout << "The member with the greater value is: " << result3 << endl;
cout << "The integer with the greater absolute value is: " << result4 << endl;

   // Comparing set containers with elements of type CInt
   // using the max algorithm
   CInt c1 = 1, c2 = 2, c3 = 3;
   set<CInt> s1, s2, s3;
   set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s2.insert ( c2 );
   s2.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   cout << "s2 = (";
   for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
      cout << " " << *s2_Iter << ",";
   s2_Iter = --s2.end( );
   cout << " " << *s2_Iter << " )." << endl;

   s3 = max ( s1, s2 );
   cout << "s3 = max ( s1, s2 ) = (";
   for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
      cout << " " << *s3_Iter << ",";
   s3_Iter = --s3.end( );
   cout << " " << *s3_Iter << " )." << endl << endl;

   // Comparing vectors with integer elements using the max algorithm
   vector <int> v1, v2, v3, v4, v5;
   vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

   int i;
   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 0 ; ii <= 2 ; ii++ )
   {
      v2.push_back( ii );
   }

   int iii;
   for ( iii = 0 ; iii <= 2 ; iii++ )
   {
      v3.push_back( 2 * iii );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   cout << "Vector v3 is ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;

   v4 = max ( v1, v2 );
   v5 = max ( v1, v3 );

   cout << "Vector v4 = max (v1,v2) is ( " ;
   for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
      cout << *Iter4 << " ";
   cout << ")." << endl;

   cout << "Vector v5 = max (v1,v3) is ( " ;
   for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
      cout << *Iter5 << " ";
   cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer wiht the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a>  max_element

Recherche la première occurrence du plus grand élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last );

template<class ForwardIterator, class BinaryPredicate>
constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage dans laquelle rechercher l’élément le plus grand.

*last*<br/>
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage dans laquelle rechercher l’élément le plus grand.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position de la première occurrence de l’élément le plus grand de la plage dans laquelle s’effectue la recherche.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire : (`last` - `first`) - 1 comparaisons sont nécessaires pour une plage non vide.

### <a name="example"></a>Exemple

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt& operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Searching a set container with elements of type CInt
   // for the maximum element
   CInt c1 = 1, c2 = 2, c3 = -3;
   set<CInt> s1;
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s1.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

   cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
   cout << endl;

   // Searching a vector with elements of type int for the maximum
   // element under default less than & mod_lesser binary predicates
   vector <int> v1;
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      v1.push_back( - 2 * ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << " ";
   cout << ")." << endl;

   v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
   v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

   cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
   cout << "The largest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a>  merge

Regroupe tous les éléments de deux plages sources triées au sein d’une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage.

*last1*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la première des deux plages sources triées à regrouper et trier au sein d’une même plage.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément de la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage.

*last2*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage.

*Résultat*<br/>
Itérateur de sortie ciblant la position du premier élément de la plage de destination quand les deux plages sources doivent être regroupées au sein d’une même plage triée.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `merge` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme `merge`.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination.

La complexité de l’algorithme est linéaire au maximum (*last1* - *first1*)-(*last2* - *first2*) - 1 comparaisons.

La [classe list](../standard-library/list-class.md) fournit une fonction membre « merge » pour fusionner les éléments de deux listes.

### <a name="example"></a>Exemple

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
   if (elem1 < 0)
      elem1 = - elem1;
   if (elem2 < 0)
      elem2 = - elem2;
   return elem1 < elem2;
}

int main() {
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1;

   // Constructing vector v1a and v1b with default less than ordering
   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1a.push_back(  i );

   int ii;
   for ( ii =-5 ; ii <= 0 ; ii++ )
      v1b.push_back(  ii  );

   cout << "Original vector v1a with range sorted by the\n "
        << "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        << "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vector v2 with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a,  Iter2b, Iter2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vector v3 with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        << "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        << "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To merge inplace in ascending order with default binary
   // predicate less <int>( )
   merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Merged inplace with default order,\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To merge inplace in descending order, specify binary
   // predicate greater<int>( )
   merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
       v2.begin( ),  greater <int>( ) );
   cout << "Merged inplace with binary predicate greater specified,\n "
        << "vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // Applying A user-defined (UD) binary predicate mod_lesser
   merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
       v3.begin( ),  mod_lesser );
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "
        << "vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="min"></a>  min

Compare deux objets et retourne le plus petit des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate comp);
template<class Type>
constexpr Type min(
    initializer_list<Type> );
template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type>,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Premier des deux objets comparés.

*right*<br/>
Second des deux objets comparés.

*comp*<br/>
Prédicat binaire utilisé pour comparer deux objets.

*_IList*<br/>
initializer_list qui contient les membres à comparer.

### <a name="return-value"></a>Valeur de retour

Le plus petit des deux objets, sauf si aucun n’est plus petit que l’autre ; dans ce cas, retourne le premier des deux objets. Dans le cas d’un initializer_list, retourne le plus petit des objets de la liste.

### <a name="remarks"></a>Notes

L'algorithme `min` est inhabituel, dans la mesure où les objets sont passés comme paramètres. La plupart des algorithmes de la bibliothèque C++ Standard opèrent sur une plage d’éléments dont la position est spécifiée par des itérateurs passés comme paramètres. Si vous avez besoin d’une fonction qui utilise une plage d’éléments, utilisez [min_element](../standard-library/algorithm-functions.md#min_element). [constexpr](../cpp/constexpr-cpp.md) a été activée sur le `initializer_list` surcharges dans Visual Studio 2017.

### <a name="example"></a>Exemple

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
       return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
    cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

// Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
       // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector <int> v1, v2, v3, v4, v5;
    vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a>  min_element

Recherche la première occurrence du plus petit élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(ForwardIterator first, ForwardIterator last );

template<class ForwardIterator, class BinaryPredicate>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage dans laquelle rechercher l’élément le plus petit.

*last*<br/>
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage dans laquelle rechercher l’élément le plus petit.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position de la première occurrence de l’élément le plus petit de la plage dans laquelle s’effectue la recherche.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire : (`last` - `first`) - 1 comparaisons sont nécessaires pour une plage non vide.

### <a name="example"></a>Exemple

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt& operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Searching a set container with elements of type CInt
   // for the minimum element
   CInt c1 = 1, c2 = 2, c3 = -3;
   set<CInt> s1;
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s1.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

   cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
   cout << endl;

   // Searching a vector with elements of type int for the maximum
   // element under default less than & mod_lesser binary predicates
   vector <int> v1;
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      v1.push_back( - 2 * ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << " ";
   cout << ")." << endl;

   v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
   v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

   cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
   cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
binary predicate is: 0
```

## <a name="minmax_element"></a>  minmax_element

Exécute le travail effectué par `min_element` et `max_element` au sein d’un même appel.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator Last);
template<class ForwardIterator, class BinaryPredicate>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator  first,
    ForwardIterator Last,
    BinaryPredicate  comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant qui indique le début d’une plage.

*last*<br/>
Itérateur vers l’avant qui indique la fin d’une plage.

*comp*<br/>
Test facultatif utilisé pour trier les éléments.

### <a name="return-value"></a>Valeur de retour

Returns (Retours)

`pair<ForwardIterator, ForwardIterator>`

`(` [min_element](../standard-library/algorithm-functions.md#min_element)`(first, last), `[max_element](../standard-library/algorithm-functions.md#max_element)`(first, last))`.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne

`pair<ForwardIterator,ForwardIterator>`

`(min_element(_First,Last), max_element(_First,Last))`.

La deuxième fonction de modèle se comporte de la même façon, sauf qu’elle remplace `operator<(X, Y)` par `comp (X, Y)`.

Si la séquence est vide, la fonction effectue au maximum `3 * (last - first - 1) / 2` comparaisons.

## <a name="minmax"></a>  minmax

Compare deux paramètres d’entrée et les retourne sous forme de paire, du plus petit au plus grand.

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);
template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate comp);
template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> );
template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type>,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Premier des deux objets comparés.

*right*<br/>
Second des deux objets comparés.

*comp*<br/>
Prédicat binaire utilisé pour comparer deux objets.

*_IList*<br/>
initializer_list qui contient les membres à comparer.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne `pair<const Type&, const Type&>( right , left )` si *droit* est inférieure à *gauche*. Sinon, il retourne `pair<const Type&, const Type&>( left , right )`.

La deuxième fonction membre retourne une paire où le premier élément est le plus petit et le second est le plus grand comparées par le prédicat *comp*.

Les fonctions de modèle restantes ont le même comportement, à ceci près qu’elles remplacent la *gauche* et *droit* paramètres avec *_IList*.

La fonction effectue exactement une comparaison.

## <a name="mismatch"></a>  mismatch

Compare deux plages, élément par élément, et recherche la première position où il y a une différence.

Utilisez les surcharges à double portée dans le code C++14, car les surcharges qui ne prennent qu'un seul itérateur pour la deuxième plage ne détecteront pas les différences si la deuxième plage est plus longue que la première et provoqueront un comportement non défini si la deuxième plage est plus courte que la première.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2,
    BinaryPredicate Comp );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2,
    InputIterator2 Last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2,
    InputIterator2 Last2,
    BinaryPredicate Comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d'entrée qui traite la position du premier élément de la première plage à tester.

*last1*<br/>
Itérateur d'entrée qui traite la position qui suit le dernier élément de la première plage à tester.

*first2*<br/>
Itérateur d'entrée qui traite la position du premier élément de la deuxième plage à tester.

*last2*<br/>
Itérateur d'entrée qui traite la position qui suit le dernier élément de la deuxième plage à tester.

*Comp.*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui compare les éléments actuels dans chaque plage et détermine s’ils sont équivalents. Retourne **true** si la condition est satisfaite et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Paire d'itérateurs qui traite les positions de l'incohérence dans les deux plages, le premier itérateur de composant à la position dans la première plage et le deuxième itérateur de composant à la position dans la deuxième plage. S’il n’existe aucune différence entre les éléments dans les plages comparées ou si le prédicat binaire dans la deuxième version est satisfait par toutes les paires d’éléments dans les deux plages, le premier itérateur de composant pointe vers la position située juste après le dernier élément dans la première plage et le deuxième itérateur de composant pointe vers la position juste après le dernier élément testé dans la seconde plage.

### <a name="remarks"></a>Notes

La première fonction avec modèle part du principe qu'il existe autant d'éléments dans la plage commençant à first2 que dans la plage désignée par [first1, last1). S'il y a plus d'éléments dans la deuxième plage, ils sont ignorés ; s'il y en a moins, le comportement est non défini.

La plage dans laquelle s'effectue la recherche doit être valide. Tous les itérateurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible depuis la première par incrémentation.

La complexité temporelle de l'algorithme est linéaire pour le nombre d'éléments contenus dans la plage la plus courte.

Le prédicat défini par l’utilisateur ne doit pas obligatoirement imposer une relation d’équivalence qui est symétrique, réflexive et transitive entre ses opérandes.

### <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser mismatch. La surcharge C++03 est affichée uniquement pour montrer comment elle peut produire un résultat inattendu.

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}

/*
Output:
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred:  match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
*/
```

## <a name="alg_move"></a>  &lt;alg&gt; move

Déplace les éléments associés à une plage spécifiée.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début de la plage d’éléments à déplacer.

*last*<br/>
Itérateur d’entrée qui indique la fin d’une plage d’éléments à déplacer.

*dest*<br/>
Itérateur de sortie qui doit contenir les éléments déplacés.

### <a name="remarks"></a>Notes

La fonction de modèle évalue `*(dest + N) = move(*(first + N))` une fois pour chaque `N` dans la plage `[0, last - first)`, pour les valeurs strictement croissantes de `N` en commençant par la valeur la plus basse. Elle retourne ensuite `dest + N`. Si `dest` et *première* désignent des régions de stockage, *dest* ne doit pas être dans la plage `[first, last)`.

## <a name="move_backward"></a>  move_backward

Déplace les éléments d'un itérateur vers un autre. Le déplacement commence par le dernier élément d'une plage spécifiée, et se termine par le premier élément de cette plage.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
   BidirectionalIterator2 move_backward(
       BidirectionalIterator1 first,
       BidirectionalIterator1 last,
       BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur qui indique le début d’une plage à partir de laquelle déplacer des éléments.

*last*<br/>
Itérateur qui indique la fin d’une plage à partir de laquelle déplacer des éléments. Cet élément n’est pas déplacé.

*destEnd*<br/>
Itérateur bidirectionnel se rapportant à la position située immédiatement après l'élément final dans la plage de destination.

### <a name="remarks"></a>Notes

La fonction de modèle évalue `*(destEnd - N - 1) = move(*(last - N - 1))` une fois pour chaque `N` dans la plage `[0, last - first)`, pour les valeurs strictement croissantes de `N` en commençant par la valeur la plus basse. Elle retourne ensuite `destEnd - (last - first)`. Si *destEnd* et *première* désignent des régions de stockage, *destEnd* ne doit pas être dans la plage `[first, last)`.

`move` et `move_backward` reviennent fonctionnellement à utiliser `copy` et `copy_backward` avec un itérateur move.

## <a name="next_permutation"></a>  next_permutation

Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.

```cpp
template<class BidirectionalIterator>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la plage à permuter.

*last*<br/>
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à permuter.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si la permutation lexicographique suivante existe et a remplacé l’ordre d’origine de la plage ; sinon **false**, auquel cas l’ordre est transformé selon la plus petite permutation lexicographique.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Le prédicat binaire par défaut est Inférieur à et les éléments de la plage doivent être comparables en termes d’infériorité pour s’assurer que la prochaine permutation est bien définie.

La complexité est linéaire au maximum (* nom - prénom *) / 2 échanges.

### <a name="example"></a>Exemple

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      { return ( m_nVal < rhs.m_nVal );}
   friend   ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Reordering the elements of type CInt in a deque
   // using the prev_permutation algorithm
   CInt c1 = 5, c2 = 1, c3 = 10;
   bool deq1Result;
   deque<CInt> deq1, deq2, deq3;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

   if ( deq1Result )
      cout << "The lexicographically next permutation "
           << "exists and has\nreplaced the original "
           << "ordering of the sequence in deq1." << endl;
   else
      cout << "The lexicographically next permutation doesn't "
           << "exist\n and the lexicographically "
           << "smallest permutation\n has replaced the "
           << "original ordering of the sequence in deq1." << endl;

   cout << "After one application of next_permutation,\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl << endl;

   // Permuting vector elements with binary function mod_lesser
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = -3 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

   cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= 5 ) {
      next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
      cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
         cout << *Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a>  nth_element

Partitionne une plage d’éléments, en recherchant le *n*-ième élément de la séquence dans la plage, de sorte que tous les éléments qui le précèdent sont inférieurs ou égaux et que tous les éléments qui le suivent sont supérieurs ou égaux.

```cpp
template<class RandomAccessIterator>
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à partitionner.

*_Nth*<br/>
Itérateur d’accès aléatoire ciblant la position de l’élément à ordonner correctement sur la limite de la partition.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à partitionner.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L’algorithme `nth_element` ne garantit pas que les éléments des sous-plages de part et d’autre du *n*-ième élément sont triés. Il apporte donc encore moins de garanties que `partial_sort`, qui ordonne les éléments de la plage en dessous d’un élément choisi, et peut être utilisé comme alternative plus rapide à `partial_sort` quand l’ordre de la plage inférieure n’est pas nécessaire.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre.

La moyenne d’une complexité de tri est linéaire par rapport à * nom - prénom *.

### <a name="example"></a>Exemple

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
   return elem1 > elem2;
}

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 3 * i );

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
      v1.push_back( 3 * ii + 1 );

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
      v1.push_back( 3 * iii +2 );

   cout << "Original vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
   cout << "Position 3 partitioned vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order, specify binary predicate
   nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
          greater<int>( ) );
   cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   random_shuffle( v1.begin( ), v1.end( ) );
   cout << "Shuffled vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
   cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

## <a name="none_of"></a>  none_of

Retourne **true** lorsqu’une condition n’est jamais présente entre les éléments dans la plage donnée.

```cpp
template<class InputIterator, class BinaryPredicate>
bool none_of(InputIterator first, InputIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début de la recherche d’une condition dans une plage d’éléments.

*last*<br/>
Itérateur d’entrée qui indique la fin d’une plage d’éléments.

*comp*<br/>
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si la condition n’est pas détectée au moins une fois dans la plage spécifiée, et **false** si la condition est détectée.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si, pour certains `N` dans la plage `[0, last - first)`, le prédicat `comp(*(first + N))` est toujours **false**.

## <a name="partial_sort"></a>  partial_sort

Réorganise un nombre spécifié d’éléments plus petits au sein d’une plage, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*sortEnd*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la sous-plage à trier.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier partiellement.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre. Le `sort` algorithme n’est pas stable et ne garantit pas que l’ordre relatif des éléments équivalents est conservé. L’algorithme `stable_sort` conserve cet ordre d’origine.

La complexité moyenne du tri partiel est *O*((`last`- `first`) journal (`sortEnd`- `first`)).

### <a name="example"></a>Exemple

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
   {
      v1.push_back( 2 * ii +1 );
   }

   cout << "Original vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
   cout << "Partially sorted vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To partially sort in descending order, specify binary predicate
   partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
   cout << "Partially resorted (greater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ),
UDgreater );
   cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector:
v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a>  partial_sort_copy

Copie les éléments d’une plage source dans une plage de destination. Les éléments sources sont triés par ordre croissant ou selon un autre prédicat binaire spécifié.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class BinaryPredicate>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la plage source.

*last1*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la plage source.

*first2*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage de destination triée.

*last2*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage de destination triée.

*comp*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur d’accès aléatoire ciblant l’élément de la plage de destination situé une position après le dernier élément inséré à partir de la plage source.

### <a name="remarks"></a>Notes

Les plages source et de destination ne doivent pas se chevaucher et doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Le prédicat binaire doit fournir un ordre faible strict pour que les éléments qui ne sont pas équivalents soient ordonnés, mais que ceux qui sont équivalents ne le soient pas. Deux éléments sont équivalents sous le prédicat Inférieur à, mais pas nécessairement égaux si aucun n’est inférieur à l’autre.

### <a name="example"></a>Exemple

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a>  partition

Répartit les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas.

```cpp
template<class BidirectionalIterator, class Predicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la plage à partitionner.

*last*<br/>
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à partitionner.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire si un élément doit être classé. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel ciblant la position du premier élément de la plage qui ne satisfait pas la condition du prédicat.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments *a* et *b* sont équivalents, mais pas nécessairement égaux si *Pr* (*a*, *b*) est false et *Pr* (*b*, *a*) est false, où *Pr* est le prédicat du paramètre spécifié. Le `partition` algorithme n’est pas stable et ne garantit pas que l’ordre relatif des éléments équivalents est conservé. L’algorithme `stable_ partition` conserve cet ordre d’origine.

La complexité est linéaire : il existe (`last` - `first`) applications de *comp* et au maximum (`last` - `first`) / 2 échanges.

### <a name="example"></a>Exemple

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value ) {
   return value > 5;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 10 ; i++ )
   {
      v1.push_back( i );
   }
   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Partition the range with predicate greater10
   partition ( v1.begin( ), v1.end( ), greater5 );
   cout << "The partitioned set of elements in v1 is: ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="partition_copy"></a>  partition_copy

Copie les éléments pour lesquels une condition est **true** vers une destination, et pour lesquelles la condition est **false** vers un autre. Les éléments doivent provenir d'une plage spécifiée.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class Predicate>
pair<OutputIterator1, OutputIterator2>
    partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée qui indique le début d’une plage dans laquelle rechercher une condition.

*last*<br/>
Itérateur d’entrée qui indique la fin d’une plage.

*dest1*<br/>
Un itérateur de sortie utilisé pour copier des éléments qui retournent la valeur true pour une condition testée à l’aide de *_Pred*.

*dest2*<br/>
Un itérateur de sortie utilisé pour copier des éléments qui retournent la valeur false pour une condition testée à l’aide de *_Pred*.

*_Pred*<br/>
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à vérifier. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="remarks"></a>Notes

La fonction de modèle copie chaque élément `X` dans `[first,last)` à `*dest1++` si `_Pred(X)` a la valeur true, ou à `*dest2++` si ce n’est pas le cas. Il retourne `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.

## <a name="partition_point"></a>  partition_point

Retourne le premier élément d'une plage donnée qui ne répond pas à une condition. Les éléments sont triés de sorte que ceux qui répondent à la condition précèdent ceux qui n'y répondent pas.

```cpp
template<class ForwardIterator, class Predicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
`ForwardIterator` qui indique le début d’une plage dans laquelle rechercher une condition.

*last*<br/>
`ForwardIterator` qui indique la fin d’une plage.

*comp*<br/>
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire par l’élément recherché. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne un `ForwardIterator` qui fait référence au premier élément qui ne remplit pas la condition vérifiée par *comp*, ou retourne *dernière* si celle-ci est introuvable.

### <a name="remarks"></a>Notes

La fonction de modèle recherche le premier itérateur `it` dans `[first, last)` pour lequel `comp(*it)` est **false**. La séquence doit être triée par *comp*.

## <a name="pop_heap"></a>  pop_heap

Retire le plus grand élément du début du tas et le place à l'avant-dernière position de la plage, puis forme un nouveau tas à partir des éléments restants.

```cpp
template<class RandomAccessIterator>
void pop_heap( RandomAccessIterator first, RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément du tas.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément du tas.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

L’algorithme `pop_heap` est l’inverse de l’opération effectuée par l’algorithme push_heap, dans lequel un élément à l’avant-dernière position d’une plage est ajouté à un tas constitué des éléments précédents de la plage, au cas où l’élément ajouté au tas est supérieur à tous les éléments déjà présents dans le tas.

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La plage qui exclut l’élément qui vient d’être ajouté à la fin doit être un tas.

La complexité est logarithmique et nécessite au maximum log (* nom - prénom *) comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()  {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 1 ; i <= 9 ; i++ )
      v1.push_back( i );

   // Make v1 a heap with default less than ordering
   random_shuffle( v1.begin( ), v1.end( ) );
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Add an element to the back of the heap
   v1.push_back( 10 );
   push_heap( v1.begin( ), v1.end( ) );
   cout << "The reheaped v1 with 10 added is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove the largest element from the heap
   pop_heap( v1.begin( ), v1.end( ) );
   cout << "The heap v1 with 10 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << endl;

   // Make v1 a heap with greater-than ordering with a 0 element
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   v1.push_back( 0 );
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Application of pop_heap to remove the smallest element
   pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="prev_permutation"></a>  prev_permutation

Réorganise les éléments d’une plage, de sorte que l’ordre d’origine est remplacé par la permutation précédente la plus élevée d’un point de vue lexicographique (s’il en existe une). Le sens de « précédente » peut être défini à l’aide d’un prédicat binaire.

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la plage à permuter.

*last*<br/>
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à permuter.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si la permutation lexicographique précédente existe et a remplacé l’ordre d’origine de la plage ; sinon **false**, auquel cas l’ordre est transformé dans le point de vue lexicographique plus grand permutation.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Le prédicat binaire par défaut est Inférieur à et les éléments de la plage doivent être comparables en termes d’infériorité pour s’assurer que la permutation précédente est bien définie.

La complexité est linéaire avec au maximum (`last` -  `first`) / 2 échanges.

### <a name="example"></a>Exemple

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main() {
   // Reordering the elements of type CInt in a deque
   // using the prev_permutation algorithm
   CInt c1 = 1, c2 = 5, c3 = 10;
   bool deq1Result;
   deque<CInt> deq1, deq2, deq3;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

   if ( deq1Result )
      cout << "The lexicographically previous permutation "
           << "exists and has \nreplaced the original "
           << "ordering of the sequence in deq1." << endl;
   else
      cout << "The lexicographically previous permutation doesn't "
           << "exist\n and the lexicographically "
           << "smallest permutation\n has replaced the "
           << "original ordering of the sequence in deq1." << endl;

   cout << "After one application of prev_permutation,\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl << endl;

   // Permutating vector elements with binary function mod_lesser
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = -3 ; i <= 3 ; i++ )
      v1.push_back( i );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

   cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= 5 ) {
      prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
      cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
         cout << *Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
and the lexicographically smallest permutation
has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a>  push_heap

Ajoute un élément qui se trouve à la fin d'une plage à un tas existant, constitué des éléments précédents de la plage.

```cpp
template<class RandomAccessIterator>
void push_heap( RandomAccessIterator first, RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap( RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément du tas.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à convertir en tas.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

L’élément doit d’abord être déplacé à la fin d’un tas existant, puis l’algorithme est utilisé pour ajouter cet élément au tas existant.

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La plage qui exclut l’élément qui vient d’être ajouté à la fin doit être un tas.

La complexité est logarithmique et nécessite au maximum log ( *nom - prénom*) comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 1 ; i <= 9 ; i++ )
      v1.push_back( i );

   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with default less than ordering
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Add an element to the heap
   v1.push_back( 10 );
   cout << "The heap v1 with 10 pushed back is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   push_heap( v1.begin( ), v1.end( ) );
   cout << "The reheaped v1 with 10 added is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << endl;

   // Make v1 a heap with greater than ordering
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater-than heaped version of v1 is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   v1.push_back(0);
   cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater than reheaped v1 with 11 added is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="random_shuffle"></a>  random_shuffle

La fonction std ::random_shuffle() est déconseillée et remplacée par [std::shuffle](../standard-library/algorithm-functions.md#shuffle). Pour un exemple de code et plus d’informations, consultez [ \<aléatoire >](../standard-library/random.md) et la publication sur [pourquoi sont méthodes std::random_shuffle déconseillées dans C ++ 14 ?](http://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a>  remove

Élimine une valeur spécifiée d'une plage donnée sans modifier l'ordre des éléments restants, et retourne la fin d'une nouvelle plage exempte de la valeur spécifiée.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur de transfert se rapportant à la position du premier élément dans la plage de laquelle les éléments sont supprimés.

*last*<br/>
Itérateur de transfert se rapportant à la position située immédiatement après l'élément final dans la plage de laquelle les éléments sont supprimés.

*Val*<br/>
Valeur qui doit être supprimée de la plage.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert se rapportant à la nouvelle position de fin de la plage modifiée, située immédiatement après l'élément final de la séquence restante exempte de la valeur spécifiée.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire ; Il existe (`last` - `first`) comparaisons d’égalité.

Le [list, classe](../standard-library/list-class.md) a une version de fonction membre plus efficace de `remove`, qui rétablit également les liens des pointeurs.

### <a name="example"></a>Exemple

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value of 7
   new_end = remove ( v1.begin( ), v1.end( ), 7 );

   cout << "Vector v1 with value 7 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To change the sequence size, use erase
   v1.erase (new_end, v1.end( ) );

   cout << "Vector v1 resized with value 7 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_copy"></a>  remove_copy

Copie les éléments d'une plage source vers une plage de destination. Les éléments ayant une valeur spécifiée ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(InputIterator first, InputIterator last, OutputIterator result, const Type& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la plage de laquelle les éléments sont supprimés.

*last*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la plage de laquelle les éléments sont supprimés.

*Résultat*<br/>
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans laquelle les éléments sont supprimés.

*Val*<br/>
Valeur qui doit être supprimée de la plage.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert ciblant la nouvelle position de fin de la plage de destination, de suite après le dernier élément de la copie de la séquence restante exempte de la valeur spécifiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La plage de destination doit avoir suffisamment d’espace pour accueillir les éléments restants qui seront copiés après la suppression de la valeur spécifiée.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire ; Il existe (`last` - `first`) comparaisons d’égalité et au maximum (`last` - `first`) affectations.

### <a name="example"></a>Exemple

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2(10);
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle (v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:     ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value of 7
   new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

   cout << "Vector v1 is left unchanged as ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a>  remove_copy_if

Copie les éléments d'une plage source vers une plage de destination. Les éléments répondant à un prédicat ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.

```cpp
template<class InputIterator, class OutputIterator, class Predicate>
OutputIterator remove_copy_if(InputIterator first, InputIterator Last, OutputIterator result, Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la plage de laquelle les éléments sont supprimés.

*last*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la plage de laquelle les éléments sont supprimés.

*Résultat*<br/>
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans laquelle les éléments sont supprimés.

*_Pred*<br/>
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert ciblant la nouvelle position de fin de la plage de destination, de suite après le dernier élément de la séquence restante exempte des éléments satisfaisant le prédicat.

### <a name="remarks"></a>Notes

La plage source référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La plage de destination doit avoir suffisamment d’espace pour accueillir les éléments restants qui seront copiés après la suppression de la valeur spécifiée.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire : il existe (`last` - `first`) comparaisons d’égalité et au maximum (`last` - `first`) affectations.

Pour plus d’informations sur le comportement de ces fonctions, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1, v2(10);
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:      ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value greater than 6
   new_end = remove_copy_if ( v1.begin( ), v1.end( ),
      v2.begin( ), greater6 );

   cout << "After the appliation of remove_copy_if to v1,\n "
        << "vector v1 is left unchanged as ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is a copy of v1 with values greater "
        << "than 6 removed:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_if"></a>  remove_if

Élimine d’une plage donnée les éléments qui répondent à un prédicat, sans modifier l’ordre des éléments restants et en retournant la fin d’une nouvelle plage exempte de la valeur spécifiée.

```cpp
template<class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant pointant sur la position du premier élément de la plage dont les éléments sont supprimés.

*last*<br/>
Itérateur vers l’avant pointant sur la position juste après le dernier élément de la plage dont les éléments sont supprimés.

*_Pred*<br/>
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert se rapportant à la nouvelle position de fin de la plage modifiée, située immédiatement après l'élément final de la séquence restante exempte de la valeur spécifiée.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire : il existe (`last` - `first`) comparaisons d’égalité.

La classe list a une version de fonction membre remove plus efficace qui rétablit les liens des pointeurs.

### <a name="example"></a>Exemple

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements satisfying predicate greater6
   new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

   cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To change the sequence size, use erase
   v1.erase (new_end, v1.end( ) );

   cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace"></a>  replace

Examine tous les éléments d'une plage et les remplace s'ils correspondent à une valeur spécifiée.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant pointant sur la position du premier élément de la plage dont les éléments sont remplacés.

*last*<br/>
Itérateur vers l’avant pointant sur la position juste après le dernier élément de la plage dont les éléments sont remplacés.

*_OldVal*<br/>
Ancienne valeur des éléments remplacés.

*_NewVal*<br/>
Nouvelle valeur assignée aux éléments ayant l’ancienne valeur.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L’ordre des éléments non remplacés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire ; Il existe (`last` - `first`) comparaisons d’égalité et au maximum (`last` - `first`) affectations de nouvelles valeurs.

### <a name="example"></a>Exemple

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle (v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements with a value of 7 with a value of 700
   replace (v1.begin( ), v1.end( ), 7 , 700);

   cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_copy"></a>  replace_copy

Examine tous les éléments d'une plage source et les remplace s'ils correspondent à une valeur spécifiée, tout en copiant le résultat dans une nouvelle plage de destination.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée pointant vers la position du premier élément de la plage dont les éléments sont remplacés.

*last*<br/>
Itérateur d’entrée pointant vers la position située de suite après le dernier élément de la plage dont les éléments sont remplacés.

*Résultat*<br/>
Itérateur de sortie pointant vers le premier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

*_OldVal*<br/>
Ancienne valeur des éléments remplacés.

*_NewVal*<br/>
Nouvelle valeur assignée aux éléments ayant l’ancienne valeur.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie pointant vers la position située de suite après le dernier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées ne doivent pas se chevaucher et doivent toutes deux être valides : tous les pointeurs doivent pouvoir être déréférencés et, dans les séquences, la dernière position est accessible à partir de la première par incrémentation.

L’ordre des éléments non remplacés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire : il existe (`last` - `first`) comparaisons d’égalité et au maximum (`last` - `first`) affectations de nouvelles valeurs.

### <a name="example"></a>Exemple

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   list <int> L1 (15);
   vector <int>::iterator Iter1;
   list <int>::iterator L_Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );

   int iii;
   for ( iii = 0 ; iii <= 15 ; iii++ )
      v1.push_back( 1 );

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in one part of a vector with a value of 7
   // with a value of 70 and copy into another part of the vector
   replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

   cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in a vector with a value of 70
   // with a value of 1 and copy into a list
   replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

   cout << "The list copy L1 of v1 with the value 0 replacing "
        << "that of 7 is:\n ( " ;
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
      cout << *L_Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a>  replace_copy_if

Examine tous les éléments d'une plage source et les remplace s'ils répondent à un prédicat, tout en copiant le résultat dans une nouvelle plage de destination.

```cpp
template<class InputIterator, class OutputIterator, class Predicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Predicate pred,
    const Type& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’entrée pointant vers la position du premier élément de la plage dont les éléments sont remplacés.

*last*<br/>
Itérateur d’entrée pointant vers la position située de suite après le dernier élément de la plage dont les éléments sont remplacés.

*Résultat*<br/>
Itérateur de sortie pointant vers la position du premier élément de la plage de destination dans laquelle les éléments sont copiés.

*_Pred*<br/>
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

*Val*<br/>
Nouvelle valeur assignée aux éléments dont l’ancienne valeur satisfait au prédicat.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie pointant vers la position située de suite après le dernier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées ne doivent pas se chevaucher et doivent toutes deux être valides : tous les pointeurs doivent pouvoir être déréférencés et, dans les séquences, la dernière position est accessible à partir de la première par incrémentation.

L’ordre des éléments non remplacés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire ; Il existe (`last` - `first`) comparaisons d’égalité et au maximum (`last` - `first`) affectations de nouvelles valeurs.

### <a name="example"></a>Exemple

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1;
   list <int> L1 (13);
   vector <int>::iterator Iter1;
   list <int>::iterator L_Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );

   int iii;
   for ( iii = 0 ; iii <= 13 ; iii++ )
      v1.push_back( 1 );

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements with a value of 7 in the 1st half of a vector
   // with a value of 70 and copy it into the 2nd half of the vector
   replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
      greater6 , 70);

   cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in a vector with a value of 70
   // with a value of 1 and copy into a list
   replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
      greater6 , -1 );

   cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
      cout << *L_Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_if"></a>  replace_if

Examine tous les éléments d’une plage et les remplace s’ils répondent à un prédicat spécifié.

```cpp
template<class ForwardIterator, class Predicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred,
    const Type& val);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant pointant sur la position du premier élément de la plage dont les éléments sont remplacés.

*last*<br/>
Itérateur pointant sur la position juste après le dernier élément de la plage dont les éléments sont remplacés.

*_Pred*<br/>
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

*Val*<br/>
Nouvelle valeur assignée aux éléments dont l’ancienne valeur satisfait au prédicat.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L’ordre des éléments non remplacés reste stable.

L’algorithme `replace_if` est une généralisation de l’algorithme `replace`, ce qui permet de n’importe quel prédicat spécifié, au lieu de l’égalité à une valeur de constante spécifiée.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire : il existe (`last` - `first`) comparaisons d’égalité et au maximum (`last` - `first`) affectations de nouvelles valeurs.

### <a name="example"></a>Exemple

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements satisfying the predicate greater6
   // with a value of 70
   replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

   cout << "The vector v1 with a value 70 replacing those\n "
        << "elements satisfying the greater6 predicate is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reverse"></a>  reverse

Inverse l'ordre des éléments d'une plage.

```cpp
template<class BidirectionalIterator>
void reverse(BidirectionalIterator first, BidirectionalIterator last);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel pointant sur la position du premier élément de la plage dont les éléments sont permutés.

*last*<br/>
Itérateur bidirectionnel pointant sur la position juste après le dernier élément de la plage dont les éléments sont permutés.

### <a name="remarks"></a>Notes

La plage source référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

### <a name="example"></a>Exemple

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Reverse the elements in the vector
   reverse (v1.begin( ), v1.end( ) );

   cout << "The modified vector v1 with values reversed is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a>  reverse_copy

Inverse l'ordre des éléments d'une plage source, tout en les copiant dans une plage de destination.

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator Last,
    OutputIterator result);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel pointant vers la position du premier élément de la plage source dont les éléments sont permutés.

*last*<br/>
Itérateur bidirectionnel pointant vers la position située de suite après le dernier élément de la plage source dont les éléments sont permutés.

*Résultat*<br/>
Itérateur de sortie pointant vers la position du premier élément de la plage de destination dans laquelle les éléments sont copiés.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie pointant vers la position située de suite après le dernier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

### <a name="example"></a>Exemple

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2( 10 );
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Reverse the elements in the vector
   reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

   cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   cout << "The original vector v1 remains unmodified as:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="rotate"></a>  rotate

Échange les éléments de deux plages adjacentes.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage à faire pivoter.

*Milieu*<br/>
Itérateur vers l’avant définissant la limite au sein de la plage qui cible la position du premier élément dans la deuxième partie de la plage dont les éléments doivent être échangés avec ceux de la première partie de la plage.

*Dernière*<br/>
Itérateur vers l’avant ciblant la position située de suite après le dernier élément de la plage à faire pivoter.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire au maximum (`last` - `first`) échange.

### <a name="example"></a>Exemple

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   deque <int> d1;
   vector <int>::iterator v1Iter1;
   deque<int>::iterator d1Iter1;

   int i;
   for ( i = -3 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =0 ; ii <= 5 ; ii++ )
   {
      d1.push_back( ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
   cout << "After rotating, vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   cout << "The original deque d1 is ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1  << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= d1.end( ) - d1.begin( ) ) {
      rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
      cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
      for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
         cout << *d1Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a>  rotate_copy

Échange les éléments de deux plages adjacentes au sein d'une plage source et copie le résultat dans une plage de destination.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage à faire pivoter.

*Milieu*<br/>
Itérateur vers l’avant définissant la limite au sein de la plage qui cible la position du premier élément dans la deuxième partie de la plage dont les éléments doivent être échangés avec ceux de la première partie de la plage.

_ *Dernière* un itérateur vers l’avant ciblant la position juste après le dernier élément dans la plage à permuter.

*Résultat*<br/>
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire au maximum (`last` - `first`) échange.

### <a name="example"></a>Exemple

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1 , v2 ( 9 );
   deque <int> d1 , d2 ( 6 );
   vector <int>::iterator v1Iter , v2Iter;
   deque<int>::iterator d1Iter , d2Iter;

   int i;
   for ( i = -3 ; i <= 5 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii =0 ; ii <= 5 ; ii++ )
      d1.push_back( ii );

   cout << "Vector v1 is ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
      cout << *v1Iter  << " ";
   cout << ")." << endl;

   rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
   cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
      cout << *v1Iter  << " ";
   cout << ")." << endl;

   cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
      cout << *v2Iter  << " ";
   cout << ")." << endl;

   cout << "The original deque d1 is ( " ;
   for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
      cout << *d1Iter  << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= d1.end( ) - d1.begin( ) )
   {
      rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
      cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
      for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
         cout << *d2Iter  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

## <a name="search"></a>  search

Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*first2*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la correspondance.

*last2*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la correspondance.

*comp*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la position du premier élément de la première sous-séquence qui correspond à la séquence spécifiée ou qui est équivalente au sens spécifié par un prédicat binaire.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité moyenne est linéaire par rapport à la taille de la plage de recherche et le pire cas de complexité est également linéaire par rapport à la taille de la séquence recherchée.

### <a name="example"></a>Exemple

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 4 ; ii <= 5 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for first match to L1 under identity
   vector <int>::iterator result1;
   result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is at least one match of L1 in v1"
           << "\n and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = search  (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent\n to those in v2 under the binary "
           << "predicate twice\n and the first one begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="search_n"></a>  search_n

Recherche la première sous-séquence d’une plage dont un nombre spécifié d’éléments ont une valeur particulière ou une relation à cette valeur, selon un prédicat binaire spécifié.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& val);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& val,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*<br/>
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*count*<br/>
Taille de la sous-séquence recherchée.

*Val*<br/>
Valeur des éléments de la séquence recherchée.

*comp*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la position du premier élément de la première sous-séquence qui correspond à la séquence spécifiée ou qui est équivalente au sens spécifié par un prédicat binaire.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire par rapport à la taille de la plage de recherche.

### <a name="example"></a>Exemple

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
   return elem1 == 2 * elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( 5  );
   }

   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( 10  );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Searching v1 for first match to (5 5 5) under identity
   vector <int>::iterator result1;
   result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

   if ( result1 == v1.end( ) )
      cout << "There is no match for a sequence ( 5 5 5 ) in v1."
           << endl;
   else
      cout << "There is at least one match of a sequence ( 5 5 5 )"
           << "\n in v1 and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for first match to (5 5 5) under one_half
   vector <int>::iterator result2;
   result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

   if ( result2 == v1.end( ) )
      cout << "There is no match for a sequence ( 5 5 5 ) in v1"
           << " under the equivalence predicate one_half." << endl;
   else
      cout << "There is a match of a sequence ( 5 5 5 ) "
           << "under the equivalence\n predicate one_half "
           << "in v1 and the first one begins at "
           << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a>  set_difference

Regroupe tous les éléments qui appartiennent à une plage source triée, mais pas à une autre plage source triée, en une même plage de destination triée. Un critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1  first1,
    InputIterator1  last1,
    InputIterator2  first2,
    InputIterator2  last2,
    OutputIterator  result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_difference(
    InputIterator1  first1,
    InputIterator1  last1,
    InputIterator2  first2,
    InputIterator2  last2,
    OutputIterator  result,
    BinaryPredicate  comp );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*last1*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*last2*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*Résultat*<br/>
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans la mesure où les deux plages sources doivent être regroupées au sein d’une même plage triée représentant la différence des deux plages sources.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant la différence des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la première plage source.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `set_difference` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme merge.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double (de telle sorte qu’il y a plus d’éléments dans la première plage source que dans la seconde), la plage de destination contient le nombre d’occurrences supplémentaires de ces éléments que contient la première plage source par rapport à la deuxième.

La complexité de l’algorithme est linéaire avec au maximum 2 \* (( *last1 - first1*)-( *last2 - first2*)) - 1 comparaisons pour des plages sources non vides.

### <a name="example"></a>Exemple

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if (elem1 < 0)
      elem1 = - elem1;
   if (elem2 < 0)
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -1 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 0 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a difference in asscending
   // order with the default binary predicate less <int>( )
   Result1 = set_difference ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Set_difference of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a difference in descending
   // order specify binary predicate greater<int>( )
   Result2 = set_difference ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Set_difference of source ranges with binary"
        << "predicate greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a difference applying a user
   // defined binary predicate mod_lesser
   Result3 = set_difference (  v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Set_difference of source ranges with binary "
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_intersection"></a>  set_intersection

Regroupe tous les éléments de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*last1*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*last2*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

**_** *Résultat* un itérateur de sortie ciblant la position du premier élément dans la plage de destination où les deux plages de source doivent être regroupées au sein d’une même plage triée représentant l’intersection de la source de deux plages d’adresses.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant l’intersection des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme merge selon le même ordre que celui utilisé par l’algorithme chargé de trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double, la plage de destination contient le nombre maximal de ces éléments qui figurent dans les deux plages sources.

La complexité de l’algorithme est linéaire avec au maximum 2 \* (( *last1 - first1*) + ( *last2 - first2*)) - 1 comparaisons pour des plages sources non vides.

### <a name="example"></a>Exemple

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main() {
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less than ordering
   int i;
   for ( i = -1 ; i <= 3 ; i++ )
      v1a.push_back( i );

   int ii;
   for ( ii =-3 ; ii <= 1 ; ii++ )
      v1b.push_back( ii );

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        << "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        << "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
           <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into an intersection in asscending order with the
   // default binary predicate less <int>( )
   Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Intersection of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into an intersection in descending order, specify
   // binary predicate greater<int>( )
   Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Intersection of source ranges with binary predicate"
        << " greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into an intersection applying a user-defined
   // binary predicate mod_lesser
   Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Intersection of source ranges with binary predicate "
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>  set_symmetric_difference

Regroupe tous les éléments qui appartiennent à l'une de deux plages sources triées (mais pas aux deux) au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*last1*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*last2*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

**_** *Résultat* un itérateur de sortie ciblant la position du premier élément dans la plage de destination où les deux plages de source doivent être regroupées au sein d’une même plage triée représentant la différence symétrique des deux plages sources.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant la différence symétrique des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `merge*` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme merge.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double, la plage de destination contient la valeur absolue du nombre d’occurrences supplémentaires de ces éléments que contient l’une des plages sources par rapport à la deuxième.

La complexité de l’algorithme est linéaire avec au maximum 2 \* ((*last1 - first1*)-(*last2 - first2*)) - 1 comparaisons pour des plages sources non vides.

### <a name="example"></a>Exemple

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -1 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 0 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference in ascending
   // order with the default binary predicate less <int>( )
   Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Set_symmetric_difference of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference in descending
   // order, specify binary predicate greater<int>( )
   Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Set_symmetric_difference of source ranges with binary"
        << "predicate greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference applying a user
   // defined binary predicate mod_lesser
   Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Set_symmetric_difference of source ranges with binary "
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_union"></a>  set_union

Regroupe tous les éléments qui appartiennent au moins à l'une de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*last1*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*first2*<br/>
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*last2*<br/>
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

**_** *Résultat* un itérateur de sortie ciblant la position du premier élément dans la plage de destination où les deux plages de source doivent être regroupées au sein d’une même plage triée représentant l’union de deux plages sources.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est supérieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant l’union des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `merge` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme `merge`.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double, la plage de destination contient le nombre maximal de ces éléments qui figurent dans les deux plages sources.

La complexité de l’algorithme est linéaire avec au maximum 2 \* (( *last1 - first1*)-( *last2 - first2*)) - 1 comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a, Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less than ordering
   int i;
   for ( i = -1 ; i <= 3 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 1 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
   vector <int>::iterator Iter2a,  Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a union in ascending order with the default
    // binary predicate less <int>( )
   Result1 = set_union ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Union of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a union in descending order, specify binary
   // predicate greater<int>( )
   Result2 = set_union (  v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Union of source ranges with binary predicate greater "
        << "specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a union applying a user-defined
   // binary predicate mod_lesser
   Result3 = set_union ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Union of source ranges with binary predicate "
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="shuffle"></a>  lecture aléatoire

Lit de façon aléatoire (réorganise) les éléments pour une plage donnée à l'aide d'un générateur de nombres aléatoires.

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur sur le premier élément de la plage à lire de façon aléatoire, compris. Doit remplir les conditions de `RandomAccessIterator` et `ValueSwappable`.

*last*<br/>
Itérateur sur le dernier élément de la plage à lire de façon aléatoire, non compris. Doit remplir les conditions de `RandomAccessIterator` et `ValueSwappable`.

*Gen*<br/>
Générateur de nombres aléatoires que la fonction `shuffle()` utilisera pour l'opération. Doit remplir les conditions d'un `UniformRandomNumberGenerator`.

### <a name="remarks"></a>Notes

Pour plus d’informations et pour obtenir un exemple de code qui utilise `shuffle()`, consultez [\<random>](../standard-library/random.md).

## <a name="sort"></a>  sort

Réorganise les éléments d’une plage spécifiée, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.

```cpp
template<class RandomAccessIterator>
   void sort(
      RandomAccessIterator first,
      RandomAccessIterator last);

template<class RandomAccessIterator, class Predicate>
   void sort(
      RandomAccessIterator first,
      RandomAccessIterator last,
      Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Ce prédicat binaire accepte deux arguments et retourne **true** si les deux arguments sont dans l’ordre et **false** dans le cas contraire. Cette fonction de comparaison doit imposer un ordre faible strict sur les paires d’éléments de la séquence. Pour plus d’informations, consultez [Algorithmes](../standard-library/algorithms.md).

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre. L’algorithme `sort` n’est pas stable et ne garantit pas que l’ordre relatif des éléments équivalents est conservé. L’algorithme `stable_sort` conserve cet ordre d’origine.

La moyenne d’une complexité de tri est *O*( *N* journal *N*), où *N* =  *dernier - premier*.

### <a name="example"></a>Exemple

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
   {
      v1.push_back( 2 * ii + 1 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order. specify binary predicate
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted (greater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   sort( v1.begin( ), v1.end( ), UDgreater );
   cout << "Resorted (UDgreater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a>  sort_heap

Convertit un tas en une plage triée.

```cpp
template<class RandomAccessIterator>
   void sort_heap(
      RandomAccessIterator first,
      RandomAccessIterator last);

template<class RandomAccessIterator, class Predicate>
   void sort_heap(
      RandomAccessIterator first,
      RandomAccessIterator last,
      Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément du tas cible.

*last*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément du tas cible.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Après l’application de cet algorithme, la plage à laquelle il a été appliqué n’est plus un tas.

Il ne s’agit pas d’un tri stable, car l’ordre relatif des éléments équivalents n’est pas nécessairement conservé.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La complexité est au maximum *N* journal *N*, où *N* = ( *nom - prénom*).

### <a name="example"></a>Exemple

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v) {
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i) {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main() {
    vector<int> v;
    for (int i = 1; i <= 9; ++i) {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a>  stable_partition

Classe les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas, et l’ordre relatif des éléments équivalents doit être conservé.

```cpp
template<class BidirectionalIterator, class Predicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Predicate pred );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la plage à partitionner.

*last*<br/>
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à partitionner.

*_Pred*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire si un élément doit être classé. Un prédicat accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel ciblant la position du premier élément de la plage qui ne satisfait pas la condition du prédicat.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments *a* et *b* sont équivalents, mais pas nécessairement égaux si *Pr* (*a*, *b*) est false et *Pr* (*b*, *a*) est false, où *Pr* est le prédicat du paramètre spécifié. Le `stable_ partition` algorithme est stable et garantit que l’ordre relatif des éléments équivalents est conservé. L’algorithme `partition` ne conserve pas nécessairement cet ordre d’origine.

### <a name="example"></a>Exemple

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value ) {
   return value > 5;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, result;

   int i;
   for ( i = 0 ; i <= 10 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 4 ; ii++ )
      v1.push_back( 5 );

   random_shuffle(v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Partition the range with predicate greater10
   result = stable_partition (v1.begin( ), v1.end( ), greater5 );
   cout << "The partitioned set of elements in v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "The first element in v1 to fail to satisfy the"
        << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a>  stable_sort

Classe les éléments d’une plage spécifiée dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire, et conserve l’ordre relatif des éléments équivalents.

```cpp
template<class BidirectionalIterator>
void stable_sort( BidirectionalIterator first, BidirectionalIterator last );

template<class BidirectionalIterator, class BinaryPredicate>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur bidirectionnel ciblant la position du premier élément de la plage à trier.

*last*<br/>
Itérateur bidirectionnel ciblant la position située juste après le dernier élément de la plage à trier.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre. Le `sort` algorithme est stable et garantit que l’ordre relatif des éléments équivalents est conservé.

La complexité de l’exécution de `stable_sort` varie selon la quantité de mémoire disponible, mais le meilleur des cas (accordé suffisamment de mémoire) sont *O*( *N* journal *N*) et le pire des cas est *O*( *N* (journal *N* ) 2), où *N* =  *last - First.* En règle générale, le `sort` algorithme est considérablement plus rapide que `stable_sort`.

### <a name="example"></a>Exemple

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i  );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   stable_sort(v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order, specify binary predicate
   stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted (greater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   stable_sort(v1.begin( ), v1.end( ), UDgreater );
   cout << "Resorted (UDgreater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a>  swap

Le premier remplacement échange les valeurs de deux objets. Le deuxième remplacement échange les valeurs de deux tableaux d’objets.

```cpp
template<class Type>
   void swap(
      Type& left,
      Type& right);
template<class Type, size_t N>
   void swap(
      Type (& left)[N],
      Type (& right)[N]);\r
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Pour le premier remplacement, premier objet dont le contenu est échangé. Pour le deuxième remplacement, premier tableau d’objets dont le contenu est échangé.

*right*<br/>
Pour le premier remplacement, deuxième objet dont le contenu est échangé. Pour le deuxième remplacement, deuxième tableau d’objets dont le contenu est échangé.

### <a name="remarks"></a>Notes

La première surcharge est conçue pour traiter des objets individuels. La deuxième surcharge échange le contenu des objets entre deux tableaux.

### <a name="example"></a>Exemple

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, result;

   for ( int i = 0 ; i <= 10 ; i++ )
   {
      v1.push_back( i );
   }

   for ( int ii = 0 ; ii <= 4 ; ii++ )
   {
      v2.push_back( 5 );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   swap( v1, v2 );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a>  swap_ranges

Échange les éléments d'une plage avec ceux d'une autre plage de taille égale.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur vers l’avant pointant sur la première position de la première plage dont les éléments doivent être échangés.

*last1*<br/>
Itérateur vers l’avant pointant juste après la dernière position de la première plage dont les éléments doivent être échangés.

*first2*<br/>
Itérateur vers l’avant pointant sur la première position de la deuxième plage dont les éléments doivent être échangés.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant pointant juste après la dernière position de la deuxième plage dont les éléments doivent être échangés.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation. La deuxième plage doit être aussi grande que la première.

La complexité est linéaire avec *last1* - *first1* les permutations. Si les éléments des conteneurs du même type sont échangés, la fonction membre `swap` de ce conteneur doit être utilisée, car la fonction membre a généralement une complexité constante.

### <a name="example"></a>Exemple

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
   using namespace std;
   vector <int> v1;
   deque <int> d1;
   vector <int>::iterator v1Iter1;
   deque<int>::iterator d1Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =4 ; ii <= 9 ; ii++ )
   {
      d1.push_back( 6 );
   }

   cout << "Vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   cout << "Deque d1 is  ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1  << " ";
   cout << ")." << endl;

   swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

   cout << "After the swap_range, vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1 << " ";
   cout << ")." << endl;

   cout << "After the swap_range deque d1 is   ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a>  transform

Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination.

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );
```

### <a name="parameters"></a>Paramètres

*first1*<br/>
Itérateur d’entrée ciblant la position du premier élément de la première plage source à traiter.

*last1*<br/>
Itérateur d’entrée ciblant la position juste après le dernier élément de la première plage source à traiter.

*first2*<br/>
Itérateur d'entrée qui traite la position du premier élément de la seconde plage source à traiter.

*Résultat*<br/>
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

*_Func*<br/>
Objet de fonction unaire défini par l’utilisateur utilisé dans la première version de l’algorithme appliqué à chaque élément de la première plage source, ou objet de fonction binaire défini par l’utilisateur utilisé dans la deuxième version de l’algorithme appliqué par paire, dans un ordre vers l’avant, aux deux plages sources.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située immédiatement après le dernier élément de la plage de destination qui reçoit les éléments de sortie transformés par l'objet de fonction.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation. La plage de destination doit être suffisamment grande pour contenir la plage source transformée.

Si *résultat* est défini comme égal à *first1* dans la première version de l’algorithme, puis les plages source et de destination doit être le même et la séquence sera modifiée en place. Mais le *résultat* ne conviennent pas à une position dans la plage [`first1` + 1, `last1`).

La complexité est linéaire au maximum (`last1` - `first1`) comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
   private:
      Type Factor;   // The value to multiply by
   public:
      // Constructor initializes the value to multiply by
      MultValue ( const Type& val ) : Factor ( val ) {
      }

      // The function call for the element to be multiplied
      Type operator( ) ( Type& elem ) const
      {
         return elem * Factor;
      }
};

int main()
{
   using namespace std;
   vector <int> v1, v2 ( 7 ), v3 ( 7 );
   vector <int>::iterator Iter1, Iter2 , Iter3;

   // Constructing vector v1
   int i;
   for ( i = -4 ; i <= 2 ; i++ )
   {
      v1.push_back(  i );
   }

   cout << "Original vector  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Modifying the vector v1 in place
   transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
   cout << "The elements of the vector v1 multiplied by 2 in place gives:"
        << "\n v1mod = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Using transform to multiply each element by a factor of 5
   transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

   cout << "Multiplying the elements of the vector v1mod\n "
        <<  "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // The second version of transform used to multiply the
   // elements of the vectors v1mod & v2 pairwise
   transform ( v1.begin( ), v1.end( ),  v2.begin( ), v3.begin( ),
      multiplies <int>( ) );

   cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
        <<  "gives:\n v3 = ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

```Output
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>  unique

Supprime les éléments en double adjacents dans une plage spécifiée.

```cpp
template<class ForwardIterator>
   ForwardIterator unique(
      ForwardIterator first,
      ForwardIterator last);

template<class ForwardIterator, class Predicate>
   ForwardIterator unique(
      ForwardIterator first,
      ForwardIterator last,
      Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle rechercher des doublons à supprimer.

*last*<br/>
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage dans laquelle rechercher des doublons à supprimer.

*comp*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant à la fin de la séquence modifiée qui ne contient aucun doublon consécutif, ciblant la position juste après le dernier élément non supprimé.

### <a name="remarks"></a>Notes

Les deux formes de l’algorithme suppriment le deuxième doublon d’une paire consécutive d’éléments égaux.

Le fonctionnement de l’algorithme est stable pour ne pas modifier l’ordre relatif des éléments rétablis.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation. le nombre d’éléments dans la séquence n’est pas modifié par l’algorithme `unique` et les éléments situés après la fin de la séquence modifiée sont déréférencés n’est pas spécifié.

La complexité est linéaire et nécessite (`last` - `first`) - 1 comparaisons.

La classe list fournit une fonction membre « unique » plus efficace qui peut donner de meilleurs résultats.

Ces algorithmes ne peuvent pas être utilisés sur un conteneur associatif.

### <a name="example"></a>Exemple

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 == elem2;
};

int main()
{
   vector <int> v1;
   vector <int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
         v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( 5 );
      v1.push_back( -5 );
   }

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
   {
      v1.push_back( 4 );
   }
   v1.push_back( 7 );

   cout << "Vector v1 is ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Remove consecutive duplicates
   v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

   cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Remove consecutive duplicates under the binary prediate mod_equals
   v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

   cout << "Removing adjacent duplicates from vector v1 under the\n "
        << " binary predicate mod_equal gives\n ( " ;
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
      cout << *v1_Iter2 << " ";
   cout << ")." << endl;

   // Remove elements if preceded by an element that was greater
   v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

   cout << "Removing adjacent elements satisfying the binary\n "
        << " predicate mod_equal from vector v1 gives ( " ;
   for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
      cout << *v1_Iter3 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a>  unique_copy

Copie les éléments d'une plage source dans une plage de destination, à l'exception des éléments en double adjacents.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy( InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy( InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Itérateur vers l’avant ciblant la position du premier élément de la plage source à copier.

*last*<br/>
Itérateur vers l’avant ciblant la position située de suite après le dernier élément de la plage source à copier.

*Résultat*<br/>
Itérateur de sortie ciblant la position du premier élément dans la plage de destination recevant la copie avec suppression des doublons consécutifs.

*comp*<br/>
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément dans la plage de destination recevant la copie avec suppression des doublons consécutifs.

### <a name="remarks"></a>Notes

Les deux formes de l’algorithme suppriment le deuxième doublon d’une paire consécutive d’éléments égaux.

Le fonctionnement de l’algorithme est stable pour ne pas modifier l’ordre relatif des éléments rétablis.

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans une séquence, la dernière position est accessible depuis la première au moyen d’une incrémentation.

La complexité est linéaire et nécessite (`last` - `first`) comparaisons.

### <a name="example"></a>Exemple

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 == elem2;
};

int main() {
   vector <int> v1;
   vector <int>::iterator v1_Iter1, v1_Iter2,
         v1_NewEnd1, v1_NewEnd2;

   int i;
   for ( i = 0 ; i <= 1 ; i++ ) {
      v1.push_back( 5 );
      v1.push_back( -5 );
   }

   int ii;
   for ( ii = 0 ; ii <= 2 ; ii++ )
      v1.push_back( 4 );
   v1.push_back( 7 );

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
      v1.push_back( 10 );

   cout << "Vector v1 is\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Copy first half to second, removing consecutive duplicates
   v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

   cout << "Copying the first half of the vector to the second half\n "
        << "while removing adjacent duplicates gives\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   int iv;
   for ( iv = 0 ; iv <= 7 ; iv++ )
      v1.push_back( 10 );

   // Remove consecutive duplicates under the binary prediate mod_equals
   v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
      v1.begin( ) + 14 , mod_equal );

   cout << "Copying the first half of the vector to the second half\n "
        << " removing adjacent duplicates under mod_equals gives\n ( " ;
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
      cout << *v1_Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="upper_bound"></a>  upper_bound

Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator, class Type>
   ForwardIterator upper_bound(
      ForwardIterator first,
      ForwardIterator last,
      const Type& value);

template<class ForwardIterator, class Type, class Predicate>
   ForwardIterator upper_bound(
      ForwardIterator first,
      ForwardIterator last,
      const Type& value,
      Predicate comp);
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Position du premier élément de la plage dans laquelle effectuer la recherche.

*last*<br/>
Position juste après le dernier élément de la plage dans laquelle effectuer la recherche.

*valeur*<br/>
Valeur dans la plage ordonnée qui doit être dépassée par la valeur de l’élément ciblé par l’itérateur retourné.

*comp*<br/>
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position du premier élément ayant une valeur supérieure à une valeur spécifiée.

### <a name="remarks"></a>Notes

Le plage source triée référencée doit être valide ; tous les itérateurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Une plage triée est une condition préalable à l’utilisation de `upper_bound` et son critère d’ordre est identique à celui spécifié par le prédicat binaire.

La plage n’est pas modifiée par l’algorithme `upper_bound`.

Les types valeur des itérateurs vers l’avant doivent être comparables en termes d’infériorité pour être ordonnés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. De cette façon, les éléments non équivalents sont ordonnés

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire sinon, avec le nombre d’étapes proportionnel à (`last - first`).

### <a name="example"></a>Exemple

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back(  i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back(  ii  );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate  mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3,  mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="see-also"></a>Voir aussi

[\<algorithm>](../standard-library/algorithm.md)<br/>
