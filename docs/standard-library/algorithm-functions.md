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
ms.openlocfilehash: f389d38cf84f8f72d12242e798010d53a26f81a8
ms.sourcegitcommit: 20a1356193fbe0ddd1002e798b952917eafc3439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661539"
---
# <a name="ltalgorithmgt-functions"></a>&lt;algorithm&gt;, fonctions

## <a name="adjacent_find"></a>adjacent_find

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
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*famille*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*prédit*\
Prédicat binaire indiquant la condition à satisfaire par les valeurs des éléments adjacents de la plage dans laquelle s’effectue la recherche.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant vers le premier des éléments adjacents qui sont égaux entre eux (dans la première version) ou qui répondent à la condition donnée par le prédicat binaire (dans la deuxième version), à condition qu’une paire d’éléments de ce type soit trouvée. Dans le cas contraire, un itérateur pointant vers *Last* est retourné.

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
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

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
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>all_of

Retourne la **valeur true** lorsqu’une condition est présente à chaque élément d’une plage donnée.

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début de la recherche d’une condition. L’itérateur marque le début d’une plage d’éléments.

*famille*\
Itérateur d’entrée qui indique la fin d’une plage d’éléments dans laquelle rechercher une condition.

*prédit*\
Condition à vérifier. Il s’agit d’un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire par l’élément vérifié. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** si la condition est détectée à chaque élément de la plage indiquée ou si la plage est vide, et false dans le cas contraire.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si, pour `N` chaque de la `[0, last - first)`plage, le prédicat `pred(*(first + N))` a la **valeur true**.

### <a name="example"></a>Exemple

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a>any_of

Retourne la **valeur true** lorsqu’une condition est présente au moins une fois dans la plage d’éléments spécifiée.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début de la recherche d’une condition dans une plage d’éléments.

*famille*\
Itérateur d’entrée qui indique la fin d’une plage d’éléments dans laquelle rechercher une condition.

*prédit*\
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur. Le prédicat définit la condition à satisfaire par l’élément vérifié. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** si la condition est détectée au moins une fois dans la plage indiquée, false si la condition n’est jamais détectée.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si, pour `N` une partie de la plage

`[0, last - first)`, le prédicat `pred(*(first + N))` a la valeur true.

### <a name="example"></a>Exemple

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a>binary_search

Teste si un élément d’une plage triée est égal à une valeur spécifiée ou équivalent, selon une condition spécifiée par un prédicat binaire.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*famille*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*value*\
Valeur qui doit correspondre à la valeur de l’élément ou qui doit satisfaire la condition avec la valeur d’élément spécifiée par le prédicat binaire.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si un élément se trouve dans la plage qui est égale ou équivalente à la valeur spécifiée; Sinon, **false**.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Les plages triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `binary_search` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

Les plages sources ne sont pas modifiées par `binary_search`.

Les types valeur des itérateurs vers l’avant doivent être comparables en termes d’infériorité pour être triés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. De cette façon, les éléments non équivalents sont ordonnés

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire dans le cas contraire, avec le nombre d'`last`étapes proportionnelles à ( - `first`).

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

    list<int> List1;

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

```Output
List1 = ( 5 10 20 25 30 50 )
There is an element in list List1 with a value equal to 10.
There is an element in list List1 with a value greater than 10 under greater than.
Ordered using mod_lesser, vector v1 = ( 0 -1 1 -2 2 3 4 )
There is an element with a value equivalent to -3 under mod_lesser.
```

## <a name="clamp"></a>bride

Compare une valeur à une limite supérieure et inférieure, et retourne une référence à la valeur si elle est comprise entre les limites ou une référence à la limite supérieure ou inférieure si la valeur est supérieure ou inférieure à celle-ci, respectivement.

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*value*\
Valeur à comparer en *majuscules* et en *minuscules*.

*inférieur*\
Limite inférieure des valeurs auxquelles fixer la *valeur* .

*coin*\
Limite supérieure des valeurs auxquelles fixer la *valeur* .

*prédit*\
Prédicat utilisé pour comparer la valeur à la *valeur* *inférieure* ou *supérieure*. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** si le premier est dans un sens inférieur à la seconde, et **false**dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à *Lower* si `value < lower`, ou une référence à *Upper* si `upper < value`. Sinon, elle retourne une référence à *value*.

### <a name="remarks"></a>Notes

Le comportement n’est pas défini si *Upper* est inférieur à *Lower*.

## <a name="copy"></a>reprographie

Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions, du haut vers le bas.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée ciblant la position du premier élément dans la plage source.

*famille*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la plage source.

*destBeg*\
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination, autrement dit, l' `result` itérateur adresse + (*Last* - *First*).

### <a name="remarks"></a>Notes

La plage source doit être valide et il doit y avoir suffisamment d'espace au niveau de la destination pour contenir tous les éléments qui sont copiés.

