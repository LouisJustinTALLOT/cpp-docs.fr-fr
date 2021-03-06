---
title: set, classe
description: Référence d’API pour la classe de conteneur de la bibliothèque standard C++ `set` , qui est utilisée pour stocker et récupérer des données d’une collection.
ms.date: 9/9/2020
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::contains
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], contains
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: 2898c06d998653a25ce771c80086ef8aef27a60b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509937"
---
# <a name="set-class"></a>set, classe

La classe de conteneur de la bibliothèque standard C++ `set` est utilisée pour stocker et récupérer des données d’une collection. Les valeurs des éléments dans le `set` sont uniques et servent de valeurs de clés en fonction desquelles les données sont automatiquement triées. La valeur d’un élément dans un `set` ne peut pas être modifiée directement. Vous devez supprimer les anciennes valeurs et insérer les éléments ayant de nouvelles valeurs.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Paramètres

*Essentiel*\
Type de données d'élément à stocker dans la classe set.

*Caractéristiques*\
Type qui fournit un objet de fonction pouvant comparer deux valeurs d'éléments comme clés de tri afin de déterminer leur ordre relatif dans la classe set. Cet argument est facultatif et le prédicat binaire est **inférieur** à *\<Key>* la valeur par défaut.

En C++ 14, vous pouvez activer la recherche hétérogène en spécifiant le `std::less<>` `std::greater<>` prédicat ou qui n’a aucun paramètre de type. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers) .

*Allocateur*\
Type qui représente l'objet allocateur stocké qui contient des informations sur l'allocation et la désallocation de mémoire de la classe set. Cet argument est facultatif et sa valeur par défaut est `allocator<Key>`.

## <a name="remarks"></a>Remarques

Une classe set de la bibliothèque standard C++ est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée. Il s’agit également d’un conteneur associatif simple, car ses valeurs d’éléments sont ses valeurs de clés.

- Réversible, car elle fournit un itérateur bidirectionnel pour accéder à ses éléments

- Triée, car les éléments sont classés par valeur de clé au sein du conteneur, selon une fonction de comparaison spécifiée.

- Unique dans le sens où chacun de ses éléments doit avoir une clé unique. Étant donné qu'il s'agit également d'un conteneur associatif simple, ses éléments sont également uniques.

Un jeu est également décrit comme un modèle de classe, car la fonctionnalité qu’il fournit est générique et indépendante du type spécifique des données contenues comme éléments. Le type de données à utiliser est spécifié comme paramètre dans le modèle de la classe, avec la fonction de comparaison et l'allocateur.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces, en les faisant dans un temps qui est en moyenne proportionnel au logarithme du nombre d’éléments dans le conteneur. L’insertion d’éléments n’invalide aucun itérateur, et la suppression d’éléments n’invalide que les itérateurs qui pointaient vers les éléments supprimés.

La classe set doit être sélectionnée comme conteneur associatif lorsque les conditions associant les valeurs à leurs clés sont remplies par l'application. Les éléments d'une classe set sont uniques et agissent comme leurs propres clés de tri. Pour ce type de structure, il peut s'agir d'une liste triée de mots qui ne peuvent apparaître qu'une seule fois. Si de multiples occurrences de mots sont autorisées, il convient d'utiliser une classe multiset comme structure de conteneur. Si les valeurs doivent être jointes à une liste de mots clés uniques, il convient d'utiliser une classe map comme conteneur de données. Si, à la place, les clés ne sont pas uniques, un Multimap serait le conteneur de choix.

La classe set trie la séquence qu’elle contrôle en appelant un objet de fonction stocké de type [key_compare](#key_compare). Cet objet stocké est une fonction de comparaison à laquelle il est possible d’accéder en appelant la fonction membre [key_comp](#key_comp). En général, les éléments doivent être simplement moins comparables pour établir cet ordre afin que, en fonction de deux éléments quelconques, il soit possible de déterminer s’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre) ou si l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. D’un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire *f*(*x, y*) est un objet de fonction qui a deux objets d’argument *x* et *y* et une valeur de retour de **`true`** ou **`false`** . Un tri appliqué à un ensemble est un ordre faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l’équivalence est transitive, où deux objets *x* et *y* sont définis comme équivalents lorsque *f* *x, y*) et *f*(*y, x*) ont la valeur false. Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

En C++ 14, vous pouvez activer la recherche hétérogène en spécifiant le `std::less<>` `std::greater<>` prédicat ou qui n’a aucun paramètre de type. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers) .

