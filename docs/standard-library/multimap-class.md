---
title: multimap, classe
description: Référence d’API pour la classe C++ Standard Template Library (STL) `multimap` , qui est utilisée pour le stockage et la récupération des données d’une collection dans laquelle chaque élément est une paire qui a à la fois une valeur de données et une clé de tri.
ms.date: 9/9/2020
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::contains
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], contains
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
ms.openlocfilehash: 7399132553205080cc784de78630e30feb0700ba
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509926"
---
# <a name="multimap-class"></a>multimap, classe

La classe multimap de la bibliothèque standard C++ est utilisée pour le stockage et la récupération des données d’une collection dans laquelle chaque élément est une paire constituée d’une valeur de données et d’une clé de tri. La valeur de la clé n’a pas besoin d’être unique et est utilisée pour trier automatiquement les données. La valeur d'un élément d'une classe multimap peut être modifiée directement, mais pas la valeur de clé qui lui est associée. Les valeurs de clés associées aux anciens éléments doivent être supprimées, et de nouvelles valeurs de clés doivent être associées aux nouveaux éléments insérés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Paramètres

*Essentiel*\
Type de données clé à stocker dans la classe multimap.

*Entrer*\
Type de données d'élément à stocker dans la classe multimap.

*Caractéristiques*\
Type qui fournit un objet de fonction pouvant comparer deux valeurs d'éléments comme clés de tri afin de déterminer leur ordre relatif dans la classe multimap. Le prédicat binaire `less<Key>` est la valeur par défaut.

Dans C++14, vous pouvez activer la recherche hétérogène en spécifiant le prédicat `std::less<>` ou `std::greater<>` qui n'a aucun paramètre de type. Pour plus d’informations, consultez [Recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14).

*Allocateur*\
Type qui représente l'objet allocateur stocké qui contient des informations sur l'allocation et la désallocation de mémoire de la classe map. Cet argument est facultatif et sa valeur par défaut est `allocator<pair <const Key, Type> >`.

## <a name="remarks"></a>Remarques

La classe multimap de la bibliothèque standard C++ est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée.

- Réversible, car elle fournit des itérateurs bidirectionnels pour accéder à ses éléments.

- Triée, car les éléments sont classés par valeur de clé au sein du conteneur, selon une fonction de comparaison spécifiée.

- Plusieurs, car ses éléments n’ont pas besoin d’une clé unique, de sorte qu’une valeur de clé peut avoir plusieurs valeurs de données d’élément associées.

- Un conteneur associatif de paires, car ses valeurs de données d'éléments sont séparées de ses valeurs de clés.

- Un modèle de classe, parce que la fonctionnalité qu’il fournit est générique et donc indépendante du type spécifique des données contenues en tant qu’éléments ou clés. Les types de données utilisés pour les éléments et les clés sont eux spécifiés comme paramètres dans la classe de modèle avec la fonction de comparaison et l'allocateur.