Étant donné que l’algorithme copie les éléments sources dans l’ordre en commençant par le premier élément, la plage de destination peut se chevaucher avec la plage source, à condition que la *dernière* position de la plage source ne soit pas contenue dans la plage de destination. `copy`peut être utilisé pour décaler des éléments vers la gauche mais pas vers la droite, sauf s’il n’existe aucun chevauchement entre les plages source et de destination. Pour décaler vers la droite d’un nombre quelconque de positions, utilisez l’algorithme [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="copy_backward"></a>copy_backward

Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions vers le haut.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur bidirectionnel se rapportant à la position du premier élément dans la plage source.

*famille*\
Itérateur bidirectionnel se rapportant à la position située immédiatement après l'élément final dans la plage source.

*destEnd*\
Itérateur bidirectionnel se rapportant à la position située immédiatement après l'élément final dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination, autrement dit, l’itérateur adresse *destEnd* -(*Last* - *First*).

### <a name="remarks"></a>Notes

La plage source doit être valide et il doit y avoir suffisamment d'espace au niveau de la destination pour contenir tous les éléments qui sont copiés.

L' `copy_backward` algorithme impose des exigences plus strictes que `copy` celles de l’algorithme. Ses itérateurs d'entrée et de sortie doivent être bidirectionnels.

Les algorithmes `copy_backward` et [move_backward](../standard-library/algorithm-functions.md#move_backward) sont les seuls algorithmes de la bibliothèque C++ Standard qui désignent la plage de sortie avec un itérateur pointant vers la fin de la plage de destination.

Étant donné que l’algorithme copie les éléments sources dans l’ordre en commençant par le dernier élément, la plage de destination peut se chevaucher avec la plage source, à condition que la *première* position de la plage source ne soit pas contenue dans la plage de destination. `copy_backward` peut être utilisé pour décaler des éléments vers la droite mais pas vers la gauche, à moins qu'il n'y ait aucun chevauchement entre la plage source et celle de destination. Pour décaler vers la gauche d’un nombre quelconque de positions, utilisez l’algorithme [copy](../standard-library/algorithm-functions.md#copy).

L'algorithme `copy_backward` modifie uniquement les valeurs sur lesquelles pointent les itérateurs, assignant de nouvelles valeurs aux éléments dans la plage de destination. Il ne peut pas être utilisé pour créer de nouveaux éléments et ne peut pas insérer directement d'éléments dans un conteneur vide.

### <a name="example"></a>Exemples

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 6 9 0 10 0 10 20 27 30 )
```

## <a name="copy_if"></a>copy_if

Dans une plage d’éléments, copie les éléments qui ont la **valeur true** pour la condition spécifiée.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début d’une plage dans laquelle rechercher la condition.

*famille*\
Itérateur d’entrée qui indique la fin de la plage.

*dest*\
Itérateur de sortie qui indique la destination des éléments copiés.

*prédit*\
Condition pour laquelle chaque élément de la plage est vérifié. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur. Un prédicat unaire accepte un argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie dont la valeur de *dest* est incrémentée une fois pour chaque élément répondant à la condition. En d’autres termes, la valeur de retour moins *dest* est égale au nombre d’éléments copiés.

### <a name="remarks"></a>Notes

La fonction de modèle évalue

`if (pred(*first + N)) * dest++ = *(first + N))`

une fois pour chaque `N` de la plage `[0, last - first)`, pour les valeurs strictement croissantes de `N` en commençant par la valeur la plus petite. Si *dest* et désignent d' *abord* les régions de stockage, la *destination* ne `[ first, last )`doit pas être comprise dans la plage.

### <a name="example"></a>Exemple

```cpp
// alg_copy_if.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

void listlist(std::list<int> l)
{
    std::cout << "( ";
    for (auto const& el : l)
        std::cout << el << " ";
    std::cout << ")" << std::endl;
}

int main()
{
    using namespace std;
    list<int> li{ 46, 59, 88, 72, 79, 71, 60, 5, 40, 84 };
    list<int> le(li.size()); // le = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
    list<int> lo(li.size()); // lo = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    cout << "li = ";
    listlist(li);

    // is_even checks if the element is even.
    auto is_even = [](int const elem) { return !(elem % 2); };
    // use copy_if to select only even elements from li 
    // and copy them to le, starting from le's begin position
    auto ec = copy_if(li.begin(),li.end(), le.begin(), is_even);
    le.resize(std::distance(le.begin(), ec));  // shrink le to new size

    cout << "Even numbers are le = ";
    listlist(le);

    // is_odd checks if the element is odd.
    auto is_odd = [](int const elem) { return (elem % 2); };
    // use copy_if to select only odd elements from li
    // and copy them to lo, starting from lo's begin position
    auto oc = copy_if(li.begin(), li.end(), lo.begin(), is_odd);
    lo.resize(std::distance(lo.begin(), oc));  // shrink lo to new size

    cout << "Odd numbers are lo = ";
    listlist(lo);
}
```

```Output
li = ( 46 59 88 72 79 71 60 5 40 84 )
Even numbers are le = ( 46 88 72 60 40 84 )
Odd numbers are lo = ( 59 79 71 5 )
```

## <a name="copy_n"></a>copy_n

Copie un nombre spécifié d'éléments.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d'entrée qui indique l'emplacement à partir duquel les éléments doivent être copiés.

*saut*\
Type entier signé ou non signé spécifiant le nombre d'éléments à copier.

*dest*\
Itérateur de sortie qui indique l'emplacement où les éléments doivent être copiés.

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur de sortie indiquant où les éléments ont été copiés. Il est identique à la valeur retournée du paramètre *dest* .

### <a name="remarks"></a>Notes

La fonction `*(dest + N) = *(first + N))` de modèle évalue une fois pour chaque `N` dans `[0, count)`la plage, pour les valeurs `N` strictement croissantes de à partir de la valeur la plus faible. Elle retourne ensuite `dest + N`. Si *dest* et désignent d' *abord* les régions de stockage, la *destination* ne `[first, last)`doit pas être comprise dans la plage.

### <a name="example"></a>Exemple

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a>saut

Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée ciblant la position du premier élément de la plage à traverser.

*famille*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la plage à traverser.

*value*\
Valeur des éléments à compter.

### <a name="return-value"></a>Valeur de retour

Type de différence `InputIterator` du qui compte le nombre d’éléments de la plage [*First*, *Last*) qui ont la valeur *value.*

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

## <a name="count_if"></a>count_if

Retourne le nombre d’éléments d’une plage dont les valeurs satisfont une condition spécifiée.

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d'entrée qui traite la position du premier élément de la plage à rechercher.

*famille*\
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage à rechercher.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire si un élément doit être compté. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

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

## <a name="equal"></a>valeur

Compare deux plages, élément par élément, à la recherche d’une égalité ou d’une équivalence, selon une condition spécifiée par un prédicat binaire.

Utilisez `std::equal` quand vous comparez des éléments de différents types de conteneurs (par exemple `vector` et `list`) ou différents types d’éléments, ou quand vous devez comparer des sous-plages de conteneurs. Sinon, quand vous comparez des éléments du même type dans le même type de conteneur, utilisez l’`operator==` de non-membre fourni pour chaque conteneur.

Utilisez les surcharges à double portée dans le code C++14, car les surcharges qui ne prennent qu'un seul itérateur pour la deuxième plage ne détecteront pas les différences si la deuxième plage est plus longue que la première et provoqueront un comportement non défini si la deuxième plage est plus courte que la première.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d'entrée qui traite la position du premier élément de la première plage à tester.

*last1*\
Itérateur d'entrée qui traite la position qui suit le dernier élément de la première plage à tester.

*First2*\
Itérateur d'entrée qui traite la position du premier élément de la deuxième plage à tester.

*last2*\
Itérateur d'entrée qui traite la position qui suit le dernier élément de la deuxième plage à tester.

*prédit*\
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si et seulement si les plages sont identiques ou équivalentes sous le prédicat binaire en cas de comparaison élément par élément ; sinon, **false**.

### <a name="remarks"></a>Notes

La plage dans laquelle s'effectue la recherche doit être valide. Tous les itérateurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible depuis la première par incrémentation.

Si les deux plages sont de longueur égale, la complexité temporelle de l'algorithme est linéaire quant au nombre d'éléments contenus dans la plage. Dans le cas contraire,la fonction retourne immédiatement false.

Ni le `operator==`, ni le prédicat défini par l'utilisateur ne doit obligatoirement imposer une relation d'équivalence qui est symétrique, réflexive et transitive entre ses opérandes.

### <a name="example"></a>Exemples

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

## <a name="equal_range"></a>equal_range

Dans une plage ordonnée définie, recherche la sous-plage dans laquelle tous les éléments sont équivalents à une valeur donnée.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*famille*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*value*\
Valeur recherchée dans la plage ordonnée.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** lorsque la valeur est satisfaite et false lorsqu’elle n’est pas satisfaite.

### <a name="return-value"></a>Valeur de retour

Paire d’itérateurs vers l’avant qui spécifient une sous-plage, contenue dans la plage recherchée, dans laquelle tous les éléments sont équivalents à la *valeur* dans le sens défini par le prédicat binaire utilisé ( *prédite* ou par défaut, inférieur à).

Si aucun élément de la plage n’est équivalent à *value*, les itérateurs vers l’avant dans la paire retournée sont égaux et spécifient le point où la *valeur* peut être insérée sans perturber l’ordre de la plage.

### <a name="remarks"></a>Notes

Le premier itérateur de la paire retournée par l’algorithme est [lower_bound](../standard-library/algorithm-functions.md#lower_bound) et le deuxième est [upper_bound](../standard-library/algorithm-functions.md#upper_bound).

La plage doit être triée selon le prédicat fourni à `equal_range`. Par exemple, si vous comptez utiliser le prédicat Supérieur à, la plage doit être triée par ordre décroissant.

Les éléments de la sous-plage éventuellement vide définie par la paire d’itérateurs `equal_range` retournées par sont équivalents à la *valeur* dans le sens défini par le prédicat utilisé.

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire dans le cas contraire, avec le nombre d’étapes proportionnels à (*Last* - *First*).

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

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
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
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
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
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
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

## <a name="fill"></a>complète

Affecte la même nouvelle valeur à chaque élément d'une plage spécifiée.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage à traverser.

*famille*\
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage à traverser.

*value*\
Valeur à assigner aux éléments de la plage [*First*, *Last*).

### <a name="remarks"></a>Notes

La plage de destination doit être valide. Tous les pointeurs doivent pouvoir être déréférencés. Par ailleurs, la dernière position est accessible à partir de la première par incrémentation. La complexité est linéaire par rapport à la taille de la plage.

### <a name="example"></a>Exemples

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="fill_n"></a>fill_n

Attribue une nouvelle valeur à un nombre spécifié d’éléments d’une plage commençant par un élément particulier.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur de sortie ciblant la position du premier élément de la plage à laquelle la valeur de la valeur doit être *affectée.*

*saut*\
Type entier signé ou non signé spécifiant le nombre d’éléments auxquels attribuer une valeur.

*value*\
Valeur à assigner aux éléments de la plage [*First*, *First + Count*).

### <a name="return-value"></a>Valeur de retour

Itérateur de l’élément qui suit le dernier élément rempli si le *nombre* > zéro, sinon le premier élément.

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
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
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

## <a name="find"></a>trouver

Recherche la position de la première occurrence d'un élément d'une plage ayant une valeur spécifiée.

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d'entrée qui traite la position du premier élément de la plage où effectuer la recherche de la valeur spécifiée.

*famille*\
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage où effectuer la recherche de la valeur spécifiée.

*value*\
Valeur à rechercher.

### <a name="return-value"></a>Valeur de retour

Itérateur d'entrée qui traite la première occurrence de la valeur spécifiée dans la plage où effectuer la recherche. Si aucun élément n’est trouvé avec une valeur équivalente, retourne *Last*.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Pour obtenir un exemple de code avec `find()`, consultez [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="find_end"></a>find_end

Recherche dans une plage la dernière sous-séquence qui est identique à une séquence spécifiée ou qui est équivalente, selon une condition spécifiée par un prédicat binaire.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*First1*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*First2*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last2*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*prédit*\
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position du premier élément de la dernière sous-séquence dans [First1, last1) qui correspond à la séquence spécifiée [First2, last2).

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

### <a name="example"></a>Exemples

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
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
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

## <a name="find_first_of"></a>find_first_of

Recherche la première occurrence parmi plusieurs valeurs d’une plage cible, ou la première occurrence parmi plusieurs éléments qui sont équivalents, selon une condition spécifiée par un prédicat binaire, à un ensemble d’éléments spécifiés.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*First1*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*First2*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la correspondance.

*last2*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la correspondance.

*prédit*\
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
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
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

## <a name="find_if"></a>find_if

Recherche la position de la première occurrence d'un élément d'une plage qui répond à une condition spécifiée.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d'entrée qui traite la position du premier élément de la plage à rechercher.

*famille*\
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage à rechercher.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur ou [expression lambda](../cpp/lambda-expressions-in-cpp.md) qui définit la condition à satisfaire par l’élément recherché. Un prédicat unaire accepte un seul argument et retourne **true** s’il est satisfait ou false s’il n’est pas respecté. La signature de *prédit* doit être `bool pred(const T& arg);`effectivement, où `T` est un type dans lequel `InputIterator` peut être converti implicitement lorsqu’il est déréférencé. Le mot clé const s’affiche uniquement pour illustrer que l’objet de fonction ou l’expression lambda ne doit pas modifier l’argument.

### <a name="return-value"></a>Valeur de retour

Itérateur d’entrée qui fait référence au premier élément de la plage qui répond à la condition spécifiée par le prédicat (le prédicat donne la **valeur true**). Si aucun élément n’est trouvé pour satisfaire le prédicat, retourne *Last*.

### <a name="remarks"></a>Notes

Cette fonction de modèle est une généralisation de l’algorithme [find](../standard-library/algorithm-functions.md#find) et remplace le prédicat « est égal à une valeur spécifique » par un autre prédicat. Pour l’opposé logique (rechercher le premier élément qui ne satisfait pas le prédicat), consultez [find_if_not](../standard-library/algorithm-functions.md#find_if_not).

### <a name="example"></a>Exemples

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

## <a name="find_if_not"></a>find_if_not

Retourne le premier élément d'une plage spécifiée qui ne répond pas à une condition.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d'entrée qui traite la position du premier élément de la plage à rechercher.

*famille*\
Itérateur d'entrée qui traite la position située au-delà du dernier élément de la plage à rechercher.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur ou [expression lambda](../cpp/lambda-expressions-in-cpp.md) qui définit la condition à ne pas satisfaire par l’élément recherché. Un prédicat unaire accepte un seul argument et retourne **true** s’il est satisfait ou false s’il n’est pas respecté. La signature de *prédit* doit être `bool pred(const T& arg);`effectivement, où `T` est un type dans lequel `InputIterator` peut être converti implicitement lorsqu’il est déréférencé. Le mot clé const s’affiche uniquement pour illustrer que l’objet de fonction ou l’expression lambda ne doit pas modifier l’argument.

### <a name="return-value"></a>Valeur de retour

Itérateur d’entrée qui fait référence au premier élément de la plage qui ne satisfait pas la condition spécifiée par le prédicat (le prédicat donne la **valeur false**). Si tous les éléments répondent au prédicat (le prédicat donne la **valeur true** à chaque élément), retourne *Last*.

### <a name="remarks"></a>Notes

Cette fonction de modèle est une généralisation de l’algorithme [find](../standard-library/algorithm-functions.md#find) et remplace le prédicat « est égal à une valeur spécifique » par un autre prédicat. Pour l’opposé logique (rechercher le premier élément qui satisfait le prédicat), consultez [find_if](../standard-library/algorithm-functions.md#find_if).

Pour obtenir un exemple de code facilement adaptable à `find_if_not()`, consultez [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a>for_each

Applique un objet de fonction spécifié à chaque élément d'une plage, du haut vers le bas, et retourne l'objet de la fonction.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée ciblant la position du premier élément de la plage à traiter.

*famille*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la plage à traiter.

*Func*\
Objet de fonction défini par l’utilisateur appliqué à chaque élément de la plage.

### <a name="return-value"></a>Valeur de retour

Copie de l’objet de fonction une fois qu’il a été appliqué à tous les éléments de la plage.

### <a name="remarks"></a>Notes

L’algorithme `for_each` est très souple et autorise la modification de chaque élément d’une plage de différentes façons spécifiées par l’utilisateur. Vous pouvez réutiliser des fonctions modélisées sous une forme modifiée en passant des paramètres différents. Les fonctions définies par l’utilisateur peuvent accumuler des informations dans un état interne que l’algorithme peut retourner après le traitement de tous les éléments de la plage.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire avec au maximum (*dernière* - *priorité*) comparaisons.

### <a name="example"></a>Exemples

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
    MultValue ( const Type& value ) : Factor ( value ) {
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
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
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
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a>automatiquement

Assigne les valeurs générées par un objet de fonction à chaque élément d'une plage.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage auquel les valeurs doivent être attribuées.

*famille*\
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage auquel les valeurs doivent être attribuées.

*général*\
Objet de fonction qui est appelé sans argument qui permet de générer les valeurs à assigner à chacun des éléments de la plage.

### <a name="remarks"></a>Notes

L'objet de fonction est appelé pour chaque élément de la plage et n'a pas besoin de retourner la même valeur à chaque appel. Il peut, par exemple, lire un fichier ou référencer et modifier un état local. Le type de résultat du générateur doit être convertible dans le type de valeur des itérateurs de transfert pour la plage.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire, avec exactement ( `last`  -  `first`) les appels au générateur requis.

### <a name="example"></a>Exemples

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
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

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

## <a name="generate_n"></a>generate_n

Assigne les valeurs générées par un objet de fonction à un nombre spécifié d'éléments d'une plage et retourne à la position située juste après la dernière valeur assignée.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur de sortie se rapportant à la position du premier élément dans la plage auquel les valeurs doivent être assignées.

*saut*\
Type entier signé ou non signé spécifiant le nombre d'éléments auxquels une valeur doit être assignée par la fonction de générateur.

*général*\
Objet de fonction qui est appelé sans argument qui permet de générer les valeurs à assigner à chacun des éléments de la plage.

### <a name="remarks"></a>Notes

L'objet de fonction est appelé pour chaque élément de la plage et n'a pas besoin de retourner la même valeur à chaque appel. Il peut, par exemple, lire un fichier ou référencer et modifier un état local. Le type de résultat du générateur doit être convertible dans le type de valeur des itérateurs de transfert pour la plage.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire, avec exactement `count` appels au générateur requis.

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

template <typename C>
void print(const string& s, const C& c)
{
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

## <a name="includes"></a>offre

Teste si une plage triée contient tous les éléments d’une autre plage triée. Le critère de tri ou d’équivalence entre les éléments peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément de la première de deux plages sources triées à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*last1*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la première de deux plages sources triées à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*First2*\
Itérateur d’entrée ciblant la position du premier élément de la deuxième de deux plages sources triées consécutives à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*last2*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la deuxième de deux plages sources triées consécutives à vérifier pour déterminer si tous les éléments de la deuxième sont contenus dans la première.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** lorsque la valeur est satisfaite et false lorsqu’elle n’est pas satisfaite.

### <a name="return-value"></a>Valeur de retour

**true** si la première plage triée contient tous les éléments de la deuxième ; sinon, **false**.

### <a name="remarks"></a>Notes

Une autre façon d’interpréter ce test est de déterminer si la deuxième plage source est un sous-ensemble de la première plage source.

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Les plages sources triées doivent chacune être organisées comme une condition préalable à l’application de l’algorithme includes selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

Les plages sources ne sont pas modifiées par l' `merge`algorithme.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Plus précisément, l’algorithme vérifie si tous les éléments de la première plage triée sous un prédicat binaire spécifié sont ordonnés de la même façon que ceux de la deuxième plage triée.

La complexité de l’algorithme est linéaire avec au `2 * ((last1 - first1) - (last2 - first2)) - 1` maximum les comparaisons pour les plages sources non vides.

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
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
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
        v2b.begin( ), v2b.end( ), greater<int>( ) );
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
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>inplace_merge

Regroupe les éléments de deux plages triées consécutives au sein d’une même plage triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur bidirectionnel ciblant la position du premier élément de la première de deux plages triées consécutives à regrouper en une seule plage et trier.

*intergiciel*\
Itérateur bidirectionnel ciblant la position du premier élément de la deuxième de deux plages triées consécutives à regrouper en une seule plage et trier.

*famille*\
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la deuxième de deux plages triées consécutives à regrouper en une seule plage et trier.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat de comparaison accepte deux arguments et doit retourner la **valeur true** lorsque le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Les plages triées consécutives référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Les plages triées consécutives doivent chacune être organisées comme une condition préalable à l’application de l’algorithme `inplace_merge` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées. L’opération est stable, car l’ordre relatif des éléments de chaque plage est préservé. Quand il existe des éléments équivalents dans les deux plages sources, l’élément de la première plage précède celui de la deuxième dans la plage regroupée.

La complexité dépend de la mémoire disponible, car l’algorithme alloue de la mémoire à une mémoire tampon temporaire. Si une quantité suffisante de mémoire est disponible, le meilleur cas `(last - first) - 1` est linéaire avec les comparaisons; si aucune mémoire auxiliaire n’est disponible `N log(N)`, le pire des cas est, où *n* = pour la*dernière* - *fois*.

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
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
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
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
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

## <a name="is_heap"></a>is_heap

Retourne la **valeur true** si les éléments de la plage spécifiée forment un segment de mémoire.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’accès aléatoire qui indique le début d’une plage dans laquelle rechercher un tas.

*famille*\
Itérateur d’accès aléatoire qui indique la fin d’une plage.

*prédit*\
Condition à vérifier pour ordonner des éléments. Un prédicat de comparaison accepte deux arguments et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** si les éléments de la plage spécifiée forment un tas, false dans le cas contraire.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`.