L’itérateur fourni par la classe set est un itérateur bidirectionnel. Toutefois, les fonctions membres de classe [insert](#insert) et [set](#set) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences de fonctionnalités sont minimales par rapport à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre ensemble de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s’agit d’un ensemble minimal de fonctionnalités, mais c’est suffisant pour pouvoir parler d’une plage d’itérateurs [ `First` , `Last` ) dans le contexte des fonctions membres de la classe.

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[set](#set)|Construit une classe set vide ou une copie de l'ensemble ou d'une partie d'une autre classe set.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet set.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément du jeu.|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un **`const`** élément d’un jeu.|
|[const_reference](#const_reference)|Type qui fournit une référence à un **`const`** élément stocké dans un jeu pour lire et effectuer des **`const`** opérations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément de l’ensemble.|
|[difference_type](#difference_type)|Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'une classe set au sein d'une plage, parmi les éléments pointés par les itérateurs.|
|[répétiteur](#iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'une classe set.|
|[key_compare](#key_compare)|Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'une classe set.|
|[key_type](#key_type)|Ce type décrit un objet stocké en tant qu'élément d'une classe set en sa qualité de clé de tri.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un élément d'une classe set.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans une classe set.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'une classe set inversée.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments d'une classe set.|
|[value_compare](#value_compare)|Type qui fournit un objet de fonction pouvant comparer deux éléments comme clés de tri pour déterminer leur ordre relatif dans la classe set.|
|[value_type](#value_type)|Ce type décrit un objet stocké en tant qu'élément d'une classe set en sa capacité en tant que valeur.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[commencer](#begin)|Retourne un itérateur qui référence le premier élément d'un objet `set`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `set`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `set`.|
|[clear](#clear)|Efface tous les éléments d'un `set`.|
|[contient](#contains)<sup>c++ 20</sup>|Vérifiez s’il existe un élément avec la clé spécifiée dans le `set` .|
|[count](#count)|Retourne le nombre d'éléments d'un `set` dont la clé correspond à une clé spécifiée par un paramètre.|
|[crbegin](#rbegin)|Retourne un itérateur const qui traite le premier élément d'un `set` inversé.|
|[crend](#rend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `set` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `set`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `set`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `set` est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `set`.|
|[equal_range](#equal_range)|Retourne une paire d'itérateurs, respectivement vers le premier élément d'un objet `set` avec une clé supérieure à une clé spécifiée, et vers le premier élément d'un objet `set` avec une clé supérieure ou égale à la clé.|
|[erase](#erase)|Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans une classe set ou supprime les éléments qui correspondent à une clé spécifiée.|
|[find](#find)|Retourne un itérateur qui référence l'emplacement d'un élément d'un objet `set` qui a une clé équivalente à une clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire le `set`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans un `set`.|
|[key_comp](#key_comp)|Récupère une copie de l'objet de comparaison utilisé pour trier les clés au sein d'un `set`.|
|[lower_bound](#lower_bound)|Retourne un itérateur au premier élément d'une classe set avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `set`.|
|[rbegin](#rbegin)|Retourne un itérateur qui traite le premier élément d'un `set` inversé.|
|[rend](#rend)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `set` inversé.|
|[size](#size)|Retourne le nombre d'éléments d'un `set`.|
|[swap](#swap)|Échange les éléments de deux `set`.|
|[upper_bound](#upper_bound)|Retourne un itérateur au premier élément d'un `set` avec une valeur de clé supérieure à celle de la clé spécifiée.|
|[value_comp](#value_comp)|Récupère une copie de l'objet de comparaison utilisé pour ordonner les valeurs des éléments d'un objet `set`.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur =](#op_eq)|Remplace les éléments d'une classe set par une copie d'une autre classe set.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Type représentant la classe allocator pour l’objet set.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Remarques

`allocator_type` est un synonyme de l' [allocateur](../standard-library/set-class.md)de paramètre de modèle.

Retourne l’objet de fonction utilisé par un multiset pour ordonner ses éléments, qui est le paramètre de modèle `Allocator`.

Pour plus d’informations sur `Allocator`, consultez la section Notes de la rubrique [set, classe](../standard-library/set-class.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="begin"></a><a name="begin"></a> commencer

Retourne un itérateur qui traite le premier élément d'une classe set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel qui traite le premier élément dans le set ou l’emplacement qui suit un set vide.

### <a name="remarks"></a>Remarques

Si la valeur de retour de `begin` est assignée à un `const_iterator` , les éléments de l’objet Set ne peuvent pas être modifiés. Si la valeur de retour de `begin` est assignée à un `iterator` , les éléments de l’objet Set peuvent être modifiés.

### <a name="example"></a>Exemple

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Retourne un **`const`** itérateur qui traite le premier élément de la plage.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`const`** Itérateur d’accès bidirectionnel qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()` ).

### <a name="remarks"></a>Remarques

Avec la valeur de retour `cbegin` , les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `begin()` et `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> CEND

Retourne un **`const`** itérateur qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`const`** Itérateur d’accès bidirectionnel qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Remarques

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `end()` et `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="clear"></a><a name="clear"></a> effacé

Efface tous les éléments d'une classe set.

```cpp
void clear();
```

### <a name="example"></a>Exemple

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément du jeu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_iterator` ne peut pas être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Consultez l’exemple [begin](#begin) pour obtenir un exemple qui utilise `const_iterator`.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Type qui fournit un pointeur vers un **`const`** élément d’un jeu.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarques

Un type `const_pointer` ne peut pas être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [const_iterator](#const_iterator) pour accéder aux éléments dans un objet set const.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Type qui fournit une référence à un **`const`** élément stocké dans un jeu pour lire et effectuer des **`const`** opérations.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Exemple

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference can't be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément de l’ensemble.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_reverse_iterator` ne peut pas modifier la valeur d’un élément et est utilisé pour itérer au sein du jeu en sens inverse.

### <a name="example"></a>Exemple

Consultez l’exemple [rend](#rend) pour savoir comment déclarer et utiliser le type `const_reverse_iterator`.

## <a name="contains"></a><a name="contains"></a> comprend

Vérifiez s’il existe un élément avec la clé spécifiée dans le `set` .

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Paramètres

*DK*\
Type de la clé.

*essentiel*\
Valeur de clé de l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

`true` Si l’élément est trouvé dans `set` ; `false` sinon,.

### <a name="remarks"></a>Remarques

`contains()` est nouveau dans C++ 20. Pour l’utiliser, spécifiez l’option de compilateur [/std : c + + latest](../build/reference/std-specify-language-standard-version.md) .

`template<class K> bool contains(const K& key) const` participe uniquement à la résolution de surcharge si `key_compare` est transparent. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](./stl-containers.md#heterogeneous-lookup-in-associative-containers-c14) .

### <a name="example"></a>Exemple

```cpp
// Requires /std:c++latest
#include <set>
#include <iostream>

int main()
{
    std::set<int> theSet = {1, 2};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theSet.contains(2) << '\n';
    std::cout << theSet.contains(3) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="count"></a><a name="count"></a> saut

Retourne le nombre d'éléments d'une classe set dont la clé correspond à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé des éléments à mettre en correspondance à partir de l'ensemble.

### <a name="return-value"></a>Valeur renvoyée

1 si la classe set contient un élément dont la clé de tri correspond à la clé de paramètre. 0 si l’ensemble ne contient pas d’élément avec une clé correspondante.

### <a name="remarks"></a>Remarques

La fonction membre retourne le nombre d'éléments dans la plage suivante :

\[ lower_bound (*clé*), upper_bound (*clé*)).

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre set::count.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

Retourne un itérateur const qui traite le premier élément d'un ensemble inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé const qui traite le premier élément dans un set inversé ou qui traite ce qui était le dernier élément dans le set non inversé.

### <a name="remarks"></a>Remarques

`crbegin` est utilisé avec un set inversé, de la même manière que [begin](#begin) est utilisé avec un set.

Avec la valeur de retour `crbegin` , l’objet Set ne peut pas être modifié.

### <a name="example"></a>Exemple

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a><a name="crend"></a> crend

Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un ensemble inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un set inversé (emplacement ayant précédé celui du premier élément du set non inversé).

### <a name="remarks"></a>Remarques

`crend` est utilisé avec un set inversé, de la même manière que [end](#end) est utilisé avec un set.

Avec la valeur de retour `crend` , l’objet Set ne peut pas être modifié. La valeur retournée par `crend` ne doit pas être déréférencée.

Vous pouvez utiliser `crend` pour déterminer si un itérateur inversé a atteint la fin de son set.

### <a name="example"></a>Exemple

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'une classe set au sein d'une plage, parmi les éléments pointés par les itérateurs.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Remarques

`difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type` est généralement utilisé pour représenter le nombre d’éléments de la plage *[ first,  last)* entre les itérateurs `first` et `last`. Il inclut l’élément vers lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) vers lequel pointe `last`.

Bien que `difference_type` soit disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui comprend la classe des itérateurs bidirectionnels pris en charge par les conteneurs réversibles tels que Set, la soustraction entre les itérateurs est prise en charge uniquement par les itérateurs à accès aléatoire fournis par un conteneur à accès aléatoire tel que Vector.

### <a name="example"></a>Exemple

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there's at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Arguments transmis pour construire un élément à insérer dans le set, sauf s’il contient déjà un élément dont la valeur est classée de façon équivalente.

### <a name="return-value"></a>Valeur renvoyée

[Paire](../standard-library/pair-structure.md) dont le composant bool retourne la valeur true si une insertion a été effectuée, ou la valeur false si la classe map contenait déjà un élément de valeur équivalente dans le classement. Le composant itérateur de la paire de la valeur de retour retourne l’adresse où un nouvel élément a été inséré (si le composant bool a la valeur true) ou l’adresse où l’élément se trouvait déjà (si le composant bool a la valeur false).

### <a name="remarks"></a>Remarques

Aucun itérateur ou référence n’est invalidé par cette fonction.

Pendant l’emplacement, si une exception est levée, l’état du conteneur n’est pas modifié.

### <a name="example"></a>Exemple

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a><a name="emplace_hint"></a> emplace_hint

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée) avec un hint d’emplacement.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Arguments transmis pour construire un élément à insérer dans le set, sauf si le set contient déjà cet élément ou, plus généralement, s’il contient déjà un élément dont la valeur est classée de façon équivalente.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement *, l'* insertion peut se produire dans le temps constant amorti plutôt que dans le temps logarithmique.)

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’élément qui vient d’être inséré.

Si l’insertion a échoué parce que l’élément existe déjà, retourne un itérateur vers l’élément existant.

### <a name="remarks"></a>Remarques

Aucun itérateur ou référence n’est invalidé par cette fonction.

Pendant l’emplacement, si une exception est levée, l’état du conteneur n’est pas modifié.

### <a name="example"></a>Exemple

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> vidé

Vérifie si une classe set est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le jeu est vide ; **`false`** si le jeu n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a><a name="end"></a> effet

Retourne l'itérateur past-the-end.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur de type past-the-end. Si l'ensemble est vide, puis `set::end() == set::begin()`.

### <a name="remarks"></a>Remarques

**end** est utilisé pour déterminer si un itérateur a dépassé la fin de son set.

La valeur retournée par **end** ne doit pas être déréférencée.

Pour obtenir un exemple de code, consultez [set::find](#find).

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

Retourne une paire d’itérateurs, respectivement au premier élément dans un set ayant une clé supérieure ou égale à une clé spécifiée et au premier élément dans le set ayant une clé supérieure à la clé.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du set dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Paire d’itérateurs telle que le premier est la [lower_bound](#lower_bound) de la clé et le second est la [upper_bound](#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **tout d’abord**, et pour déréférencer l’itérateur de la limite inférieure, utilisez \* ( `pr` . **tout d’abord**). Pour accéder au second itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **Deuxièmement**, et pour déréférencer l’itérateur de la limite supérieure, utilisez \* ( `pr` . **seconde**).

### <a name="example"></a>Exemple

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> effacer

Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans une classe set ou supprime les éléments qui correspondent à une clé spécifiée.

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

### <a name="return-value"></a>Valeur renvoyée

Pour les deux premières fonctions membres, itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou élément à la fin du set si aucun élément de ce type n’existe.

Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés du set.

### <a name="example"></a>Exemple

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a><a name="find"></a> trouver

Retourne un itérateur qui fait référence à l'emplacement d'un élément dans un ensemble ayant une clé équivalente à la clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé qui doit correspondre à la clé de tri d'un élément de l'ensemble dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui fait référence à l'emplacement d'un élément ayant la clé spécifiée, ou emplacement qui suit le dernier élément de l'ensemble (`set::end()`), si aucune correspondance n'est trouvée pour la clé.

### <a name="remarks"></a>Remarques

La fonction membre retourne un itérateur qui fait référence à un élément de l’ensemble dont la clé est équivalente à la *clé* d’argument sous un prédicat binaire qui induit un classement basé sur une relation d’infériorité.

Si la valeur de retour de `find` est assignée à un `const_iterator` , l’objet Set ne peut pas être modifié. Si la valeur de retour de `find` est assignée à un `iterator` , l’objet set peut être modifié.

### <a name="example"></a>Exemple

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Retourne une copie de l’objet allocateur utilisé pour construire le set.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur renvoyée

Allocateur utilisé par le set pour gérer la mémoire, qui est le paramètre de modèle `Allocator`.

Pour plus d’informations sur `Allocator`, consultez la section Notes de la rubrique [set, classe](../standard-library/set-class.md).

### <a name="remarks"></a>Remarques

Les allocateurs de la classe set spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> Insérer

Insère un élément ou une plage d'éléments dans une classe set.

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
Valeur d'un élément à insérer dans la classe set à moins qu'elle ne contienne déjà un élément dont la valeur est classée de façon équivalente.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement *, l'* insertion peut se produire dans le temps constant amorti plutôt que dans le temps logarithmique.)

*ValTy*\
Paramètre de modèle qui spécifie le type d’argument que le jeu peut utiliser pour construire un élément de [Value_type](../standard-library/map-class.md#value_type), et parfait-transfère la valeur *Val* comme argument.

*Premier*\
Position du premier élément à copier.

*Famille*\
Position juste au-delà du dernier élément à copier.

*InputIterator*\
Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](../standard-library/map-class.md#value_type).

*IList*\
[Initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.

### <a name="return-value"></a>Valeur renvoyée

Les fonctions membres à un élément, (1) et (2), retournent une [paire](../standard-library/pair-structure.md) dont **`bool`** le composant a la valeur true si une insertion a été effectuée, et false si le jeu contient déjà un élément de valeur équivalente dans le classement. Le composant itérateur de la paire de valeur de retour pointe sur l’élément qui vient d’être inséré si le **`bool`** composant a la valeur true ou sur l’élément existant si le **`bool`** composant a la valeur false.

Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe sur la position où le nouvel élément a été inséré dans la classe set ou, si un élément avec une clé équivalente existe déjà, sur l'élément existant.

### <a name="remarks"></a>Remarques

Aucun itérateur, pointeur ou référence n'est invalidé par cette fonction.

Pendant l’insertion d’un seul élément, si une exception est levée, l’état du conteneur n’est pas modifié. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.

Pour accéder au composant itérateur d’un objet `pair` `pr` retourné par les fonctions membres à un élément, utilisez `pr.first`. Pour déréférencer l’itérateur dans la paire retournée, utilisez `*pr.first`, qui vous donne un élément. Pour accéder au **`bool`** composant, utilisez `pr.second` . Pour obtenir un exemple, voir l'exemple de code plus loin dans cet article.

Le [value_type](../standard-library/map-class.md#value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe set, `set<V>::value_type` est du type `const V`.

La fonction membre de plage (5) insère la séquence de valeurs d’éléments dans un jeu qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; par conséquent, `Last` n’est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `s.insert(v.begin(), v.end());` tente d'insérer tous les éléments de `v` dans `s`. Seuls les éléments qui ont des valeurs uniques dans la plage sont insérés. Les doublons sont ignorés. Pour savoir quels éléments sont rejetés, utilisez les versions à un élément de `insert`.

La fonction membre de liste d’initialiseurs (6) utilise une [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans la classe set.

Pour plus d’informations sur l’insertion d’un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée), consultez [set::emplace](#emplace) et [set::emplace_hint](#emplace_hint).

### <a name="example"></a>Exemple

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> répétiteur

Type qui fournit un [itérateur bidirectionnel](../standard-library/bidirectional-iterator-tag-struct.md) constant capable de lire un élément dans un set.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [Begin](#begin) pour obtenir un exemple de la façon de déclarer et d’utiliser un `iterator` .

## <a name="key_comp"></a><a name="key_comp"></a> key_comp

Récupère une copie de l'objet de comparaison utilisé pour trier les clés au sein d'une classe set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet de fonction utilisé par un set pour trier ses éléments, qui est le paramètre de modèle `Traits`.

Pour plus d’informations sur `Traits` , consultez la rubrique [Set Class](../standard-library/set-class.md) .

### <a name="remarks"></a>Remarques

L’objet stocké définit la fonction membre :

**bool, opérateur ()**(**clé const&** `_xVal` , **clé const&** `_yVal` );

qui retourne **`true`** si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

[Key_compare](#key_compare) et [value_compare](#value_compare) sont des synonymes du paramètre de modèle `Traits` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a><a name="key_compare"></a> key_compare

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'une classe set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarques

`key_compare` est un synonyme du paramètre de modèle `Traits`.

Pour plus d’informations sur `Traits` , consultez la rubrique [Set Class](../standard-library/set-class.md) .

`key_compare`Et [value_compare](#value_compare) sont des synonymes du paramètre de modèle `Traits` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_compare`, consultez l’exemple [key_comp](#key_comp).

## <a name="key_type"></a><a name="key_type"></a> key_type

Type qui décrit un objet stocké comme élément d’un set en sa qualité de clé de tri.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarques

`key_type` est un synonyme du paramètre de modèle `Key`.

Pour plus d’informations sur `Key`, consultez la section Notes de la rubrique [set, classe](../standard-library/set-class.md).

`key_type`Et [Value_type](#value_type) sont des synonymes du paramètre de modèle `Key` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_type`, consultez l’exemple [value_type](#value_type).

## <a name="lower_bound"></a><a name="lower_bound"></a> lower_bound

Retourne un itérateur au premier élément d'une classe set avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du set dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Itérateur ou `const_iterator` qui traite l’emplacement d’un élément dans un set ayant une clé supérieure ou égale à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le set si aucune correspondance n’est trouvée pour la clé.

### <a name="example"></a>Exemple

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a><a name="max_size"></a> max_size

Retourne la longueur maximale de la classe set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur maximale autorisée du set.

### <a name="example"></a>Exemple

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> opérateur =

Remplace les éléments de ce `set` par les éléments d’un autre `set`.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
`set` fournissant les nouveaux éléments à assigner à ce `set`.

### <a name="remarks"></a>Remarques

La première version de `operator=` utilise une [référence lvalue](../cpp/lvalue-reference-declarator-amp.md) pour *Right*pour copier des éléments de *droite* vers ce `set` .

La deuxième version utilise [rvalue reference](../cpp/rvalue-reference-declarator-amp-amp.md) pour right. Il déplace les éléments de *droite* vers ce `set` .

Les éléments de ce `set` avant l’exécution de la fonction d’opérateur sont ignorés.

### <a name="example"></a>Exemple

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

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

## <a name="pointer"></a>Pointeur <a name="pointer"></a>

Type qui fournit un pointeur vers un élément d'une classe set.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Remarques

Un type **pointer** peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet set.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Retourne un itérateur qui traite le premier élément d'une classe set inversée.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé qui traite le premier élément dans un set inversé ou qui traite ce qui était le dernier élément dans le set non inversé.

### <a name="remarks"></a>Remarques

`rbegin` est utilisé avec un set inversé, de la même manière que [begin](#begin) est utilisé avec un set.

Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator` , l’objet Set ne peut pas être modifié. Si la valeur de retour de `rbegin` est assignée à un `reverse_iterator`, l’objet set peut être modifié.

Vous pouvez utiliser `rbegin` pour itérer un set vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a><a name="reference"></a> faire

Type qui fournit une référence à un élément stocké dans une classe set.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Exemple

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a><a name="rend"></a> rend

Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'une classe set inversée.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un set inversé (emplacement ayant précédé celui du premier élément du set non inversé).

### <a name="remarks"></a>Remarques

`rend` est utilisé avec un set inversé, de la même manière que [end](#end) est utilisé avec un set.

Si la valeur de retour de `rend` est assignée à un `const_reverse_iterator` , l’objet Set ne peut pas être modifié. Si la valeur de retour de `rend` est assignée à un `reverse_iterator`, l’objet set peut être modifié. La valeur retournée par `rend` ne doit pas être déréférencée.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son set.

### <a name="example"></a>Exemple

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'une classe set inversée.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `reverse_iterator` est utilisé pour itérer au sein du jeu en sens inverse.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="set"></a><a name="set"></a> définie

Construit une classe set vide ou une copie de l'ensemble ou d'une partie d'une autre classe set.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

*&*\
Classe d’allocateur de stockage à utiliser pour cet objet set, qui a comme valeur par défaut `Allocator` .

*Conformes*\
Fonction de comparaison de type `const Traits` utilisée pour classer les éléments dans le set (par défaut, `Compare`).

*Rght*\
Set dont le set construit doit être une copie.

*Premier*\
Position du premier élément de la plage d'éléments à copier.

*Famille*\
Position du premier élément au-delà de la plage d'éléments à copier.

*IList*\
Initializer_list depuis laquelle copier les éléments.

### <a name="remarks"></a>Remarques

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du set et peut être retourné ultérieurement en appelant [get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe, et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leurs objets set.

Tous les constructeurs stockent un objet de fonction de type `Traits` qui est utilisé pour établir un ordre parmi les clés du jeu et qui peut être retourné ultérieurement en appelant [key_comp](#key_comp).

Les trois premiers constructeurs spécifient un jeu initial vide, le second spécifiant le type de fonction de comparaison ( `comp` ) à utiliser pour établir l’ordre des éléments et le troisième spécifie explicitement le type d’allocateur ( `al` ) à utiliser. Le mot clé **`explicit`** supprime certains genres de conversion de type automatique.

Le quatrième constructeur spécifie une copie du set `right`.

Les trois constructeurs suivants utilisent initializer_list pour spécifier les éléments.

Les trois constructeurs suivants copient la plage [ `first` , `last` ) d’un jeu avec un caractère explicite accru dans la spécification du type de fonction de comparaison de classe `Traits` et d' **Allocator**.

Le huitième constructeur spécifie une copie du set en déplaçant `right`.

### <a name="example"></a>Exemple

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a><a name="size"></a> corps

Retourne le nombre d'éléments figurant dans le jeu.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur actuelle du set.

### <a name="example"></a>Exemple

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Type entier non signé qui peut représenter le nombre d'éléments d'une classe set.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).

## <a name="swap"></a><a name="swap"></a> échange

Échange les éléments de deux classes set.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Argument set qui fournit les éléments à échanger avec le set cible.

### <a name="remarks"></a>Remarques

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux sets dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> upper_bound

Retourne un itérateur au premier élément d’un set ayant une valeur de clé supérieure à celle de la clé spécifiée.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du set dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

`iterator`Ou `const_iterator` qui traite l’emplacement d’un élément dans un ensemble qui a une clé supérieure à la clé d’argument, ou qui traite l’emplacement qui suit le dernier élément du jeu si aucune correspondance n’est trouvée pour la clé.

### <a name="example"></a>Exemple

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> value_comp

Récupère une copie de l'objet de comparaison utilisé pour trier les valeurs d'éléments d'une classe set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet de fonction utilisé par un set pour trier ses éléments, qui est le paramètre de modèle `Traits`.

Pour plus d’informations sur `Traits` , consultez la rubrique [Set Class](../standard-library/set-class.md) .

### <a name="remarks"></a>Remarques

L’objet stocké définit la fonction membre :

**bool, opérateur**(**&de clé const ** `_xVal` , **clé const&** `_yVal` );

qui retourne **`true`** si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

[Value_compare](#value_compare) et [key_compare](#key_compare) sont des synonymes du paramètre de modèle `Traits` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a><a name="value_compare"></a> value_compare

Type qui fournit un objet de fonction pouvant comparer deux valeurs d’élément pour déterminer leur ordre relatif dans la classe set.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Remarques

`value_compare` est un synonyme du paramètre de modèle `Traits`.

Pour plus d’informations sur `Traits` , consultez la rubrique [Set Class](../standard-library/set-class.md) .

Les [key_compare](#key_compare) et `value_compare` sont des synonymes du paramètre de modèle `Traits` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Consultez l’exemple [value_comp](#value_comp) pour savoir comment déclarer et utiliser `value_compare`.

## <a name="value_type"></a><a name="value_type"></a> value_type

Type qui décrit un objet stocké comme élément d’un set en sa qualité de valeur.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Remarques

`value_type` est un synonyme du paramètre de modèle `Key`.

Pour plus d’informations sur `Key`, consultez la section Notes de la rubrique [set, classe](../standard-library/set-class.md).

Les [KEY_TYPE](#key_type) et `value_type` sont des synonymes du paramètre de modèle `Key` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