L’itérateur fourni par la classe map est un itérateur bidirectionnel. Toutefois, les fonctions membres de classe [insert](#insert) et [multimap](#multimap) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences de fonctionnalités sont minimales par rapport à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre ensemble de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s'agit d'un jeu minimal de fonctionnalités, mais c'est suffisant pour pouvoir parler de plage d'itérateurs (`[First, Last)`) dans le contexte des fonctions membres de la classe.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces, car elles les exécutent en un temps qui est, en moyenne, proportionnel au logarithme du nombre d'éléments dans le conteneur. L’insertion d’éléments n’invalide aucun itérateur, et la suppression d’éléments n’invalide que les itérateurs qui avaient pointé sur les éléments supprimés.

La classe multimap doit être sélectionnée comme conteneur associatif lorsque les conditions associant les valeurs à leurs clés sont remplies par l'application. Un modèle pour ce type de structure est une liste ordonnée de mots clés avec des valeurs de chaîne associées fournissant, par exemple, des définitions, où les mots n’ont pas toujours été définis de manière unique. Si, en revanche, les mots clés sont définis de manière unique afin que les clés soient uniques, il convient d'utiliser une classe map comme conteneur. Si, en revanche, seule la liste de mots a été stockée, il convient d'utiliser une classe set comme conteneur. Si plusieurs occurrences des mots étaient autorisées, `multiset` il s’agit de la structure de conteneur appropriée.

La classe multimap trie la séquence qu’elle contrôle en appelant un objet de fonction stocké de type [key_compare](#key_compare). Cet objet stocké est une fonction de comparaison à laquelle il est possible d’accéder en appelant la fonction membre [key_comp](#key_comp). En général, les éléments ne doivent pas être tout à fait comparables, afin que, à l'aide de deux événements quelconques donnés, il soit possible de déterminer, soit qu'ils soient équivalents (dans le sens où l'un n'est pas inférieur à l'autre), soit que l'un est inférieur à l'autre. Cela entraîne le tri des éléments non équivalents. D’un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire `f(x,y)` est un objet de fonction qui a deux objets d'argument `x` et `y`, et une valeur de retour true ou false. Un tri appliqué à un ensemble est un ordre faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l'équivalence est transitive, où deux objets `x` et `y` sont définis comme équivalents lorsque `f(x,y)` et `f(y,x)` sont false. Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

Dans C++14, vous pouvez activer la recherche hétérogène en spécifiant le prédicat `std::less<>` ou `std::greater<>` qui n'a aucun paramètre de type. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers) .

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[multimap](#multimap)|Construit un `multimap` vide ou une copie de l'ensemble ou d'une partie d'un autre `multimap`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet `multimap`.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément dans le `multimap` .|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un **`const`** élément d’un `multimap` .|
|[const_reference](#const_reference)|Type qui fournit une référence à un **`const`** élément stocké dans un `multimap` pour la lecture et l’exécution d' **`const`** opérations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément de `multimap` .|
|[difference_type](#difference_type)|Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'un `multimap` au sein d'une plage, parmi les éléments pointés par les itérateurs.|
|[répétiteur](#iterator)|Type qui fournit la différence entre deux itérateurs qui font référence aux éléments d'un même `multimap`.|
|[key_compare](#key_compare)|Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'un `multimap`.|
|[key_type](#key_type)|Type qui décrit l’objet de clé de tri qui compose chaque élément de `multimap` .|
|[mapped_type](#mapped_type)|Type qui représente le type de données stocké dans un `multimap`.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un **`const`** élément d’un `multimap` .|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un `multimap`.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'un `multimap` inversé.|
|[size_type](#size_type)|Type entier non signé qui fournit un pointeur vers un **`const`** élément d’un `multimap` .|
|[value_type](#value_type)|Type qui fournit un objet de fonction pouvant comparer deux éléments comme clés de tri pour déterminer leur ordre relatif dans le `multimap`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[commencer](#begin)|Retourne un itérateur traitant le premier élément d'un `multimap`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `multimap`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `multimap`.|
|[clear](#clear)|Efface tous les éléments d'un `multimap`.|
|[contient](#contains)<sup>c++ 20</sup>|Vérifie s’il existe un élément avec la clé spécifiée dans le `multimap` .|
|[count](#count)|Retourne le nombre d'éléments d'un `multimap` dont la clé correspond à une clé spécifiée par un paramètre.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un `multimap` inversé.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `multimap` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `multimap`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `multimap`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `multimap` est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `multimap`.|
|[equal_range](#equal_range)|Recherche la plage d'éléments dans laquelle se trouve une clé d'élément correspondant à une valeur spécifiée.|
|[erase](#erase)|Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un `multimap` ou supprime les éléments qui correspondent à une clé spécifiée.|
|[find](#find)|Retourne un itérateur qui traite le premier emplacement d'un élément dans un `multimap` possédant une clé équivalente à une clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire le `multimap`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans un `multimap`.|
|[key_comp](#key_comp)|Récupère une copie de l'objet de comparaison utilisé pour trier les clés au sein d'un `multimap`.|
|[lower_bound](#lower_bound)|Retourne un itérateur au premier élément d'un `multimap` avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `multimap`.|
|[rbegin](#rbegin)|Retourne un itérateur qui traite le premier élément d'un `multimap` inversé.|
|[rend](#rend)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `multimap` inversé.|
|[size](#size)|Retourne le nombre d'éléments d'un `multimap`.|
|[swap](#swap)|Échange les éléments de deux `multimap`.|
|[upper_bound](#upper_bound)|Retourne un itérateur au premier élément d'un `multimap` avec une valeur de clé supérieure à celle de la clé spécifiée.|
|[value_comp](#value_comp)|La fonction membre retourne un objet de fonction qui détermine l'ordre des éléments d'un `multimap` en comparant leurs valeurs de clés.|

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Remplace les éléments d'un `multimap` par une copie d'un autre `multimap`.|

## <a name="requirements"></a>Configuration requise

**En-tête :**\<map>

**Espace de noms :** std

Les paires (**key**, **value**) sont stockées dans une classe multimap en tant qu’objets de type `pair`. La classe de paire requiert l’en-tête \<utility> , qui est inclus automatiquement par \<map> .

## <a name="multimapallocator_type"></a><a name="allocator_type"></a> Multimap :: allocator_type

Type qui représente la classe allocator pour l’objet multimap.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="multimapbegin"></a><a name="begin"></a> Multimap :: Begin

Retourne un itérateur qui traite le premier élément du multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel qui traite le premier élément du multimap ou l’emplacement qui suit un multimap vide.

### <a name="example"></a>Exemple

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="multimapcbegin"></a><a name="cbegin"></a> Multimap :: cbegin

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

## <a name="multimapcend"></a><a name="cend"></a> Multimap :: CEND

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

## <a name="multimapclear"></a><a name="clear"></a> Multimap :: Clear

Efface tous les éléments d'un multimap.

```cpp
void clear();
```

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multimap::clear.

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="multimapconst_iterator"></a><a name="const_iterator"></a> Multimap :: const_iterator

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément dans le Multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_iterator` ne peut pas être utilisé pour modifier la valeur d’un élément.

Le `const_iterator` défini par Multimap pointe vers les objets de [Value_type](#value_type), qui sont de type `pair<const Key, Type>` . La valeur de la clé est disponible par l’intermédiaire du premier membre de la paire, et la valeur de l’élément mappé est disponible par l’intermédiaire du deuxième membre de la paire.

Pour déréférencer un `const_iterator` *cite* pointant vers un élément d’un multimap, utilisez l' **->** opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `cIter->first` , qui est équivalent à `(*cIter).first` . Pour accéder à la valeur de la référence mappée de l’élément, utilisez `cIter->second` , qui est équivalent à `(*cIter).second` .

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `const_iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="multimapconst_pointer"></a><a name="const_pointer"></a> Multimap :: const_pointer

Type qui fournit un pointeur vers un **`const`** élément d’un Multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarques

Un type `const_pointer` ne peut pas être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet multimap.

## <a name="multimapconst_reference"></a><a name="const_reference"></a> Multimap :: const_reference

Type qui fournit une référence à un **`const`** élément stocké dans un Multimap pour la lecture et l’exécution d' **`const`** opérations.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Exemple

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> Multimap :: const_reverse_iterator

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément dans le Multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_reverse_iterator` ne peut pas modifier la valeur d’un élément et est utilisé pour itérer au sein du Multimap en sens inverse.

Le `const_reverse_iterator` défini par Multimap pointe vers les objets de [Value_type](#value_type), qui sont de type `pair<const Key, Type>` . La valeur de la clé est disponible par l’intermédiaire du premier membre de la paire, et la valeur de l’élément mappé est disponible par l’intermédiaire du deuxième membre de la paire.

Pour déréférencer `const_reverse_iterator` *un* élément de plus en pointant sur un élément d’un multimap, utilisez l' **->** opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `crIter->first` , qui est équivalent à `(*crIter).first` . Pour accéder à la valeur de la référence mappée de l’élément, utilisez `crIter->second` , qui est équivalent à `(*crIter).first` .

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `const_reverse_iterator`, consultez l’exemple [rend](#rend).

## <a name="multimapcontains"></a><a name="contains"></a> Multimap :: Contains

Vérifiez s’il existe un élément avec la clé spécifiée dans le `multimap` .

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

`true` Si l’élément est trouvé dans le conteneur ; `false` sinon,.

### <a name="remarks"></a>Remarques

`contains()` est nouveau dans C++ 20. Pour l’utiliser, spécifiez l’option de compilateur [/std : c + + latest](../build/reference/std-specify-language-standard-version.md) .

`template<class K> bool contains(const K& key) const` participe uniquement à la résolution de surcharge si `key_compare` est transparent. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](./stl-containers.md#heterogeneous-lookup-in-associative-containers-c14) .

### <a name="example"></a>Exemple

```cpp
// Requires /std:c++latest
#include <map>
#include <string>
#include <iostream>
#include <functional>

int main()
{
    std::multimap<int, bool> m = {{0, false}, {1, true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << m.contains(1) << '\n';
    std::cout << m.contains(2) << '\n';

    // call template function
    std::multimap<std::string, int, std::less<>> m2 = {{"ten", 10}, {"twenty", 20}, {"thirty", 30}};
    std::cout << m2.contains("ten");

    return 0;
}
```

```Output
true
false
true
```

## <a name="multimapcount"></a><a name="count"></a> Multimap :: Count

Retourne le nombre d'éléments d'un multimap dont les clés correspondent à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé des éléments à mettre en correspondance à partir du multimap.

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments dont les clés de tri correspondent à la clé de paramètre ; 0 si le multimap ne contient pas d'élément avec une clé correspondante.

### <a name="remarks"></a>Remarques

La fonction membre retourne le nombre d'éléments dans la plage

\[ lower_bound (*clé*), upper_bound (*clé*))

qui ont une *clé*de valeur de clé.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre multimap::count.

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements don't need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="multimapcrbegin"></a><a name="crbegin"></a> Multimap :: crbegin

Retourne un itérateur const qui traite le premier élément d’un multimap inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé const qui traite le premier élément d’un [multimap](../standard-library/multimap-class.md) inversé ou qui traite ce qui était le dernier élément de l’objet `multimap` non inversé.

### <a name="remarks"></a>Remarques

`crbegin` est utilisé avec une classe `multimap` inversée de la même manière que [begin](#begin) est utilisé avec une classe `multimap`.

Avec la valeur de retour `crbegin` , l' `multimap` objet ne peut pas être modifié.

`crbegin` peut servir à itérer un `multimap` vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="multimapcrend"></a><a name="crend"></a> Multimap :: crend

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un multimap inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un [multimap](../standard-library/multimap-class.md) inversé (emplacement qui précédait celui du premier élément du `multimap` non inversé).

### <a name="remarks"></a>Remarques

`crend` est utilisé avec un `multimap` inversé comme [multimap::end](#end) est utilisé avec un `multimap`.

Avec la valeur de retour `crend` , l' `multimap` objet ne peut pas être modifié.

`crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son objet `multimap`.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="multimapdifference_type"></a><a name="difference_type"></a> Multimap ::d ifference_type

Type entier signé qui peut être utilisé pour représenter le nombre d’éléments d’un multimap au sein d’une plage, parmi les éléments pointés par les itérateurs.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Remarques

`difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type`Est généralement utilisé pour représenter le nombre d’éléments dans la plage [*First*, *Last*) entre les itérateurs `first` et `last` , inclut l’élément vers lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) vers lequel pointe `last` .

Bien que `difference_type` soit disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui comprend la classe des itérateurs bidirectionnels pris en charge par les conteneurs réversibles tels que Set, la soustraction entre les itérateurs est prise en charge uniquement par les itérateurs à accès aléatoire fournis par un conteneur à accès aléatoire tel que Vector.

### <a name="example"></a>Exemple

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="multimapemplace"></a><a name="emplace"></a> Multimap :: emplace

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Arguments transférés pour construire un élément à insérer dans le multimap.

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’élément qui vient d’être inséré.

### <a name="remarks"></a>Remarques

Aucune référence aux éléments de conteneur n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Si une exception est levée pendant l’insertion, le conteneur n’est pas modifié et l’exception est levée une nouvelle fois.

Le [value_type](../standard-library/map-class.md#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

### <a name="example"></a>Exemple

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="multimapemplace_hint"></a><a name="emplace_hint"></a> Multimap :: emplace_hint

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée) avec un hint d’emplacement.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Arguments transférés pour construire un élément à insérer dans le multimap.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement *, l'* insertion peut se produire dans le temps constant amorti plutôt que dans le temps logarithmique.)

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’élément qui vient d’être inséré.

### <a name="remarks"></a>Remarques

Aucune référence aux éléments de conteneur n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Durant le placement, si une exception est levée, l’état du conteneur n’est pas modifié.

Le [value_type](../standard-library/map-class.md#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

Pour obtenir un exemple de code, consultez [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="multimapempty"></a><a name="empty"></a> Multimap :: Empty

Teste si un multimap est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le Multimap est vide ; **`false`** si Multimap n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="multimapend"></a><a name="end"></a> Multimap :: fin

Retourne l'itérateur past-the-end.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur de type past-the-end. Si le mappage multiple est vide, puis `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Remarques

**end** est utilisé pour déterminer si un itérateur a dépassé la fin de son multimap.

La valeur retournée par **end** ne doit pas être déréférencée.

Pour obtenir un exemple de code, consultez [multimap::find](#find).

## <a name="multimapequal_range"></a><a name="equal_range"></a> Multimap :: equal_range

Recherche la plage d'éléments dans laquelle se trouve une clé d'élément correspondant à une valeur spécifiée.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Paire d’itérateurs telle que le premier est la [lower_bound](#lower_bound) de la clé et le second est la [upper_bound](#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **tout d’abord** , et pour déréférencer l’itérateur de la limite inférieure, utilisez \* ( `pr` . **tout d’abord**). Pour accéder au second itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **ensuite** , pour déréférencer l’itérateur de la limite supérieure, utilisez \* ( `pr` . **seconde**).

### <a name="example"></a>Exemple

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="multimaperase"></a><a name="erase"></a> Multimap :: Erase

Supprime d’un emplacement spécifié un élément ou une plage d’éléments compris dans un multimap ou supprime les éléments qui correspondent à une clé spécifiée.

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
Clé des éléments à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Pour les deux premières fonctions membres, itérateur bidirectionnel qui désigne le premier élément restant après que tous les éléments ont été supprimés ou élément à la fin de la classe map si aucun élément de ce type n’existe.

Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés du multimap.

### <a name="remarks"></a>Remarques

Pour obtenir un exemple de code, consultez [map::erase](../standard-library/map-class.md#erase).

## <a name="multimapfind"></a><a name="find"></a> Multimap :: find

Retourne un itérateur qui fait référence au premier emplacement d'un élément dans un mappage multiple dont la clé est équivalente à la clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé qui doit correspondre à la clé de tri d'un élément du mappage multiple dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui fait référence à l'emplacement d'un élément ayant la clé spécifiée, ou emplacement qui suit le dernier élément du mappage multiple (`multimap::end()`), si aucune correspondance n'est trouvée pour la clé.

### <a name="remarks"></a>Remarques

La fonction membre retourne un itérateur qui fait référence à un élément du mappage multiple dont la clé de tri est équivalente à l’argument key sous un prédicat binaire qui induit un classement basé sur une relation d’infériorité.

Si la valeur de retour de `find` est assignée à un `const_iterator` , l’objet Multimap ne peut pas être modifié. Si la valeur de retour de `find` est assignée à `iterator` , l’objet Multimap peut être modifié.

### <a name="example"></a>Exemple

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="multimapget_allocator"></a><a name="get_allocator"></a> Multimap :: get_allocator

Retourne une copie de l’objet allocateur utilisé pour construire le multimap.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur renvoyée

Allocateur utilisé par le multimap.

### <a name="remarks"></a>Remarques

Les allocateurs de la classe multimap spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multimapinsert"></a><a name="insert"></a> Multimap :: Insert

Insère un élément ou une plage d'éléments dans une classe multimap.

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
Valeur d'un élément à insérer dans la classe multimap.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement *, l'* insertion peut se produire dans le temps constant amorti plutôt que dans le temps logarithmique.)

*ValTy*\
Paramètre de modèle qui spécifie le type d’argument que le mappage peut utiliser pour construire un élément de [Value_type](../standard-library/map-class.md#value_type), et parfait-transfère la valeur *Val* comme argument.

*Premier*\
Position du premier élément à copier.

*Famille*\
Position juste au-delà du dernier élément à copier.

*InputIterator*\
Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](../standard-library/map-class.md#value_type).

*IList*\
[Initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.

### <a name="return-value"></a>Valeur renvoyée

Les fonctions membres d'insertion à un élément, (1) et (2), retournent un itérateur vers l'emplacement où le nouvel élément a été inséré dans la classe multimap.

Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe vers l'emplacement où le nouvel élément a été inséré dans la classe multimap.

### <a name="remarks"></a>Remarques

Aucun pointeur ou référence n'est invalidé par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Durant l'insertion d'un seul élément, si une exception est levée, l'état du conteneur n'est pas modifié. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.

Le [value_type](../standard-library/map-class.md#value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe map, `multimap<K, V>::value_type` est `pair<const K, V>`. La valeur d'un élément est une paire ordonnée dans laquelle le premier composant est égal à la valeur de clé et le second composant est égal à la valeur de données de l'élément.

La fonction membre de plage (5) insère la séquence de valeurs d’éléments dans un Multimap qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; par conséquent, *Last* n’est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `m.insert(v.begin(), v.end());` insère tous les éléments de `v` dans `m`.

La fonction membre de liste d’initialiseurs (6) utilise une [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans la classe map.

Pour plus d’informations sur l’insertion d’un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée), consultez [multimap::emplace](#emplace) et [multimap::emplace_hint](#emplace_hint).

### <a name="example"></a>Exemple

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="multimapiterator"></a><a name="iterator"></a> Multimap :: Iterator

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un multimap.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Remarques

Le `iterator` défini par Multimap pointe vers les objets de [Value_type](#value_type), qui sont de type `pair<const Key, Type>` . La valeur de la clé est disponible par l’intermédiaire du premier membre de la paire, et la valeur de l’élément mappé est disponible par l’intermédiaire du deuxième membre de la paire.

Pour déréférencer un `iterator` *ITER* pointant vers un élément d’un multimap, utilisez l' **->** opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `Iter->first` , qui est équivalent à `(*Iter).first` . Pour accéder à la valeur de la référence mappée de l’élément, utilisez `Iter->second` , qui est équivalent à `(*Iter).second` .

Un type `iterator` peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="multimapkey_comp"></a><a name="key_comp"></a> Multimap :: key_comp

Récupère une copie de l’objet de comparaison utilisé pour ordonner les clés dans un multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet de fonction utilisé par un multimap pour ordonner ses éléments.

### <a name="remarks"></a>Remarques

L’objet stocké définit la fonction membre

`bool operator( const Key& x, const Key& y);`

qui retourne true si *x* précède strictement *y* dans l’ordre de tri.

### <a name="example"></a>Exemple

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="multimapkey_compare"></a><a name="key_compare"></a> Multimap :: key_compare

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l’ordre relatif de deux éléments dans le multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarques

`key_compare` est un synonyme du paramètre de modèle `Traits`.

Pour plus d’informations sur `Traits` , consultez la rubrique [multimap, classe](../standard-library/multimap-class.md) .

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_compare`, consultez l’exemple [key_comp](#key_comp).

## <a name="multimapkey_type"></a><a name="key_type"></a> Multimap :: key_type

Type qui décrit l’objet de clé de tri qui constitue chaque élément du multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarques

`key_type` est un synonyme du paramètre de modèle `Key`.

Pour plus d’informations sur `Key`, consultez la section Notes de la rubrique [multimap, classe](../standard-library/multimap-class.md).

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_type`, consultez l’exemple [value_type](#value_type).

## <a name="multimaplower_bound"></a><a name="lower_bound"></a> Multimap :: lower_bound

Retourne un itérateur au premier élément d’un multimap avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Itérateur ou `const_iterator` qui traite l’emplacement d’un élément dans un multimap ayant une clé supérieure ou égale à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le multimap si aucune correspondance n’est trouvée pour la clé.

Si la valeur de retour de `lower_bound` est assignée à un `const_iterator` , l’objet Multimap ne peut pas être modifié. Si la valeur de retour de `lower_bound` est affectée à un **iterator**, l’objet multimap peut être changé.

### <a name="example"></a>Exemple

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="multimapmapped_type"></a><a name="mapped_type"></a> Multimap :: mapped_type

Type qui représente le type de données stockées dans un multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Remarques

`mapped_type` est un synonyme du paramètre de modèle `Type`.

Pour plus d’informations sur `Type` , consultez la rubrique [multimap, classe](../standard-library/multimap-class.md) .

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_type`, consultez l’exemple [value_type](#value_type).

## <a name="multimapmax_size"></a><a name="max_size"></a> Multimap :: max_size

Retourne la longueur maximale du multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur maximale autorisée du multimap.

### <a name="example"></a>Exemple

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimapmultimap"></a><a name="multimap"></a> Multimap :: Multimap

Construit un multimap vide ou une copie de l’ensemble ou d’une partie d’un autre multimap.

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

*&*\
Classe d’allocateur de stockage à utiliser pour cet objet multimap, qui est par défaut Allocator.

*Conformes*\
Fonction de comparaison de type `constTraits` utilisée pour ordonner les éléments dans la classe map (par défaut, `Traits`).

*Oui*\
Classe map dont l’ensemble construit doit être une copie.

*Premier*\
Position du premier élément de la plage d'éléments à copier.

*Famille*\
Position du premier élément au-delà de la plage d'éléments à copier.

*IList*\
Initializer_list depuis laquelle copier les éléments.

### <a name="remarks"></a>Remarques

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du multimap et peut être retourné ultérieurement en appelant [get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe, et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leur multimap.

Tous les constructeurs stockent un objet de fonction de type `Traits`, qui est utilisé pour établir un ordre parmi les clés du multimap et qui peut être retourné ultérieurement en appelant [key_comp](#key_comp).

Les trois premiers constructeurs spécifient un Multimap initial vide, le second spécifiant le type de fonction de comparaison (*COMP*) à utiliser pour établir l’ordre des éléments et le troisième spécifie explicitement le type d’allocateur (*al*) à utiliser. Le mot clé **`explicit`** supprime certains genres de conversion de type automatique.

Le quatrième constructeur spécifie une copie du *droit*Multimap.

Le cinquième constructeur spécifie une copie du Multimap en déplaçant vers la *droite*.

Les constructeurs 6ème, 7 et 8 copient les membres d’un initializer_list.

Les trois constructeurs suivants copient la plage `[First, Last)` d’une classe map avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison de la classe `Traits` et de l’allocateur.

### <a name="example"></a>Exemple

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of greater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}
```

## <a name="multimapoperator"></a><a name="op_eq"></a> Multimap :: Operator =

Remplace les éléments d’un multimap par une copie d’un autre multimap.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
[multimap](../standard-library/multimap-class.md) copié dans le `multimap`.

### <a name="remarks"></a>Remarques

Après l’effacement des éléments existants dans un `multimap` , `operator=` copie ou déplace le contenu de *droite* dans le `multimap` .

### <a name="example"></a>Exemple

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

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

## <a name="multimappointer"></a><a name="pointer"></a> Multimap ::p ointer

Type qui fournit un pointeur vers un élément d’un multimap.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Remarques

Un type `pointer` peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet multimap.

## <a name="multimaprbegin"></a><a name="rbegin"></a> Multimap :: rbegin

Retourne un itérateur traitant le premier élément d’un multimap inversé.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé traitant le premier élément d’un multimap inversé ou traitant ce qui était le dernier élément du multimap non inversé.

### <a name="remarks"></a>Remarques

`rbegin` est utilisé avec un multimap inversé comme [begin](#begin) est utilisé avec un multimap.

Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator` , l’objet Multimap ne peut pas être modifié. Si la valeur de retour de `rbegin` est affectée à un `reverse_iterator`, l’objet multimap peut être changé.

Vous pouvez utiliser `rbegin` pour itérer un multimap vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="multimapreference"></a><a name="reference"></a> Multimap :: Reference

Type qui fournit une référence à un élément stocké dans un multimap.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Exemple

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="multimaprend"></a><a name="rend"></a> Multimap :: rend

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un multimap inversé.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un multimap inversé (emplacement qui précédait le premier élément du multimap non inversé).

### <a name="remarks"></a>Remarques

`rend` est utilisé avec un multimap inversé comme [end](../standard-library/map-class.md#end) est utilisé avec un multimap.

Si la valeur de retour de `rend` est assignée à un `const_reverse_iterator` , l’objet Multimap ne peut pas être modifié. Si la valeur de retour de `rend` est affectée à un `reverse_iterator`, l’objet multimap peut être changé.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son multimap.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="multimapreverse_iterator"></a><a name="reverse_iterator"></a> Multimap :: reverse_iterator

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier un élément d’un multimap inversé.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `reverse_iterator` est utilisé pour itérer au sein du Multimap en sens inverse.

Le `reverse_iterator` défini par Multimap pointe vers les objets de [Value_type](#value_type), qui sont de type `pair<const Key, Type>` . La valeur de la clé est disponible par l’intermédiaire du premier membre de la paire, et la valeur de l’élément mappé est disponible par l’intermédiaire du deuxième membre de la paire.

Pour déréférencer un `reverse_iterator` *Sprite* pointant vers un élément d’un multimap, utilisez l' **->** opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `rIter->first` , qui est équivalent à `(*rIter).first` . Pour accéder à la valeur de la référence mappée de l’élément, utilisez `rIter->second` , qui est équivalent à `(*rIter).second` .

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="multimapsize"></a><a name="size"></a> Multimap :: Size

Retourne le nombre d'éléments dans le multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur actuelle du multimap.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre multimap::size.

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="multimapsize_type"></a><a name="size_type"></a> Multimap :: size_type

Type entier non signé qui compte le nombre d’éléments d’un multimap.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).

## <a name="multimapswap"></a><a name="swap"></a> Multimap :: swap

Échange les éléments de deux multimaps.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Multimap qui fournit les éléments à échanger ou multimap dont les éléments doivent être échangés avec ceux du multimap `left`.

### <a name="remarks"></a>Remarques

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux multimaps dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="multimapupper_bound"></a><a name="upper_bound"></a> Multimap :: upper_bound

Retourne un itérateur au premier élément d’un multimap avec une valeur de clé supérieure à celle de la clé spécifiée.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Iterateur ou `const_iterator` qui traite l’emplacement d’un élément dans un multimap ayant une clé supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le multimap si aucune correspondance n’est trouvée pour la clé.

Si la valeur de retour est assignée à `const_iterator` , l’objet Multimap ne peut pas être modifié. Si la valeur de retour est assignée à `iterator` , l’objet Multimap peut être modifié.

### <a name="example"></a>Exemple

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="multimapvalue_comp"></a><a name="value_comp"></a> Multimap :: value_comp

La fonction membre retourne un objet de fonction qui détermine l’ordre des éléments d’un multimap en comparant leurs valeurs de clés.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet de fonction de comparaison utilisé par un multimap pour ordonner ses éléments.

### <a name="remarks"></a>Remarques

Pour un Multimap *m*, si deux éléments *E1*(*K1*, *D1*) et *E2*(*K2*, *D2*) sont des objets de type `value_type` , où *K1* et *K2* sont leurs clés de type `key_type` et *D1* et *D2* sont leurs données de type, et `mapped_type` `m.value_comp(e1, e2)` est équivalent à `m.key_comp(k1, k2)` .

### <a name="example"></a>Exemple

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="multimapvalue_type"></a><a name="value_type"></a> Multimap :: value_type

Type qui représente le type d’objet stocké en tant qu’élément dans une classe map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Exemple

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Voir aussi

[Recipie](./stl-containers.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