La deuxième fonction de modèle retourne

`is_heap_until(first, last, pred) == last`.

## <a name="is_heap_until"></a>is_heap_until

Retourne un itérateur positionné au premier élément de la plage [ `first`, `last`) qui ne satisfait pas la condition d’ordonnancement du tas, ou *end* si la plage forme un tas.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur à accès aléatoire qui spécifie le premier élément d'une plage dans laquelle effectuer la recherche d'un tas.

*famille*\
Itérateur à accès aléatoire qui spécifie le dernier élément de la plage où effectuer la recherche d'un tas.

*prédit*\
Prédicat binaire qui spécifie la condition d'ordonnancement faible strict qui définit un tas. Le prédicat par défaut est `std::less<>` lorsque l’option *prédit* n’est pas spécifiée.

### <a name="return-value"></a>Valeur de retour

Retourne *Last* si la plage spécifiée forme un tas ou contient un ou plusieurs éléments. Sinon, retourne un itérateur pointant vers le premier élément trouvé qui ne remplit pas la condition de tas.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne le dernier `next` itérateur `[first, last)` dans `[first, next)` où est un tas ordonné par l’objet `std::less<>`de fonction. Si la distance `last - first` est inférieure à 2, la fonction retourne *Last*.

La deuxième fonction de modèle se comporte comme la première, sauf qu’elle utilise le prédicat *prédit* au lieu de comme condition `std::less<>` d’ordonnancement du tas.

## <a name="is_partitioned"></a>is_partitioned

Retourne la **valeur true** si tous les éléments d’une plage donnée qui testent la **valeur true** pour une condition précèdent tous les éléments qui testent **false**.

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début de la recherche d’une condition dans une plage.

*famille*\
Itérateur d’entrée qui indique la fin d’une plage.

*prédit*\
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire par l’élément recherché. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** lorsque tous les éléments d’une plage donnée qui testent la **valeur true** pour une condition sont placés avant les éléments qui testent **false**, et sinon, retourne **false**.

### <a name="remarks"></a>Notes

La fonction de modèle **retourne true** uniquement si tous les `[first, last)` éléments de sont partitionnés par *prédit*; autrement dit, `X` tous `[first, last)` les éléments `pred (X)` dans pour lesquels est true se `Y` produisent avant tous les éléments pour lesquels a la **valeur false.** `pred (Y)`

## <a name="is_permutation"></a>is_permutation

Retourne la valeur true si les deux plages contiennent les mêmes éléments, même s'ils ne sont pas dans le même ordre. Utilisez les surcharges à double portée dans le code C++14, car les surcharges qui ne prennent qu'un seul itérateur pour la deuxième plage ne détecteront pas les différences si la deuxième plage est plus longue que la première et provoqueront un comportement non défini si la deuxième plage est plus courte que la première.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*First1*\
Itérateur vers l'avant qui fait référence au premier élément de la plage.

*last1*\
Itérateur vers l'avant qui fait référence à l'élément qui suit le dernier élément de la plage.

*First2*\
Itérateur vers l'avant qui fait référence au premier élément d'une deuxième plage, utilisé à des fins de comparaison.

*last2*\
Itérateur vers l'avant qui fait référence à l'élément qui suit le dernier élément d'une deuxième plage, utilisé à des fins de comparaison.

*prédit*\
Prédicat qui teste l’équivalence et retourne une valeur **booléenne**.

### <a name="return-value"></a>Valeur de retour

**true** lorsque les plages peuvent être réorganisées pour être identiques en fonction du prédicat du comparateur; Sinon, **false**.

### <a name="remarks"></a>Notes

`is_permutation` a une complexité quadratique dans le pire des cas.

La première fonction de modèle part du principe qu’il existe autant d’éléments dans la plage commençant à *First2* que dans la plage désignée par `[first1, last1)`. S'il y a plus d'éléments dans la deuxième plage, ils sont ignorés ; s'il y en a moins, le comportement est non défini. La troisième fonction de modèle (C++14 et versions ultérieures) ne part pas de ce principe. Les deux renvoient **true** uniquement si, pour chaque élément x dans la plage `[first1, last1)` désignée par, il y a autant d’éléments y dans la même plage pour lesquels x = = y, comme dans la plage commençant `[first2, last2)`à *First2* ou. Ici, `operator==` doit effectuer une comparaison par paire entre ses opérandes.

Les deuxième et quatrième fonctions avec modèle ont le même comportement, hormis le fait qu'elles remplacent `operator==(X, Y)` par `Pred(X, Y)`. Pour se comporter correctement, le prédicat doit être symétrique, réflexif et transitif.

### <a name="example"></a>Exemples

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

## <a name="is_sorted"></a>is_sorted

Retourne la **valeur true** si les éléments de la plage spécifiée sont triés.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant qui indique où commence la plage à vérifier.

*famille*\
Itérateur vers l’avant qui indique la fin d’une plage.

*prédit*\
Condition à vérifier pour déterminer un ordre entre deux éléments. Un prédicat de comparaison accepte deux arguments et retourne **true** ou **false**. Il effectue la même tâche que `operator<`.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne [is_sorted_until](#is_sorted_until)`( first, last ) == last`. La `operator<` fonction effectue la comparaison d’ordre.

La deuxième fonction de modèle `is_sorted_until( first, last , pred ) == last`retourne. La fonction de prédicat *prédit* effectue la comparaison d’ordre.

## <a name="is_sorted_until"></a>is_sorted_until

Retourne un `ForwardIterator` défini sur le dernier élément qui se trouve dans l’ordre trié d’une plage spécifiée.

La deuxième version vous permet de fournir un objet de fonction de comparaison qui retourne la **valeur true** lorsque deux éléments donnés sont triés, et false dans le cas contraire.

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant qui indique où commence la plage à vérifier.

*famille*\
Itérateur vers l’avant qui indique la fin d’une plage.

*prédit*\
Condition à vérifier pour déterminer un ordre entre deux éléments. Un prédicat de comparaison accepte deux arguments et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne un `ForwardIterator` défini sur le dernier élément dans un ordre trié. La séquence triée commence par la *première*.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne le dernier `next` itérateur `[first, last]` dans afin `[first, next)` qu’il s’agit d’une `operator<`séquence triée ordonnée par. Si `distance()` est inférieur à 2, la fonction retourne *Last*.

La deuxième fonction de modèle se comporte de la même façon, sauf qu’elle remplace `operator<(X, Y)` par `pred(X, Y)`.

## <a name="iter_swap"></a>iter_swap

Échange deux valeurs référencées par une paire d'itérateurs spécifiés.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>Paramètres

*gauche*\
Un des itérateurs vers l’avant dont la valeur est à échanger.

*Oui*\
Le deuxième des itérateurs vers l’avant dont la valeur est à échanger.

### <a name="remarks"></a>Notes

`swap`doit être utilisé de préférence à **iter_swap**, qui a été inclus dans C++ la norme pour la compatibilité descendante. Si `Fit1` `iter_swap( Fit1, Fit2 )` `swap( *Fit1, *Fit2 )`et `Fit2` sont des itérateurs vers l’avant, est équivalent à.

Les types valeur des itérateurs vers l’avant/d’entrée doivent avoir la même valeur.

### <a name="example"></a>Exemples

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
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

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

## <a name="lexicographical_compare"></a>lexicographical_compare

Compare deux séquences, élément par élément, pour déterminer lequel est inférieur à l'autre.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément de la première plage à comparer.

*last1*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la première plage à comparer.

*First2*\
Itérateur d’entrée ciblant la position du premier élément de la deuxième plage à comparer.

*last2*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la deuxième plage à comparer.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** lorsque la valeur est satisfaite et false lorsqu’elle n’est pas satisfaite.

### <a name="return-value"></a>Valeur de retour

**true** si la première plage est inférieure à la deuxième plage d’un point de vue lexicographique ; sinon **false**.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre séquences les compare élément par élément jusqu’à ce que :

- Elle trouve deux éléments correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les séquences.

- Aucune inégalité n’est trouvée, mais une séquence a plus d’éléments que l’autre et la séquence la plus courte est considérée comme inférieure à la séquence la plus longue.

- Aucune inégalité n’est trouvée et les séquences ont le même nombre d’éléments. par conséquent, les séquences sont égales et le résultat dela comparaison est false.

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
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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

## <a name="lower_bound"></a>lower_bound

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
    BinaryPredicate pred );
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*famille*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*value*\
Valeur dont la première position ou la première position possible est recherchée dans la plage ordonnée.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant situé à la position du premier élément d’une plage triée dont la valeur est supérieure ou égale à une valeur spécifiée, où l’équivalence est spécifiée par un prédicat binaire.

### <a name="remarks"></a>Notes

Le plage source triée référencée doit être valide ; tous les itérateurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Une plage triée est une condition préalable à l’utilisation de `lower_bound` et son ordre est identique à celui spécifié par un prédicat binaire.

La plage n’est pas modifiée par l’algorithme `lower_bound`.

Les types valeur des itérateurs vers l’avant doivent être comparables en termes d’infériorité pour être ordonnés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. De cette façon, les éléments non équivalents sont ordonnés

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire dans le cas contraire, avec le nombre d'`last - first`étapes proportionnelles à ().

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
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
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
        << "binary predicate mod_lesser is v3 = ( " ;
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

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a>make_heap

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
    BinaryPredicate pred );
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à convertir en tas.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à convertir en tas.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La complexité est linéaire, ce `3 * (last - first)` qui nécessite des comparaisons.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="max"></a>Max

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
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Premier des deux objets comparés.

*Oui*\
Second des deux objets comparés.

*prédit*\
Prédicat binaire utilisé pour comparer deux objets.

*liste*\
Liste d'initialiseurs qui contient les objets à comparer.

### <a name="return-value"></a>Valeur de retour

Le plus grand des deux objets, sauf si aucun n'est plus grand que l'autre ; dans ce cas, retourne le premier des deux objets. Dans le cas d'une initializer_list, retourne le plus grand des objets dans la liste.

### <a name="remarks"></a>Notes

L'algorithme `max` est inhabituel, dans la mesure où les objets sont passés comme paramètres. La plupart des algorithmes de la bibliothèque C++ Standard opèrent sur une plage d’éléments dont la position est spécifiée par des itérateurs passés comme paramètres. Si vous avez besoin d’une fonction qui opère sur une plage d’éléments, utilisez plutôt [max_element](../standard-library/algorithm-functions.md#max_element). Visual Studio 2017 active **constexpr** sur les surcharges qui prennent un initializer_list.

### <a name="example"></a>Exemples

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
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

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

## <a name="max_element"></a>max_element

Recherche la première occurrence du plus grand élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage dans laquelle rechercher l’élément le plus grand.

*famille*\
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage dans laquelle rechercher l’élément le plus grand.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat de comparaison accepte deux arguments et doit retourner la **valeur true** lorsque le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position de la première occurrence de l’élément le plus grand de la plage dans laquelle s’effectue la recherche.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire: `(last - first) - 1` les comparaisons sont nécessaires pour une plage non vide.

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
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

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

## <a name="merge"></a>fusion

Regroupe tous les éléments de deux plages sources triées au sein d’une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage.

*last1*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la première des deux plages sources triées à regrouper et trier au sein d’une même plage.

*First2*\
Itérateur d’entrée ciblant la position du premier élément de la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage.

*last2*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage.

*venir*\
Itérateur de sortie ciblant la position du premier élément de la plage de destination quand les deux plages sources doivent être regroupées au sein d’une même plage triée.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat de comparaison accepte deux arguments et doit retourner **true** lorsque le premier élément est inférieur au second, et false dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `merge` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l' `merge`algorithme.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination.

La complexité de l’algorithme est linéaire avec au `(last1 - first1) - (last2 - first2) - 1` maximum comparaisons.

La [classe list](../standard-library/list-class.md) fournit une fonction membre « merge » pour fusionner les éléments de deux listes.

### <a name="example"></a>Exemples

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a>min

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
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Premier des deux objets comparés.

*Oui*\
Second des deux objets comparés.

*prédit*\
Prédicat binaire utilisé pour comparer deux objets.

*liste*\
`initializer_list` Qui contient les membres à comparer.

### <a name="return-value"></a>Valeur de retour

Le plus petit des deux objets, sauf si aucun n’est plus petit que l’autre ; dans ce cas, retourne le premier des deux objets. Dans le cas d’un `initializer_list`, il retourne le moins des objets de la liste.

### <a name="remarks"></a>Notes

L'algorithme `min` est inhabituel, dans la mesure où les objets sont passés comme paramètres. La plupart des algorithmes de la bibliothèque C++ Standard opèrent sur une plage d’éléments dont la position est spécifiée par des itérateurs passés comme paramètres. Si vous avez besoin d’une fonction qui utilise une plage d’éléments, utilisez [min_element](../standard-library/algorithm-functions.md#min_element). [constexpr](../cpp/constexpr-cpp.md) a été activé sur `initializer_list` les surcharges dans Visual Studio 2017.

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
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

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

## <a name="min_element"></a>min_element

Recherche la première occurrence du plus petit élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage dans laquelle rechercher l’élément le plus petit.

*famille*\
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage dans laquelle rechercher l’élément le plus petit.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat de comparaison accepte deux arguments et doit retourner **true** lorsque le premier élément est inférieur au second, et false dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position de la première occurrence de l’élément le plus petit de la plage dans laquelle s’effectue la recherche.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire: `(last - first) - 1` les comparaisons sont nécessaires pour une plage non vide.

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
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

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

## <a name="minmax_element"></a>minmax_element

Exécute le travail effectué par `min_element` et `max_element` au sein d’un même appel.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant qui indique le début d’une plage.

*famille*\
Itérateur vers l’avant qui indique la fin d’une plage.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le sens dans lequel un élément est inférieur à un autre. Le prédicat de comparaison accepte deux arguments et doit retourner la **valeur true** lorsque le premier est inférieur au second, et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Returns (Retours)

`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`.

### <a name="remarks"></a>Notes

La première fonction de modèle retourne

`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`.

La deuxième fonction de modèle se comporte de la même façon, sauf qu’elle remplace `operator<(X, Y)` par `pred(X, Y)`.

Si la séquence n’est pas vide, la fonction effectue au mieux `3 * (last - first - 1) / 2` les comparaisons.

## <a name="minmax"></a>MinMax

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
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Premier des deux objets comparés.

*Oui*\
Second des deux objets comparés.

*prédit*\
Prédicat binaire utilisé pour comparer deux objets.

*liste*\
`initializer_list` Qui contient les membres à comparer.

### <a name="remarks"></a>Notes

La première fonction de modèle `pair<const Type&, const Type&>( right, left )` retourne si *Right* est inférieur à *Left*. Sinon, il retourne `pair<const Type&, const Type&>( left, right )`.

La deuxième fonction membre retourne une paire où le premier élément est le plus petit et le deuxième est le plus grand en cas de comparaison par le prédicat *prédit*.

Les fonctions de modèle restantes se comportent de la même façon, sauf qu’elles remplacent les paramètres de *gauche* et de *droite* par inList.

La fonction effectue exactement une comparaison.

## <a name="mismatch"></a>Concorde

Compare deux plages, élément par élément, et recherche la première position où il y a une différence.

Utilisez les surcharges à double portée dans le code C++14, car les surcharges qui ne prennent qu'un seul itérateur pour la deuxième plage ne détecteront pas les différences si la deuxième plage est plus longue que la première et provoqueront un comportement non défini si la deuxième plage est plus courte que la première.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d'entrée qui traite la position du premier élément de la première plage à tester.

*last1*\
Itérateur d'entrée qui traite la position qui suit le dernier élément de la première plage à tester.

*First2*\
Itérateur d'entrée qui traite la position du premier élément de la deuxième plage à tester.

*last2*\
Itérateur d'entrée qui traite la position qui suit le dernier élément de la deuxième plage à tester.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui compare les éléments actuels dans chaque plage et détermine s’ils sont équivalents. Retourne **true** si la condition est satisfaite et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Paire d'itérateurs qui traite les positions de l'incohérence dans les deux plages, le premier itérateur de composant à la position dans la première plage et le deuxième itérateur de composant à la position dans la deuxième plage. S’il n’existe aucune différence entre les éléments dans les plages comparées ou si le prédicat binaire dans la deuxième version est satisfait par toutes les paires d’éléments dans les deux plages, le premier itérateur de composant pointe vers la position située juste après le dernier élément dans la première plage et le deuxième itérateur de composant pointe vers la position juste après le dernier élément testé dans la seconde plage.

### <a name="remarks"></a>Notes

La première fonction avec modèle part du principe qu'il existe autant d'éléments dans la plage commençant à first2 que dans la plage désignée par [first1, last1). S’il y a plus d’éléments dans la deuxième plage, ils sont ignorés; s’il y en a moins, le comportement non défini se produit.

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
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="alg_move"></a>&lt;déplacementALG&gt;

Déplace les éléments associés à une plage spécifiée.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début de la plage d’éléments à déplacer.

*famille*\
Itérateur d’entrée qui indique la fin d’une plage d’éléments à déplacer.

*dest*\
Itérateur de sortie qui doit contenir les éléments déplacés.

### <a name="remarks"></a>Notes

La fonction `*(dest + N) = move(*(first + N))` de modèle évalue une fois pour chaque `N` dans `[0, last - first)`la plage, pour les valeurs `N` strictement croissantes de à partir de la valeur la plus faible. Elle retourne ensuite `dest + N`. Si `dest` et désignent d' *abord* les régions de stockage, la *destination* ne `[first, last)`doit pas être comprise dans la plage.

## <a name="move_backward"></a>move_backward

Déplace les éléments d'un itérateur vers un autre. Le déplacement commence par le dernier élément d'une plage spécifiée, et se termine par le premier élément de cette plage.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur qui indique le début d’une plage à partir de laquelle déplacer des éléments.

*famille*\
Itérateur qui indique la fin d’une plage à partir de laquelle déplacer des éléments. Cet élément n’est pas déplacé.

*destEnd*\
Itérateur bidirectionnel se rapportant à la position située immédiatement après l'élément final dans la plage de destination.

### <a name="remarks"></a>Notes

La fonction `*(destEnd - N - 1) = move(*(last - N - 1))` de modèle évalue une fois pour chaque `N` dans `[0, last - first)`la plage, pour les valeurs `N` strictement croissantes de à partir de la valeur la plus faible. Elle retourne ensuite `destEnd - (last - first)`. Si *destEnd* et désignent d' *abord* les régions de stockage, *destEnd* ne doit `[first, last)`pas figurer dans la plage.

`move` et `move_backward` reviennent fonctionnellement à utiliser `copy` et `copy_backward` avec un itérateur move.

## <a name="next_permutation"></a>next_permutation

Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur bidirectionnel ciblant la position du premier élément de la plage à permuter.

*famille*\
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à permuter.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si la permutation lexicographique suivante existe et a remplacé l’ordre d’origine de la plage ; sinon **false**, auquel cas l’ordre est transformé selon la plus petite permutation lexicographique.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Le prédicat binaire par défaut est inférieur à et les éléments de la plage doivent être moins comparables pour garantir que la permutation suivante est bien définie.

La complexité est linéaire avec au maximum `(last - first) / 2` permutations.

### <a name="example"></a>Exemples

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
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
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
    vector<int> v1;
    vector<int>::iterator Iter1;

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
            cout << *Iter1 << " ";
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

## <a name="nth_element"></a>nth_element

Partitionne une plage d’éléments, en recherchant le *n*-ième élément de la séquence dans la plage, de sorte que tous les éléments qui le précèdent sont inférieurs ou égaux, et que tous les éléments qui le suivent sont supérieurs ou égaux.

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à partitionner.

*énième*\
Itérateur d’accès aléatoire ciblant la position de l’élément à ordonner correctement sur la limite de la partition.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à partitionner.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** lorsque la valeur est satisfaite et false lorsqu’elle n’est pas satisfaite.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L' `nth_element` algorithme ne garantit pas que les éléments des sous-plages de part et d’autre du *n*ième élément sont triés. Il apporte donc encore moins de garanties que `partial_sort`, qui ordonne les éléments de la plage en dessous d’un élément choisi, et peut être utilisé comme alternative plus rapide à `partial_sort` quand l’ordre de la plage inférieure n’est pas nécessaire.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre.

La moyenne d’une complexité de tri est linéaire par rapport à *Last-First*.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="none_of"></a>none_of

Retourne la **valeur true** lorsqu’une condition n’est jamais présente parmi les éléments de la plage donnée.

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début de la recherche d’une condition dans une plage d’éléments.

*famille*\
Itérateur d’entrée qui indique la fin d’une plage d’éléments.

*prédit*\
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** si la condition n’est pas détectée au moins une fois dans la plage indiquée, et false si la condition est détectée.

### <a name="remarks"></a>Notes

La fonction de modèle retourne **true** uniquement si, pour `N` certains de la `[0, last - first)`plage, le prédicat `pred(*(first + N))` est toujours **false**.

## <a name="partial_sort"></a>partial_sort

Réorganise un nombre spécifié d’éléments plus petits au sein d’une plage, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*sortEnd*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la sous-plage à trier.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier partiellement.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre. L' `sort` algorithme n’est pas stable et ne garantit pas que l’ordre relatif des éléments équivalents sera préservé. L’algorithme `stable_sort` conserve cet ordre d’origine.

La complexité moyenne du tri partiel *est O*(`last`(- - `first`) log`sortEnd`(`first`)).

### <a name="example"></a>Exemples

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
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

## <a name="partial_sort_copy"></a>partial_sort_copy

Copie les éléments d’une plage source dans une plage de destination. Les éléments sources sont triés par ordre croissant ou selon un autre prédicat binaire spécifié.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément dans la plage source.

*last1*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la plage source.

*First2*\
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage de destination triée.

*last2*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage de destination triée.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur d’accès aléatoire ciblant l’élément de la plage de destination situé une position après le dernier élément inséré à partir de la plage source.

### <a name="remarks"></a>Notes

Les plages source et de destination ne doivent pas se chevaucher et doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Le prédicat binaire doit fournir un ordre faible strict pour que les éléments qui ne sont pas équivalents soient ordonnés, mais que ceux qui sont équivalents ne le soient pas. Deux éléments sont équivalents sous le prédicat Inférieur à, mais pas nécessairement égaux si aucun n’est inférieur à l’autre.

### <a name="example"></a>Exemples

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

## <a name="partition"></a>non

Répartit les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur bidirectionnel ciblant la position du premier élément de la plage à partitionner.

*famille*\
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à partitionner.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire si un élément doit être classé. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel ciblant la position du premier élément de la plage qui ne satisfait pas la condition du prédicat.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments *a* et *b* sont équivalents, mais pas nécessairement égaux `pred( a, b )` , si a la valeur false et `pred( b, a )` a la valeur false, où prédit est le prédicat spécifié par le paramètre. L' `partition` algorithme n’est pas stable et ne garantit pas que l’ordre relatif des éléments équivalents sera préservé. L’algorithme `stable_partition` conserve cet ordre d’origine.

La complexité est linéaire: il existe `(last - first)` des applications qui sont prédites `(last - first)/2` et au maximum.

### <a name="example"></a>Exemple

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="partition_copy"></a>partition_copy

Copie les éléments pour lesquels une condition a la **valeur true** pour une destination, et pour laquelle la condition est false à une autre. Les éléments doivent provenir d'une plage spécifiée.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée qui indique le début d’une plage dans laquelle rechercher une condition.

*famille*\
Itérateur d’entrée qui indique la fin d’une plage.

*dest1*\
Itérateur de sortie utilisé pour copier des éléments qui retournent la valeur true pour une condition testée à l’aide de *prédit*.

*dest2*\
Itérateur de sortie utilisé pour copier des éléments qui retournent la valeur false pour une condition testée à l’aide de *prédit*.

*prédit*\
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à vérifier. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="remarks"></a>Notes

La fonction de modèle copie chaque `X` élément `[first,last)` `*dest1++` dans dans `pred(X)` si a la valeur true `*dest2++` , ou la valeur à dans le cas contraire. Il retourne `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.

## <a name="partition_point"></a>partition_point

Retourne le premier élément d'une plage donnée qui ne répond pas à une condition. Les éléments sont triés de sorte que ceux qui répondent à la condition précèdent ceux qui n'y répondent pas.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
`ForwardIterator` qui indique le début d’une plage dans laquelle rechercher une condition.

*famille*\
`ForwardIterator` qui indique la fin d’une plage.

*prédit*\
Condition à vérifier. Cette condition est fournie par un objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire par l’élément recherché. Un prédicat unaire accepte un seul argument et retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Retourne un `ForwardIterator` qui fait référence au premier élément qui ne respecte pas la condition testée par *prédit*, ou retourne le *dernier* si aucun n’est trouvé.

### <a name="remarks"></a>Notes

La fonction de modèle recherche le premier `it` itérateur `[first, last)` dans pour `pred(*it)` lequel a la **valeur false**. La séquence doit être classée par *prédit*.

## <a name="pop_heap"></a>pop_heap

Retire le plus grand élément du début du tas et le place à l'avant-dernière position de la plage, puis forme un nouveau tas à partir des éléments restants.

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément du tas.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément du tas.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

L’algorithme `pop_heap` est l’inverse de l’opération effectuée par l’algorithme push_heap, dans lequel un élément à l’avant-dernière position d’une plage est ajouté à un tas constitué des éléments précédents de la plage, au cas où l’élément ajouté au tas est supérieur à tous les éléments déjà présents dans le tas.

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La plage qui exclut l’élément qui vient d’être ajouté à la fin doit être un tas.

La complexité est logarithmique et nécessite au maximum `log (last - first)` les comparaisons.

### <a name="example"></a>Exemples

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="prev_permutation"></a>prev_permutation

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
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur bidirectionnel ciblant la position du premier élément de la plage à permuter.

*famille*\
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à permuter.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

**true** si le vue lexicographique de permutation précédent existe et a remplacé le classement d’origine de la plage; sinon, false, auquel cas le classement est transformé en permutation vue lexicographique la plus grande.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Le prédicat binaire par défaut est inférieur à et les éléments de la plage doivent être comparables pour garantir que la permutation précédente est bien définie.

La complexité est linéaire, avec au maximum (`last` - `first`)/2 swaps.

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

int main()
{
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
    vector<int> v1;
    vector<int>::iterator Iter1;

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
            cout << *Iter1 << " ";
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

## <a name="push_heap"></a>push_heap

Ajoute un élément qui se trouve à la fin d'une plage à un tas existant, constitué des éléments précédents de la plage.

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément du tas.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à convertir en tas.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

L’élément doit d’abord être déplacé à la fin d’un tas existant, puis l’algorithme est utilisé pour ajouter cet élément au tas existant.

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La plage qui exclut l’élément qui vient d’être ajouté à la fin doit être un tas.

La complexité est logarithmique et nécessite au maximum `log(last - first)` les comparaisons.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="random_shuffle"></a>random_shuffle

La fonction std:: random_shuffle () est déconseillée et remplacée par [std:: de lecture aléatoire](../standard-library/algorithm-functions.md#shuffle). Pour obtenir un exemple de code et plus d’informations, consultez [ \<> aléatoire](../standard-library/random.md) et le Stack Overflow publication [pourquoi les méthodes std:: random_shuffle sont-elles dépréciées dans c++ 14?](https://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a>Installez

Élimine une valeur spécifiée d'une plage donnée sans modifier l'ordre des éléments restants, et retourne la fin d'une nouvelle plage exempte de la valeur spécifiée.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur de transfert se rapportant à la position du premier élément dans la plage de laquelle les éléments sont supprimés.

*famille*\
Itérateur de transfert se rapportant à la position située immédiatement après l'élément final dans la plage de laquelle les éléments sont supprimés.

*value*\
Valeur qui doit être supprimée de la plage.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert se rapportant à la nouvelle position de fin de la plage modifiée, située immédiatement après l'élément final de la séquence restante exempte de la valeur spécifiée.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire; Il existe (`last` - )descomparaisonsd’égalité`first`.

La [classe List](../standard-library/list-class.md) a une version de fonction membre plus efficace `remove`de, qui relient également les pointeurs.

### <a name="example"></a>Exemples

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_copy"></a>remove_copy

Copie les éléments d'une plage source vers une plage de destination. Les éléments ayant une valeur spécifiée ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée ciblant la position du premier élément dans la plage de laquelle les éléments sont supprimés.

*famille*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la plage de laquelle les éléments sont supprimés.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans laquelle les éléments sont supprimés.

*value*\
Valeur qui doit être supprimée de la plage.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert ciblant la nouvelle position de fin de la plage de destination, de suite après le dernier élément de la copie de la séquence restante exempte de la valeur spécifiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La plage de destination doit avoir suffisamment d’espace pour accueillir les éléments restants qui seront copiés après la suppression de la valeur spécifiée.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire; Il existe (`last` - `first` - ) des comparaisons d’égalité et au maximum`last`() assignations.`first`

### <a name="example"></a>Exemple

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_copy_if"></a>remove_copy_if

Copie les éléments d’une plage source vers une plage de destination, à l’exception des éléments qui répondent à un prédicat. Les éléments sont copiés sans perturber l’ordre des éléments restants. Retourne la fin d’une nouvelle plage de destination.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée ciblant la position du premier élément dans la plage de laquelle les éléments sont supprimés.

*famille*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément de la plage de laquelle les éléments sont supprimés.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans laquelle les éléments sont supprimés.

*prédit*\
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert ciblant la nouvelle position de fin de la plage de destination, de suite après le dernier élément de la séquence restante exempte des éléments satisfaisant le prédicat.

### <a name="remarks"></a>Notes

La plage source référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La plage de destination doit avoir suffisamment d’espace pour accueillir les éléments restants qui seront copiés après la suppression de la valeur spécifiée.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire: il y a`last`( -  - `first`) des comparaisons d’égalité et au`last`maximum (`first`) affectations.

Pour plus d’informations sur le comportement de ces fonctions, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemples

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_if"></a>remove_if

Élimine d’une plage donnée les éléments qui répondent à un prédicat, sans modifier l’ordre des éléments restants et en retournant la fin d’une nouvelle plage exempte de la valeur spécifiée.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant pointant sur la position du premier élément de la plage dont les éléments sont supprimés.

*famille*\
Itérateur vers l’avant pointant sur la position juste après le dernier élément de la plage dont les éléments sont supprimés.

*prédit*\
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

### <a name="return-value"></a>Valeur de retour

Itérateur de transfert se rapportant à la nouvelle position de fin de la plage modifiée, située immédiatement après l'élément final de la séquence restante exempte de la valeur spécifiée.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L'ordre des éléments non supprimés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire: il y a`last`( - `first`) comparaisons d’égalité.

La classe list a une version de fonction membre remove plus efficace qui rétablit les liens des pointeurs.

### <a name="example"></a>Exemple

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="replace"></a>lieu

Examine tous les éléments d'une plage et les remplace s'ils correspondent à une valeur spécifiée.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant pointant sur la position du premier élément de la plage dont les éléments sont remplacés.

*famille*\
Itérateur vers l’avant pointant sur la position juste après le dernier élément de la plage dont les éléments sont remplacés.

*oldVal*\
Ancienne valeur des éléments remplacés.

*newVal*\
Nouvelle valeur assignée aux éléments ayant l’ancienne valeur.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L’ordre des éléments non remplacés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire; Il existe (`last` - `first` - ) des comparaisons d’égalité et au maximum`last`() des affectations de nouvelles valeurs.`first`

### <a name="example"></a>Exemple

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="replace_copy"></a>replace_copy

Examine tous les éléments d'une plage source et les remplace s'ils correspondent à une valeur spécifiée, tout en copiant le résultat dans une nouvelle plage de destination.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée pointant vers la position du premier élément de la plage dont les éléments sont remplacés.

*famille*\
Itérateur d’entrée pointant vers la position située de suite après le dernier élément de la plage dont les éléments sont remplacés.

*venir*\
Itérateur de sortie pointant vers le premier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

*oldVal*\
Ancienne valeur des éléments remplacés.

*newVal*\
Nouvelle valeur assignée aux éléments ayant l’ancienne valeur.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie pointant vers la position située de suite après le dernier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées ne doivent pas se chevaucher et doivent toutes deux être valides : tous les pointeurs doivent pouvoir être déréférencés et, dans les séquences, la dernière position est accessible à partir de la première par incrémentation.

L’ordre des éléments non remplacés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire: il existe (`last` - `last` - `first`) des comparaisons d’égalité et au maximum (`first`) des affectations de nouvelles valeurs.

### <a name="example"></a>Exemple

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

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

## <a name="replace_copy_if"></a>replace_copy_if

Examine tous les éléments d'une plage source et les remplace s'ils répondent à un prédicat, tout en copiant le résultat dans une nouvelle plage de destination.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’entrée pointant vers la position du premier élément de la plage dont les éléments sont remplacés.

*famille*\
Itérateur d’entrée pointant vers la position située de suite après le dernier élément de la plage dont les éléments sont remplacés.

*venir*\
Itérateur de sortie pointant vers la position du premier élément de la plage de destination dans laquelle les éléments sont copiés.

*prédit*\
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

*value*\
Nouvelle valeur assignée aux éléments dont l’ancienne valeur satisfait au prédicat.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie pointant vers la position située de suite après le dernier élément de la plage de destination dans laquelle la séquence d’éléments modifiée est copiée.

### <a name="remarks"></a>Notes

Les plages source et de destination référencées ne doivent pas se chevaucher et doivent toutes deux être valides : tous les pointeurs doivent pouvoir être déréférencés et, dans les séquences, la dernière position est accessible à partir de la première par incrémentation.

L’ordre des éléments non remplacés reste stable.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire; Il existe (`last` - `first` - ) des comparaisons d’égalité et au maximum`last`() des affectations de nouvelles valeurs.`first`

### <a name="example"></a>Exemple

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

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

## <a name="replace_if"></a>replace_if

Examine tous les éléments d’une plage et les remplace s’ils répondent à un prédicat spécifié.

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant pointant sur la position du premier élément de la plage dont les éléments sont remplacés.

*famille*\
Itérateur pointant sur la position juste après le dernier élément de la plage dont les éléments sont remplacés.

*prédit*\
Prédicat unaire qui doit être satisfait si la valeur d’un élément doit être remplacée.

*value*\
Nouvelle valeur assignée aux éléments dont l’ancienne valeur satisfait au prédicat.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

L’ordre des éléments non remplacés reste stable.

L’algorithme `replace_if` est une généralisation de `replace`l’algorithme, qui permet de spécifier n’importe quel prédicat, plutôt que d’agir sur une valeur de constante spécifiée.

L' `operator==` utilisé pour déterminer l'égalité entre des éléments doit imposer une relation d'équivalence entre ses opérandes.

La complexité est linéaire: il existe (`last` - `last` - `first`) des comparaisons d’égalité et au maximum (`first`) des affectations de nouvelles valeurs.

### <a name="example"></a>Exemple

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="reverse"></a>TVA

Inverse l'ordre des éléments d'une plage.

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur bidirectionnel pointant sur la position du premier élément de la plage dont les éléments sont permutés.

*famille*\
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

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="reverse_copy"></a>reverse_copy

Inverse l'ordre des éléments d'une plage source, tout en les copiant dans une plage de destination.

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur bidirectionnel pointant vers la position du premier élément de la plage source dont les éléments sont permutés.

*famille*\
Itérateur bidirectionnel pointant vers la position située de suite après le dernier élément de la plage source dont les éléments sont permutés.

*venir*\
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

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

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

## <a name="rotate"></a>MUTE

Échange les éléments de deux plages adjacentes.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage à faire pivoter.

*intergiciel*\
Itérateur vers l’avant définissant la limite au sein de la plage qui cible la position du premier élément dans la deuxième partie de la plage dont les éléments doivent être échangés avec ceux de la première partie de la plage.

*famille*\
Itérateur vers l’avant ciblant la position située de suite après le dernier élément de la plage à faire pivoter.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire avec au maximum (`last` - `first`) des permutations.

### <a name="example"></a>Exemples

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
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
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
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

## <a name="rotate_copy"></a>rotate_copy

Échange les éléments de deux plages adjacentes au sein d'une plage source et copie le résultat dans une plage de destination.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage à faire pivoter.

*intergiciel*\
Itérateur vers l’avant définissant la limite au sein de la plage qui cible la position du premier élément dans la deuxième partie de la plage dont les éléments doivent être échangés avec ceux de la première partie de la plage.

*famille*\
Itérateur vers l’avant ciblant la position située de suite après le dernier élément de la plage à faire pivoter.

*venir*\
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible à partir de la première par incrémentation.

La complexité est linéaire avec au maximum (`last` - `first`) des permutations.

### <a name="example"></a>Exemples

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a>exemple

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a>recherche

Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*First2*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la correspondance.

*last2*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la correspondance.

*prédit*\
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

*recherche*\
Recherche qui encapsule le modèle à rechercher et l’algorithme de recherche à utiliser.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

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

## <a name="search_n"></a>search_n

Recherche la première sous-séquence d’une plage dont un nombre spécifié d’éléments ont une valeur particulière ou une relation à cette valeur, selon un prédicat binaire spécifié.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle s'effectue la recherche.

*last1*\
Itérateur vers l'avant ciblant la position juste après le dernier élément de la plage dans laquelle s'effectue la recherche.

*saut*\
Taille de la sous-séquence recherchée.

*value*\
Valeur des éléments de la séquence recherchée.

*prédit*\
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la position du premier élément de la première sous-séquence qui correspond à la séquence spécifiée ou qui est équivalente au sens spécifié par un prédicat binaire.

### <a name="remarks"></a>Notes

`operator==`, qui sert à déterminer la correspondance entre un élément et la valeur spécifiée, doit imposer une relation d'équivalence entre ses opérandes.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La complexité est linéaire par rapport à la taille de la plage de recherche.

### <a name="example"></a>Exemples

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
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

## <a name="set_difference"></a>set_difference

Regroupe tous les éléments qui appartiennent à une plage source triée, mais pas à une autre plage source triée, en une même plage de destination triée. Un critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*last1*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*First2*\
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*last2*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence des deux plages sources.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans la mesure où les deux plages sources doivent être regroupées au sein d’une même plage triée représentant la différence des deux plages sources.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant la différence des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la première plage source.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `set_difference` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme merge.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double (de telle sorte qu’il y a plus d’éléments dans la première plage source que dans la seconde), la plage de destination contient le nombre d’occurrences supplémentaires de ces éléments que contient la première plage source par rapport à la deuxième.

La complexité de l’algorithme est linéaire avec au `2 * ((last1 - first1) - (last2 - first2)) - 1` maximum les comparaisons pour les plages sources non vides.

### <a name="example"></a>Exemples

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a>set_intersection

Regroupe tous les éléments de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*last1*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*First2*\
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*last2*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’intersection des deux plages sources.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans la mesure où les deux plages sources doivent être regroupées au sein d’une même plage triée représentant l’intersection des deux plages sources.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant l’intersection des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme merge selon le même ordre que celui utilisé par l’algorithme chargé de trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double, la plage de destination contient le nombre maximal de ces éléments qui figurent dans les deux plages sources.

La complexité de l’algorithme est linéaire avec au `2 * ((last1 - first1) + (last2 - first2)) - 1` maximum les comparaisons pour les plages sources non vides.

### <a name="example"></a>Exemple

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>set_symmetric_difference

Regroupe tous les éléments qui appartiennent à l'une de deux plages sources triées (mais pas aux deux) au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*last1*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*First2*\
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*last2*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant la différence symétrique des deux plages sources.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans la mesure où les deux plages sources doivent être regroupées au sein d’une même plage triée représentant la différence symétrique des deux plages sources.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant la différence symétrique des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `merge*` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l’algorithme merge.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double, la plage de destination contient la valeur absolue du nombre d’occurrences supplémentaires de ces éléments que contient l’une des plages sources par rapport à la deuxième.

La complexité de l’algorithme est linéaire avec au `2 * ((last1 - first1) - (last2 - first2)) - 1` maximum les comparaisons pour les plages sources non vides.

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a>set_union

Regroupe tous les éléments qui appartiennent au moins à l'une de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*last1*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la première des deux plages sources triées à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*First2*\
Itérateur d’entrée ciblant la position du premier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*last2*\
Itérateur d’entrée ciblant la position située de suite après le dernier élément dans la deuxième des deux plages sources triées consécutives à regrouper et trier au sein d’une même plage représentant l’union des deux plages sources.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination dans la mesure où les deux plages sources doivent être regroupées au sein d’une même plage triée représentant l’union des deux plages sources.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Le prédicat binaire accepte deux arguments et doit retourner **true** quand le premier élément est inférieur au deuxième et **false** dans le cas contraire.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément de la plage de destination triée représentant l’union des deux plages sources.

### <a name="remarks"></a>Notes

Les plages sources triées référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation.

La plage de destination ne doit pas chevaucher les plages sources et doit être suffisamment grande pour contenir la plage de destination.

Les plages sources triées doivent chacune être structurées comme condition préalable à l’application de l’algorithme `merge` selon le même ordre que celui utilisé par l’algorithme pour trier les plages regroupées.

L’opération est stable, car l’ordre relatif des éléments dans chaque plage est préservé dans la plage de destination. Les plages sources ne sont pas modifiées par l' `merge`algorithme.

Les types de valeur des itérateurs d’entrée doivent être comparables en termes d’infériorité pour être classés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. Quand il existe des éléments équivalents dans les deux plages sources, les éléments de la première plage précèdent ceux de la deuxième dans la plage de destination. Si les plages sources contiennent des éléments en double, la plage de destination contient le nombre maximal de ces éléments qui figurent dans les deux plages sources.

La complexité de l’algorithme est linéaire avec au `2 * ((last1 - first1) - (last2 - first2)) - 1` maximum comparaisons.

### <a name="example"></a>Exemples

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a>lecture aléatoire

Lit de façon aléatoire (réorganise) les éléments pour une plage donnée à l'aide d'un générateur de nombres aléatoires.

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur sur le premier élément de la plage à lire de façon aléatoire, compris. Doit remplir les conditions de `RandomAccessIterator` et `ValueSwappable`.

*famille*\
Itérateur sur le dernier élément de la plage à lire de façon aléatoire, non compris. Doit remplir les conditions de `RandomAccessIterator` et `ValueSwappable`.

*général*\
Générateur de nombres aléatoires que la fonction `shuffle()` utilisera pour l'opération. Doit remplir les conditions d'un `UniformRandomNumberGenerator`.

### <a name="remarks"></a>Notes

Pour plus d’informations et pour obtenir un exemple de code qui utilise `shuffle()`, consultez [\<random>](../standard-library/random.md).

## <a name="sort"></a>Tris

Réorganise les éléments d’une plage spécifiée, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Ce prédicat binaire accepte deux arguments et retourne **true** si les deux arguments sont dans l’ordre et **false** dans le cas contraire. Cette fonction de comparaison doit imposer un ordre faible strict sur les paires d’éléments de la séquence. Pour plus d’informations, consultez [Algorithmes](../standard-library/algorithms.md).

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre. L’algorithme `sort` n’est pas stable et ne garantit pas que l’ordre relatif des éléments équivalents est conservé. L’algorithme `stable_sort` conserve cet ordre d’origine.

La moyenne d’une complexité de tri `O( N log N )`est, où *N* = pour la*dernière* - *fois*.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="sort_heap"></a>sort_heap

Convertit un tas en une plage triée.

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’accès aléatoire ciblant la position du premier élément du tas cible.

*famille*\
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément du tas cible.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la logique selon laquelle un élément est inférieur à un autre. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** lorsque la valeur est satisfaite et false lorsqu’elle n’est pas satisfaite.

### <a name="remarks"></a>Notes

Les tas ont deux propriétés :

- Le premier élément est toujours le plus grand.

- Des éléments peuvent être ajoutés ou supprimés en temps logarithmique.

Après l’application de cet algorithme, la plage à laquelle il a été appliqué n’est plus un tas.

Il ne s’agit pas d’un tri stable, car l’ordre relatif des éléments équivalents n’est pas nécessairement conservé.

Les tas sont un moyen idéal d’implémenter des files d’attente prioritaires et sont utilisés dans l’implémentation de la [classe priority_queue](../standard-library/priority-queue-class.md) de l’adaptateur de conteneur de bibliothèque C++ Standard.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

La complexité est au maximum `N log N`, où *N* = au plus le*dernier* -  *.*

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

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
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

## <a name="stable_partition"></a>stable_partition

Classe les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas, et l’ordre relatif des éléments équivalents doit être conservé.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur bidirectionnel ciblant la position du premier élément de la plage à partitionner.

*famille*\
Itérateur bidirectionnel ciblant la position juste après le dernier élément de la plage à partitionner.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit la condition à satisfaire si un élément doit être classé. Un prédicat unaire accepte un seul argument et retourne **true** s’il est satisfait ou false s’il n’est pas respecté.

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel ciblant la position du premier élément de la plage qui ne satisfait pas la condition du prédicat.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments *a* et *b* sont équivalents, mais pas nécessairement égaux `pred( a, b )` , si a la valeur false et `pred( b, a )` a la valeur false, où prédit est le prédicat spécifié par le paramètre. L' `stable_partition` algorithme est stable et garantit que l’ordre relatif des éléments équivalents sera préservé. L’algorithme `partition` ne préserve pas nécessairement ce classement d’origine.

### <a name="example"></a>Exemples

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

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

## <a name="stable_sort"></a>stable_sort

Classe les éléments d’une plage spécifiée dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire, et conserve l’ordre relatif des éléments équivalents.

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur bidirectionnel ciblant la position du premier élément de la plage à trier.

*famille*\
Itérateur bidirectionnel ciblant la position située juste après le dernier élément de la plage à trier.

*prédit*\
Objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans l’ordre. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="remarks"></a>Notes

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation.

Les éléments sont équivalents, mais pas nécessairement égaux si aucun n’est inférieur à l’autre. L' `sort` algorithme est stable et garantit que l’ordre relatif des éléments équivalents sera préservé.

La complexité au moment de l' `stable_sort` exécution de dépend de la quantité de mémoire disponible, mais le meilleur cas (avec une mémoire `O(N log N)` suffisante) est et, `O(N (log N)^2)`dans le pire des cas, c’est, où *N* = *dernier*  -   *tout d’abord*. En règle générale `sort` , l’algorithme est `stable_sort`beaucoup plus rapide que.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
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

## <a name="swap"></a>échange

Le premier remplacement échange les valeurs de deux objets. Le deuxième remplacement échange les valeurs de deux tableaux d’objets.

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Pour le premier remplacement, premier objet dont le contenu est échangé. Pour le deuxième remplacement, premier tableau d’objets dont le contenu est échangé.

*Oui*\
Pour le premier remplacement, deuxième objet dont le contenu est échangé. Pour le deuxième remplacement, deuxième tableau d’objets dont le contenu est échangé.

### <a name="remarks"></a>Notes

La première surcharge est conçue pour traiter des objets individuels. La deuxième surcharge échange le contenu des objets entre deux tableaux.

### <a name="example"></a>Exemples

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

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

## <a name="swap_ranges"></a>swap_ranges

Échange les éléments d'une plage avec ceux d'une autre plage de taille égale.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur vers l’avant pointant sur la première position de la première plage dont les éléments doivent être échangés.

*last1*\
Itérateur vers l’avant pointant juste après la dernière position de la première plage dont les éléments doivent être échangés.

*First2*\
Itérateur vers l’avant pointant sur la première position de la deuxième plage dont les éléments doivent être échangés.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant pointant juste après la dernière position de la deuxième plage dont les éléments doivent être échangés.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position est accessible à partir de la première par incrémentation. La deuxième plage doit être aussi grande que la première.

La complexité est linéaire avec les échanges *last1* - *First1* effectués. Si les éléments des conteneurs du même type sont échangés, la fonction membre `swap` de ce conteneur doit être utilisée, car la fonction membre a généralement une complexité constante.

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
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
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
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
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

## <a name="transform"></a>Modifiez

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

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*First1*\
Itérateur d’entrée ciblant la position du premier élément de la première plage source à traiter.

*last1*\
Itérateur d’entrée ciblant la position juste après le dernier élément de la première plage source à traiter.

*First2*\
Itérateur d'entrée qui traite la position du premier élément de la seconde plage source à traiter.

*venir*\
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

*Func*\
Objet de fonction unaire défini par l’utilisateur utilisé dans la première version de l’algorithme appliqué à chaque élément de la première plage source, ou objet de fonction binaire défini par l’utilisateur utilisé dans la deuxième version de l’algorithme appliqué par paire, dans un ordre vers l’avant, aux deux plages sources.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située immédiatement après le dernier élément de la plage de destination qui reçoit les éléments de sortie transformés par l'objet de fonction.

### <a name="remarks"></a>Notes

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans chaque séquence, la dernière position doit être accessible à partir de la première par incrémentation. La plage de destination doit être suffisamment grande pour contenir la plage source transformée.

Si le *résultat* est égal à *First1* dans la première version de l’algorithme, les plages source et de destination seront identiques et la séquence sera modifiée sur place. Toutefois, le *résultat* peut ne pas traiter une position dans la`first1` plage [+ `last1`1,).

La complexité est linéaire avec au maximum (`last1` - `first1`) comparaisons.

### <a name="example"></a>Exemples

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
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
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
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>unique

Supprime les éléments en double adjacents dans une plage spécifiée.

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l'avant ciblant la position du premier élément de la plage dans laquelle rechercher des doublons à supprimer.

*famille*\
Itérateur vers l’avant ciblant la position juste après le dernier élément de la plage dans laquelle rechercher des doublons à supprimer.

*prédit*\
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant à la fin de la séquence modifiée qui ne contient aucun doublon consécutif, ciblant la position juste après le dernier élément non supprimé.

### <a name="remarks"></a>Notes

Les deux formes de l’algorithme suppriment le deuxième doublon d’une paire consécutive d’éléments égaux.

Le fonctionnement de l’algorithme est stable pour ne pas modifier l’ordre relatif des éléments rétablis.

La plage référencée doit être valide ; tous les pointeurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position est accessible depuis la première au moyen d'une incrémentation. le nombre d’éléments dans la séquence n’est pas modifié par l' `unique` algorithme et les éléments au-delà de la fin de la séquence modifiée sont déréférencés, mais ne sont pas spécifiés.

La complexité est linéaire, ce `(last - first) - 1` qui nécessite des comparaisons.

La classe list fournit une fonction membre « unique » plus efficace qui peut donner de meilleurs résultats.

Ces algorithmes ne peuvent pas être utilisés sur un conteneur associatif.

### <a name="example"></a>Exemples

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
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
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

## <a name="unique_copy"></a>unique_copy

Copie les éléments d'une plage source dans une plage de destination, à l'exception des éléments en double adjacents.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Paramètres

*exécutable*\
Stratégie d’exécution à utiliser.

*premier*\
Itérateur vers l’avant ciblant la position du premier élément de la plage source à copier.

*famille*\
Itérateur vers l’avant ciblant la position située de suite après le dernier élément de la plage source à copier.

*venir*\
Itérateur de sortie ciblant la position du premier élément dans la plage de destination recevant la copie avec suppression des doublons consécutifs.

*prédit*\
Objet de fonction de prédicat défini par l'utilisateur qui définit la condition à satisfaire si deux éléments sont à considérer comme équivalents. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie ciblant la position située de suite après le dernier élément dans la plage de destination recevant la copie avec suppression des doublons consécutifs.

### <a name="remarks"></a>Notes

Les deux formes de l’algorithme suppriment le deuxième doublon d’une paire consécutive d’éléments égaux.

Le fonctionnement de l’algorithme est stable pour ne pas modifier l’ordre relatif des éléments rétablis.

Les plages référencées doivent être valides ; tous les pointeurs doivent pouvoir être déréférencés et, dans une séquence, la dernière position est accessible depuis la première au moyen d’une incrémentation.

La complexité est linéaire, ce qui`last`nécessite des comparaisons ( - `first`).

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
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
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

## <a name="upper_bound"></a>upper_bound

Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Paramètres

*premier*\
Position du premier élément de la plage dans laquelle effectuer la recherche.

*famille*\
Position juste après le dernier élément de la plage dans laquelle effectuer la recherche.

*value*\
Valeur dans la plage ordonnée qui doit être dépassée par la valeur de l’élément ciblé par l’itérateur retourné.

*prédit*\
Objet de fonction de prédicat de comparaison défini par l’utilisateur qui définit le sens dans lequel un élément est inférieur à un autre. Un prédicat de comparaison prend deux arguments et retourne la **valeur true** lorsque la valeur est satisfaite et false lorsqu’elle n’est pas satisfaite.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant ciblant la position du premier élément ayant une valeur supérieure à une valeur spécifiée.

### <a name="remarks"></a>Notes

Le plage source triée référencée doit être valide ; tous les itérateurs doivent pouvoir être déréférencés et, dans la séquence, la dernière position doit être accessible à partir de la première par incrémentation.

Une plage triée est une condition préalable à l' `upper_bound` utilisation de et où le critère de tri est le même que celui spécifié par le prédicat de comparaison.

La plage n’est pas modifiée par l’algorithme `upper_bound`.

Les types valeur des itérateurs vers l’avant doivent être comparables en termes d’infériorité pour être ordonnés. Ainsi, pour deux éléments donnés, il est possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. De cette façon, les éléments non équivalents sont ordonnés

La complexité de l’algorithme est logarithmique pour les itérateurs d’accès aléatoire et linéaire dans le cas contraire, avec le nombre d'`last - first`étapes proportionnelles à ().

### <a name="example"></a>Exemples

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
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
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
        << "binary predicate mod_lesser is v3 = ( " ;
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

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```
