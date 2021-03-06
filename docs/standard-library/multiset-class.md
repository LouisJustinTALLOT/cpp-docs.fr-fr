---
title: multiset, classe
description: Référence d’API pour la classe C++ Standard Template Library (STL) `multiset` , qui est utilisée pour le stockage et la récupération des données d’une collection dans laquelle les valeurs des éléments contenus n’ont pas besoin d’être uniques et dans lesquelles elles servent de valeurs de clés en fonction desquelles les données sont automatiquement triées.
ms.date: 9/9/2020
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::contains
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], contains
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
ms.openlocfilehash: cf7f071ab98cb872537af076b89e0a1b07a1a6a1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505876"
---
# <a name="multiset-class"></a>multiset, classe

La classe multiset de la bibliothèque standard C++ est utilisée pour le stockage et la récupération des données d’une collection dans laquelle les valeurs des éléments n’ont pas besoin d’être uniques, et où ces dernières servent de valeurs de clés en fonction desquelles les données sont automatiquement triées. La valeur de clé d’un élément dans un `multiset` ne peut pas être modifiée directement. En effet, les anciennes valeurs doivent être supprimées et les éléments ayant une nouvelle valeur doivent être insérés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>Paramètres

*Essentiel*\
Type de données d'élément à stocker dans le `multiset`.

*Compar*\
Type qui fournit un objet de fonction qui peut comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif dans le `multiset` . Le prédicat binaire **moins** \<Key> est la valeur par défaut.

En C++ 14, vous pouvez activer la recherche hétérogène en spécifiant le `std::less<>` `std::greater<>` prédicat ou qui n’a aucun paramètre de type. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers) .

*Allocateur*\
Type qui représente l’objet allocateur stocké qui encapsule des détails sur l' `multiset` allocation et la désallocation de mémoire de. La valeur par défaut est `allocator<Key>`.

## <a name="remarks"></a>Remarques

La classe de la bibliothèque standard C++ `multiset` est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée.

- Réversible, car elle fournit des itérateurs bidirectionnels pour accéder à ses éléments.

- Triée, car les éléments sont classés par valeur de clé au sein du conteneur, selon une fonction de comparaison spécifiée.

- Plusieurs dans le sens où il n’est pas nécessaire que ses éléments aient des clés uniques, de sorte qu’une valeur de clé peut avoir plusieurs valeurs d’élément associées.

- Un conteneur associatif simple, car les valeurs de ses éléments sont ses valeurs de clés.

- Un modèle de classe, parce que la fonctionnalité qu’il fournit est générique et donc indépendante du type spécifique des données contenues comme éléments. Le type de données à utiliser est spécifié comme paramètre dans le modèle de la classe, avec la fonction de comparaison et l'allocateur.

L’itérateur fourni par la `multiset` classe est un itérateur bidirectionnel, mais les fonctions membres de classe [Insert](#insert) et [multijeu](#multiset) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les spécifications de fonctionnalités sont minimales par rapport à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre ensemble de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s’agit d’un jeu minimal de fonctionnalités, mais c’est suffisant pour pouvoir parler de plage d’itérateurs [ `First`, `Last`) dans le contexte des fonctions membres de la classe.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces, en les faisant dans un temps qui est en moyenne proportionnel au logarithme du nombre d’éléments dans le conteneur. L’insertion d’éléments n’invalide aucun itérateur, et la suppression d’éléments n’invalide que les itérateurs qui avaient pointé sur les éléments supprimés.

Le `multiset` doit être le conteneur associatif de Choice lorsque les conditions associant les valeurs à leurs clés sont satisfaites par l’application. Les éléments d’un `multiset` peuvent être multiples et servir leurs propres clés de tri, de sorte que les clés ne sont pas uniques. Pour ce type de structure, il peut s'agir d'une liste triée de mots qui peuvent apparaître plusieurs fois. Si les occurrences multiples de mots ne sont pas autorisées, c'est un ensemble qu'il convient d'utiliser comme structure de conteneur. Si des définitions uniques sont jointes en tant que valeurs à la liste de mots clés uniques, c'est une classe map qu'il convient d'utiliser comme structure pour la contenance des données. Si, à la place, les définitions n’étaient pas uniques, un `multimap` serait le conteneur de choix.

Le `multiset` ordonne la séquence qu’il contrôle en appelant un objet de fonction stocké de type *compare*. Cet objet stocké est une fonction de comparaison à laquelle il est possible d’accéder en appelant la fonction membre [key_comp](#key_comp). En général, les éléments doivent être simplement moins comparables pour établir cet ordre : de sorte que, en fonction de deux éléments quelconques, il peut être déterminé soit qu’ils sont équivalents (dans le sens où ni l’un ni l’autre n’est inférieur à l’autre), soit que l’un est inférieur à l’autre. Cela entraîne le tri des éléments non équivalents. D’un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire *f*(*x*, *y*) est un objet de fonction qui a deux objets d’argument *x* et *y* et une valeur de retour de **`true`** ou **`false`** . Un tri appliqué à un ensemble est un ordre faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l’équivalence est transitive, où deux objets x et y sont définis comme équivalents lorsque *f*(*x, y*) et *f*(*y, x*) ont la valeur false. Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

En C++ 14, vous pouvez activer la recherche hétérogène en spécifiant le `std::less<>` `std::greater<>` prédicat ou qui n’a aucun paramètre de type. Pour plus d’informations, consultez [recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers) .

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[ensemble](#multiset)|Construit un `multiset` vide ou une copie de l'ensemble ou d'une partie d'un `multiset` spécifié.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Typedef pour la classe `allocator` de l'objet `multiset`.|
|[const_iterator](#const_iterator)|Typedef pour un itérateur bidirectionnel qui peut lire un **`const`** élément dans le `multiset` .|
|[const_pointer](#const_pointer)|Typedef pour un pointeur vers un **`const`** élément dans un `multiset` .|
|[const_reference](#const_reference)|Typedef pour une référence à un **`const`** élément stocké dans un `multiset` pour la lecture et l’opération **`const`** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typedef pour un itérateur bidirectionnel qui peut lire n’importe quel **`const`** élément dans `multiset` .|
|[difference_type](#difference_type)|Typedef entier signé pour le nombre d'éléments d'un `multiset` compris dans une plage d'éléments pointés par des itérateurs.|
|[répétiteur](#iterator)|Typedef pour un itérateur bidirectionnel qui permet de lire ou de modifier tout élément d'un `multiset`.|
|[key_compare](#key_compare)|Typedef pour un objet de fonction qui peut comparer deux clés pour déterminer l'ordre relatif de deux éléments d'un `multiset`.|
|[key_type](#key_type)|Typedef pour un objet de fonction qui peut comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments d'un `multiset`.|
|[dirigé](#pointer)|Typedef pour un pointeur vers un élément d'un `multiset`.|
|[reference](#reference)|Typedef pour une référence à un élément stocké dans un `multiset`.|
|[reverse_iterator](#reverse_iterator)|Typedef pour un itérateur bidirectionnel qui permet de lire ou de modifier un élément d'un `multiset` inversé.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `multiset`.|
|[value_compare](#value_compare)|Typedef pour un objet de fonction qui peut comparer deux éléments en tant que clés de tri pour déterminer leur ordre relatif au sein d'un `multiset`.|
|[value_type](#value_type)|Typedef qui décrit un objet stocké en tant qu'élément comme un `multiset` par sa capacité en tant que valeur.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[commencer](#begin)|Retourne un itérateur qui pointe vers le premier élément d'un `multiset`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `multiset`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `multiset`.|
|[clear](#clear)|Efface tous les éléments d'un `multiset`.|
|[contient](#contains)<sup>c++ 20</sup>|Vérifiez s’il existe un élément avec la clé spécifiée dans le `multiset` .|
|[count](#count)|Retourne le nombre d'éléments d'un `multiset` dont la clé correspond à celle spécifiée en tant que paramètre.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un `multiset` inversé.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `multiset` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `multiset`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `multiset`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `multiset` est vide.|
|[end](#end)|Retourne un itérateur qui pointe vers l'emplacement situé après le dernier élément d'un `multiset`.|
|[equal_range](#equal_range)|Retourne une paire d'itérateurs. Le premier itérateur de la paire pointe vers le premier élément d'un `multiset` avec une clé qui est supérieure à celle spécifiée. Le deuxième itérateur de la paire pointe vers le premier élément du `multiset` avec une clé dont la valeur est supérieure ou égale à la clé spécifiée.|
|[erase](#erase)|Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un `multiset` ou supprime les éléments qui correspondent à une clé spécifiée.|
|[find](#find)|Retourne un itérateur qui pointe vers le premier emplacement d'un élément d'un `multiset` dont la clé est égale à la clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` qui est utilisé pour construire le `multiset`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans un `multiset`.|
|[key_comp](#key_comp)|Fournit un objet de fonction qui peut comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments d'un `multiset`.|
|[lower_bound](#lower_bound)|Retourne un itérateur au premier élément d'un `multiset` avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `multiset`.|
|[rbegin](#rbegin)|Retourne un itérateur qui pointe vers le premier élément d'un `multiset` inversé.|
|[rend](#rend)|Retourne un itérateur qui pointe vers l'emplacement situé après le dernier élément d'un `multiset` inversé.|
|[size](#size)|Retourne le nombre d'éléments contenus dans un `multiset`.|
|[swap](#swap)|Échange les éléments de deux `multiset`.|
|[upper_bound](#upper_bound)|Retourne un itérateur au premier élément d'un `multiset` avec une valeur de clé supérieure à celle de la clé spécifiée.|
|[value_comp](#value_comp)|Récupère une copie de l'objet de comparaison utilisé pour trier les valeurs d'éléments dans un `multiset`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Remplace les éléments d'un `multiset` par une copie d'un autre `multiset`.|

## <a name="requirements"></a>Configuration requise

**En-tête :**\<set>

**Espace de noms :** std

## <a name="multisetallocator_type"></a><a name="allocator_type"></a> multijeu :: allocator_type

Type qui représente la classe allocator pour l’objet multiset.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Remarques

`allocator_type` est un synonyme du paramètre de modèle `Allocator`.

Pour plus d’informations sur `Allocator`, consultez la section Notes de la rubrique [multiset, classe](../standard-library/multiset-class.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `allocator_type`, consultez l’exemple relatif à [get_allocator](#get_allocator).

## <a name="multisetbegin"></a><a name="begin"></a> multijeu :: Begin

Retourne un itérateur qui traite le premier élément du multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel qui traite le premier élément du multiset ou l’emplacement qui suit un multiset vide.

### <a name="example"></a>Exemple

```cpp
// multiset_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::const_iterator ms1_cIter;

   ms1.insert( 1 );
   ms1.insert( 2 );
   ms1.insert( 3 );

   ms1_Iter = ms1.begin( );
   cout << "The first element of ms1 is " << *ms1_Iter << endl;

   ms1_Iter = ms1.begin( );
   ms1.erase( ms1_Iter );

   // The following 2 lines would err as the iterator is const
   // ms1_cIter = ms1.begin( );
   // ms1.erase( ms1_cIter );

   ms1_cIter = ms1.begin( );
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;
}
```

```Output
The first element of ms1 is 1
The first element of ms1 is now 2
```

## <a name="multisetcbegin"></a><a name="cbegin"></a> multijeu :: cbegin

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

## <a name="multisetcend"></a><a name="cend"></a> multijeu :: CEND

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

## <a name="multisetclear"></a><a name="clear"></a> multijeu :: Clear

Efface tous les éléments d’un multiset.

```cpp
void clear();
```

### <a name="example"></a>Exemple

```cpp
// multiset_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 1 );
   ms1.insert( 2 );

   cout << "The size of the multiset is initially "
        << ms1.size( ) << "." << endl;

   ms1.clear( );
   cout << "The size of the multiset after clearing is "
        << ms1.size( ) << "." << endl;
}
```

```Output
The size of the multiset is initially 2.
The size of the multiset after clearing is 0.
```

## <a name="multisetconst_iterator"></a><a name="const_iterator"></a> multijeu :: const_iterator

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément dans le multiensemble.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_iterator` ne peut pas être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `const_iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="multisetconst_pointer"></a><a name="const_pointer"></a> multijeu :: const_pointer

Type qui fournit un pointeur vers un **`const`** élément dans un multiensemble.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarques

Un type `const_pointer` ne peut pas être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet multiset.

## <a name="multisetconst_reference"></a><a name="const_reference"></a> multijeu :: const_reference

Type qui fournit une référence à un **`const`** élément stocké dans un multiensemble pour la lecture et l’opération **`const`** .

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Exemple

```cpp
// multiset_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference can't be used to modify the multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> multijeu :: const_reverse_iterator

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément du multiensemble.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_reverse_iterator` ne peut pas modifier la valeur d’un élément et est utilisé pour itérer au sein du multiensemble en sens inverse.

### <a name="example"></a>Exemple

Consultez l’exemple [rend](#rend) pour savoir comment déclarer et utiliser le type `const_reverse_iterator`.

## <a name="multisetcontains"></a><a name="contains"></a> multijeu :: Contains

Vérifiez s’il existe un élément avec la clé spécifiée dans le `multiset` .

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
#include <set>
#include <iostream>

int main()
{
    std::multiset<int> theMultiSet = {1, 2};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theMultiSet.contains(2) << '\n';
    std::cout << theMultiSet.contains(3) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="multisetcount"></a><a name="count"></a> multijeu :: Count

Retourne le nombre d'éléments d'un multiset dont la clé correspond à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé des éléments à mettre en correspondance à partir du multiset.

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments du multiset dont la clé de tri correspond à la clé de paramètre.

### <a name="remarks"></a>Remarques

La fonction membre retourne le nombre d’éléments *x* dans la plage

\[ lower_bound (*clé*), upper_bound (*clé*))

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre multiset::count.

```cpp
// multiset_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    multiset<int> ms1;
    multiset<int>::size_type i;

    ms1.insert(1);
    ms1.insert(1);
    ms1.insert(2);

    // Elements don't need to be unique in multiset,
    // so duplicates are allowed and counted.
    i = ms1.count(1);
    cout << "The number of elements in ms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = ms1.count(2);
    cout << "The number of elements in ms1 with a sort key of 2 is: "
         << i << "." << endl;

    i = ms1.count(3);
    cout << "The number of elements in ms1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in ms1 with a sort key of 1 is: 2.
The number of elements in ms1 with a sort key of 2 is: 1.
The number of elements in ms1 with a sort key of 3 is: 0.
```

## <a name="multisetcrbegin"></a><a name="crbegin"></a> multijeu :: crbegin

Retourne un itérateur const qui traite le premier élément d’un multiset inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé const qui traite le premier élément d’un multiset inversé (ou qui traite ce qui a été le dernier élément du multiset non inversé).

### <a name="remarks"></a>Remarques

`crbegin` est utilisé avec un multiset inversé comme begin est utilisé avec un multiset.

Avec la valeur de retour `crbegin` , l’objet de multiensemble ne peut pas être modifié.

Vous pouvez utiliser `crbegin` pour itérer un multiset vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// multiset_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

```Output
The first element in the reversed multiset is 30.
```

## <a name="multisetcrend"></a><a name="crend"></a> multijeu :: crend

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un multiset inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un multiset inversé (emplacement qui précédait celui du premier élément du multiset non inversé).

### <a name="remarks"></a>Remarques

`crend` est utilisé avec un multiset inversé comme [end](#end) est utilisé avec un multiset.

Avec la valeur de retour `crend` , l’objet de multiensemble ne peut pas être modifié.

Vous pouvez utiliser `crend` pour déterminer si un itérateur inversé a atteint la fin de son multiset.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// multiset_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crend( ) ;
   ms1_crIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

## <a name="multisetdifference_type"></a><a name="difference_type"></a> multiensemble ::d ifference_type

Type entier signé qui peut être utilisé pour représenter le nombre d’éléments d’un multiset au sein d’une plage, parmi les éléments pointés par les itérateurs.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Remarques

`difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type` est généralement utilisé pour représenter le nombre d’éléments de la plage [ `first`, `last`) entre les itérateurs `first` et `last`. Il inclut l’élément vers lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) vers lequel pointe `last`.

Bien que `difference_type` soit disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui comprend la classe des itérateurs bidirectionnels pris en charge par les conteneurs réversibles tels que Set, la soustraction entre les itérateurs est prise en charge uniquement par les itérateurs à accès aléatoire fournis par un conteneur à accès aléatoire comme Vector.

### <a name="example"></a>Exemple

```cpp
// multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;

   ms1.insert( 20 );
   ms1.insert( 10 );
   ms1.insert( 20 );

   ms1_bIter = ms1.begin( );
   ms1_eIter = ms1.end( );

   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );

   // The keys, and hence the elements, of a multiset aren't unique
   cout << "The number '5' occurs " << df_typ5
        << " times in multiset ms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in multiset ms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in multiset ms1.\n";

   // Count the number of elements in a multiset
   multiset <int>::difference_type  df_count = 0;
   ms1_Iter = ms1.begin( );
   while ( ms1_Iter != ms1_eIter)
   {
      df_count++;
      ms1_Iter++;
   }

   cout << "The number of elements in the multiset ms1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in multiset ms1.
The number '10' occurs 1 times in multiset ms1.
The number '20' occurs 2 times in multiset ms1.
The number of elements in the multiset ms1 is: 3.
```

## <a name="multisetemplace"></a><a name="emplace"></a> multijeu :: emplace

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée) avec un hint d’emplacement.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Arguments transférés pour construire un élément à insérer dans le multiset.

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’élément qui vient d’être inséré.

### <a name="remarks"></a>Remarques

Aucune référence aux éléments de conteneur n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Pendant l’emplacement, si une exception est levée, l’état du conteneur n’est pas modifié.

### <a name="example"></a>Exemple

```cpp
// multiset_emplace.cpp
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
    multiset<string> s1;

    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;

    s1.emplace("Bob");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="multisetemplace_hint"></a><a name="emplace_hint"></a> multijeu :: emplace_hint

Insère un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée) avec un hint d’emplacement.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

*attend*\
Arguments transférés pour construire un élément à insérer dans le multiset.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement *, l'* insertion peut se produire dans le temps constant amorti plutôt que dans le temps logarithmique.)

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’élément qui vient d’être inséré.

### <a name="remarks"></a>Remarques

Aucune référence aux éléments de conteneur n’est invalidée par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Pendant l’emplacement, si une exception est levée, l’état du conteneur n’est pas modifié.

Pour obtenir un exemple de code, consultez [set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="multisetempty"></a><a name="empty"></a> multijeu :: Empty

Teste si un multiset est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le multiensemble est vide ; **`false`** si le multiensemble n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// multiset_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
   using namespace std;
   multiset <int> ms1, ms2;
   ms1.insert ( 1 );

   if ( ms1.empty( ) )
      cout << "The multiset ms1 is empty." << endl;
   else
      cout << "The multiset ms1 is not empty." << endl;

   if ( ms2.empty( ) )
      cout << "The multiset ms2 is empty." << endl;
   else
      cout << "The multiset ms2 is not empty." << endl;
}
```

```Output
The multiset ms1 is not empty.
The multiset ms2 is empty.
```

## <a name="multisetend"></a><a name="end"></a> multijeu :: end

Retourne l'itérateur past-the-end.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur de type past-the-end. Si le multiensemble est vide, puis `multiset::end() == multiset::begin()`.

### <a name="remarks"></a>Remarques

**end** est utilisé pour déterminer si un itérateur a dépassé la fin de son multiset.

La valeur retournée par **end** ne doit pas être déréférencée.

Pour obtenir un exemple de code, consultez [multiset::find](#find).

## <a name="multisetequal_range"></a><a name="equal_range"></a> multijeu :: equal_range

Retourne une paire d’itérateurs, respectivement au premier élément d’un multiset ayant une clé supérieure à celle spécifiée et au premier élément d’un multiset ayant une clé supérieure ou égale à la clé spécifiée.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Paire d’itérateurs telle que le premier est la [lower_bound](#lower_bound) de la clé et le second est la [upper_bound](#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **tout d’abord**, et pour déréférencer l’itérateur de la limite inférieure, utilisez \* ( `pr` . **tout d’abord**). Pour accéder au second itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **Deuxièmement**, et pour déréférencer l’itérateur de la limite supérieure, utilisez \* ( `pr` . **seconde**).

### <a name="example"></a>Exemple

```cpp
// multiset_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multiset<int, less<int> > IntSet;
   IntSet ms1;
   multiset <int> :: const_iterator ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = ms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.second ) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.first ) << "." << endl;

   // Compare the upper_bound called directly
   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *ms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = ms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key less than 40." << endl;
   else
      cout << "The element of multiset ms1 with a key >= 40 is: "
                << *( p1.first ) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The multiset ms1 doesn't have an element with a key less than 40.
```

## <a name="multiseterase"></a><a name="erase"></a> multijeu :: Erase

Supprime d’un emplacement spécifié un élément ou une plage d’éléments compris dans un multiset ou supprime les éléments qui correspondent à une clé spécifiée.

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

Pour les deux premières fonctions membres, itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou élément à la fin du multiset si aucun élément de ce type n’existe.

Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés du multiset.

### <a name="remarks"></a>Remarques

Pour obtenir un exemple de code, consultez [set::erase](../standard-library/set-class.md#erase).

## <a name="multisetfind"></a><a name="find"></a> multijeu :: find

Retourne un itérateur qui fait référence à l'emplacement d'un élément dans un multiensemble ayant une clé équivalente à la clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé qui doit correspondre à la clé de tri d'un élément du multiensemble dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui fait référence à l’emplacement d’un élément ayant la clé spécifiée, ou emplacement qui suit le dernier élément du multiset ( `multiset::end()`), si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Remarques

La fonction membre retourne un itérateur qui fait référence à un élément du multiensemble dont la clé est équivalente à la *clé* d’argument sous un prédicat binaire qui induit un classement basé sur une relation d’infériorité.

Si la valeur de retour de `find` est assignée à un `const_iterator` , l’objet de multiensemble ne peut pas être modifié. Si la valeur de retour de `find` est assignée à `iterator` , l’objet de multiensemble peut être modifié

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
    multiset<int> s1({ 40, 45 });
    cout << "The starting multiset s1 is: " << endl;
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

    cout << "The modified multiset s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="multisetget_allocator"></a><a name="get_allocator"></a> multijeu :: get_allocator

Retourne une copie de l’objet allocateur utilisé pour construire le multiset.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur renvoyée

Allocateur utilisé par le multiset.

### <a name="remarks"></a>Remarques

Les allocateurs de la classe multiset spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// multiset_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int>::allocator_type ms1_Alloc;
   multiset <int>::allocator_type ms2_Alloc;
   multiset <double>::allocator_type ms3_Alloc;
   multiset <int>::allocator_type ms4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multiset <int> ms1;
   multiset <int, allocator<int> > ms2;
   multiset <double, allocator<double> > ms3;

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms3.max_size( ) <<  "." << endl;

   // The following lines create a multiset ms4
   // with the allocator of multiset ms1
   ms1_Alloc = ms1.get_allocator( );
   multiset <int> ms4( less<int>( ), ms1_Alloc );
   ms4_Alloc = ms4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( ms1_Alloc == ms4_Alloc )
   {
      cout << "Allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "Allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multisetinsert"></a><a name="insert"></a> multijeu :: Insert

Insère un élément ou une plage d'éléments dans une classe multiset.

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
Valeur d'un élément à insérer dans la classe multiset.

*Cela*\
Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement *, l'* insertion peut se produire dans le temps constant amorti plutôt que dans le temps logarithmique.)

*ValTy*\
Paramètre de modèle qui spécifie le type d’argument que le multiensemble peut utiliser pour construire un élément de [Value_type](../standard-library/map-class.md#value_type), et fait avancer la valeur *Val* comme argument.

*Premier*\
Position du premier élément à copier.

*Famille*\
Position juste au-delà du dernier élément à copier.

*InputIterator*\
Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](../standard-library/map-class.md#value_type).

*IList*\
[Initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.

### <a name="return-value"></a>Valeur renvoyée

Les fonctions membres d'insertion à un élément, (1) et (2), retournent un itérateur vers l'emplacement où le nouvel élément a été inséré dans la classe multiset.

Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe vers l'emplacement où le nouvel élément a été inséré dans la classe multiset.

### <a name="remarks"></a>Remarques

Aucun pointeur ou référence n'est invalidé par cette fonction, mais elle peut invalider tous les itérateurs du conteneur.

Pendant l’insertion d’un seul élément, si une exception est levée, l’état du conteneur n’est pas modifié. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.

Le [value_type](../standard-library/map-class.md#value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe set, `multiset<V>::value_type` est du type `const V`.

La fonction membre de plage (5) insère la séquence de valeurs d'éléments dans une classe multiset qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; ainsi, `Last` n'est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `s.insert(v.begin(), v.end());` insère tous les éléments de `v` dans `s`.

La fonction membre de liste d’initialiseurs (6) utilise une [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans le multiset.

Pour plus d’informations sur l’insertion d’un élément construit sur place (aucune opération de copie ou déplacement n’est effectuée), consultez [multiset::emplace](#emplace) et [multiset::emplace_hint](#emplace_hint).

### <a name="example"></a>Exemple

```cpp
// multiset_insert.cpp
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
    multiset<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original multiset values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    s1.insert(1);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multiset<int> s2;
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

    cout << "The modified multiset values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    multiset<string>  s3;
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

    multiset<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="multisetiterator"></a><a name="iterator"></a> multijeu :: Iterator

Type qui fournit un [itérateur bidirectionnel](../standard-library/bidirectional-iterator-tag-struct.md) constant capable de lire un élément dans un multiset.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [Begin](#begin) pour obtenir un exemple de la façon de déclarer et d’utiliser un `iterator` .

## <a name="multisetkey_comp"></a><a name="key_comp"></a> multijeu :: key_comp

Récupère une copie de l’objet de comparaison utilisé pour ordonner les clés dans un multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet de fonction utilisé par un multiset pour ordonner ses éléments, qui est le paramètre de modèle `Compare`.

Pour plus d’informations sur `Compare`, consultez la section Notes de la rubrique [multiset, classe](../standard-library/multiset-class.md).

### <a name="remarks"></a>Remarques

L’objet stocké définit la fonction membre :

**bool operator**( **const Key&** *x*, **const Key&** *y*);

qui retourne true si *x* précède strictement *y* dans l’ordre de tri.

[Key_compare](#key_compare) et [value_compare](#value_compare) sont des synonymes du paramètre de modèle `Compare` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// multiset_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;
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
           << "where kc1 is the function object of ms1."
           << endl;
   }

   multiset <int, greater<int> > ms2;
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.
```

## <a name="multisetkey_compare"></a><a name="key_compare"></a> multijeu :: key_compare

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l’ordre relatif de deux éléments dans le multiset.

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>Remarques

`key_compare` est un synonyme du paramètre de modèle `Compare`.

Pour plus d’informations sur `Compare`, consultez la section Notes de la rubrique [multiset, classe](../standard-library/multiset-class.md).

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_compare`, consultez l’exemple [key_comp](#key_comp).

## <a name="multisetkey_type"></a><a name="key_type"></a> multijeu :: key_type

Type qui fournit un objet de fonction pouvant comparer des clés de tri pour déterminer l’ordre relatif de deux éléments dans le multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarques

`key_type` est un synonyme du paramètre de modèle `Key`.

Pour plus d’informations sur `Key`, consultez la section Notes de la rubrique [multiset, classe](../standard-library/multiset-class.md).

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_type`, consultez l’exemple [value_type](#value_type).

## <a name="multisetlower_bound"></a><a name="lower_bound"></a> multijeu :: lower_bound

Retourne un itérateur au premier élément d’un multiset avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

`iterator`Ou `const_iterator` qui traite l’emplacement d’un élément dans un multiensemble qui a une clé supérieure ou égale à la clé d’argument, ou qui traite l’emplacement qui suit le dernier élément du multiensemble si aucune correspondance n’est trouvée pour la clé.

### <a name="example"></a>Exemple

```cpp
// multiset_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.lower_bound( 20 );
   cout << "The element of multiset ms1 with a key of 20 is: "
        << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of multiset ms1 with a key of 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.end( );
   ms1_AcIter--;
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );
   cout << "The element of ms1 with a key matching "
        << "that of the last element is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The element of multiset ms1 with a key of 20 is: 20.
The multiset ms1 doesn't have an element with a key of 40.
The element of ms1 with a key matching that of the last element is: 30.
```

## <a name="multisetmax_size"></a><a name="max_size"></a> multijeu :: max_size

Retourne la longueur maximale du multiset.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur maximale autorisée du multiset.

### <a name="example"></a>Exemple

```cpp
// multiset_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::size_type i;

   i = ms1.max_size( );
   cout << "The maximum possible length "
        << "of the multiset is " << i << "." << endl;
}
```

## <a name="multisetmultiset"></a><a name="multiset"></a> multijeu :: multimultijeu

Construit un multiset vide ou une copie de l’ensemble ou d’une partie d’un autre multiset.

```cpp
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

*&*\
Classe d’allocateur de stockage à utiliser pour cet objet multiset, qui est par défaut `Allocator`.

*Conformes*\
Fonction de comparaison de type `const Compare` utilisée pour ordonner les éléments dans le multiset (par défaut, `Compare`).

*Oui*\
Multiset dont le multiset construit doit être une copie.

*Premier*\
Position du premier élément de la plage d'éléments à copier.

*Famille*\
Position du premier élément au-delà de la plage d'éléments à copier.

*IList*\
Initializer_list depuis laquelle copier les éléments.

### <a name="remarks"></a>Remarques

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du multiset et peut être retourné ultérieurement en appelant [get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe, et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leur multiset.

Tous les constructeurs stockent un objet de fonction de type Compare, qui est utilisé pour établir un ordre parmi les clés du multiset et qui peut être retourné ultérieurement en appelant [key_comp](#key_comp).

Les trois premiers constructeurs spécifient un multiensemble initial vide, le second spécifiant le type de fonction de comparaison (*COMP*) à utiliser pour établir l’ordre des éléments et le troisième spécifie explicitement le type d’allocateur (*al*) à utiliser. Le mot clé **`explicit`** supprime certains genres de conversion de type automatique.

Le quatrième constructeur spécifie une copie du *droit*de multiensemble.

Le cinquième constructeur spécifie une copie du multiensemble en se déplaçant vers la *droite*.

Les constructeurs 6ème, 7 et 8 spécifient un initializer_list à partir duquel les éléments doivent être copiés.

Les trois constructeurs suivants copient la plage `[First, Last)` d’une multiset avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison et de l’allocateur.

### <a name="example"></a>Exemple

```cpp
// multiset_ctor.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;

    // Create an empty multiset ms0 of key type integer
    multiset <int> ms0;

    // Create an empty multiset ms1 with the key comparison
    // function of less than, then insert 4 elements
    multiset <int, less<int> > ms1;
    ms1.insert(10);
    ms1.insert(20);
    ms1.insert(20);
    ms1.insert(40);

    // Create an empty multiset ms2 with the key comparison
    // function of greater than, then insert 2 elements
    multiset <int, less<int> > ms2;
    ms2.insert(10);
    ms2.insert(20);

    // Create a multiset ms3 with the
    // allocator of multiset ms1
    multiset <int>::allocator_type ms1_Alloc;
    ms1_Alloc = ms1.get_allocator();
    multiset <int> ms3(less<int>(), ms1_Alloc);
    ms3.insert(30);

    // Create a copy, multiset ms4, of multiset ms1
    multiset <int> ms4(ms1);

    // Create a multiset ms5 by copying the range ms1[ first,  last)
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;
    ms1_bcIter = ms1.begin();
    ms1_ecIter = ms1.begin();
    ms1_ecIter++;
    ms1_ecIter++;
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);

    // Create a multiset ms6 by copying the range ms4[ first,  last)
    // and with the allocator of multiset ms2
    multiset <int>::allocator_type ms2_Alloc;
    ms2_Alloc = ms2.get_allocator();
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);

    cout << "ms1 =";
    for (auto i : ms1)
        cout << " " << i;
    cout << endl;

    cout << "ms2 =";
    for (auto i : ms2)
        cout << " " << i;
   cout << endl;

   cout << "ms3 =";
   for (auto i : ms3)
       cout << " " << i;
    cout << endl;

    cout << "ms4 =";
    for (auto i : ms4)
        cout << " " << i;
    cout << endl;

    cout << "ms5 =";
    for (auto i : ms5)
        cout << " " << i;
    cout << endl;

    cout << "ms6 =";
    for (auto i : ms6)
        cout << " " << i;
    cout << endl;

    // Create a multiset by moving ms5
    multiset<int> ms7(move(ms5));
    cout << "ms7 =";
    for (auto i : ms7)
        cout << " " << i;
    cout << endl;

    // Create a multiset with an initializer_list
    multiset<int> ms8({1, 2, 3, 4});
    cout << "ms8=";
    for (auto i : ms8)
        cout << " " << i;
    cout << endl;
}
```

## <a name="multisetoperator"></a><a name="op_eq"></a> multijeu :: Operator =

Remplace les éléments de ce `multiset` par les éléments d’un autre `multiset`.

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
`multiset` à partir duquel les éléments sont copiés ou déplacés.

### <a name="remarks"></a>Remarques

`operator=` copie ou déplace les éléments de *droite* dans ce `multiset` , selon le type de référence (lvalue ou rvalue) utilisé. Les éléments qui figurent dans ce `multiset` avant l’exécution de `operator=` sont ignorés.

### <a name="example"></a>Exemple

```cpp
// multiset_operator_as.cpp
// compile with: /EHsc
#include <multiset>
#include <iostream>

int main( )
   {
   using namespace std;
   multiset<int> v1, v2, v3;
   multiset<int>::iterator iter;

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

## <a name="multisetpointer"></a><a name="pointer"></a> multiensemble ::p ointer

Type qui fournit un pointeur vers un élément d’un multiset.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Remarques

Un type **pointer** peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet multiset.

## <a name="multisetrbegin"></a><a name="rbegin"></a> multijeu :: rbegin

Retourne un itérateur ciblant le premier élément d’un multiset inversé.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé ciblant le premier élément d’un multiset inversé ou ciblant ce qui a été le dernier élément du multiset non inversé.

### <a name="remarks"></a>Remarques

`rbegin` est utilisé avec un multiset inversé comme rbegin est utilisé avec un multiset.

Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator` , l’objet de multiensemble ne peut pas être modifié. Si la valeur de retour de `rbegin` est assignée à un `reverse_iterator`, l’objet multiset peut être changé.

Vous pouvez utiliser `rbegin` pour itérer un multiset vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// multiset_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a multiset in a forward order
   cout << "The multiset is:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is:";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << " " << *ms1_rIter;
   cout << endl;

   // A multiset element can be erased by dereferencing to its key
   ms1_rIter = ms1.rbegin( );
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multiset is "<< *ms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed multiset is 30.
The multiset is: 10 20 30
The reversed multiset is: 30 20 10
After the erasure, the first element in the reversed multiset is 20.
```

## <a name="multisetreference"></a><a name="reference"></a> multijeu :: Reference

Type qui fournit une référence à un élément stocké dans un multiset.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Exemple

```cpp
// multiset_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="multisetrend"></a><a name="rend"></a> multijeu :: rend

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un multiset inversé.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un multiset inversé (emplacement qui précédait celui du premier élément du multiset non inversé).

### <a name="remarks"></a>Remarques

`rend` est utilisé avec un multiset inversé comme [end](#end) est utilisé avec un multiset.

Si la valeur de retour de `rend` est assignée à un `const_reverse_iterator` , l’objet de multiensemble ne peut pas être modifié. Si la valeur de retour de `rend` est assignée à un `reverse_iterator`, l’objet multiset peut être changé.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son multiset.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// multiset_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rend( ) ;
   ms1_rIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a multiset in a forward order
   cout << "The multiset is: ";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << *ms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is: ";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << *ms1_rIter << " ";
   cout << "." << endl;

   ms1_rIter = ms1.rend( );
   ms1_rIter--;
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rend( );
   --ms1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed multiset is " << *ms1_rIter << "." << endl;
}
```

## <a name="multisetreverse_iterator"></a><a name="reverse_iterator"></a> multijeu :: reverse_iterator

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier un élément d’un multiset inversé.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `reverse_iterator` est utilisé pour itérer au sein du multiensemble en sens inverse.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="multisetsize"></a><a name="size"></a> multijeu :: Size

Retourne le nombre d’éléments du multiset.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur actuelle du multiset.

### <a name="example"></a>Exemple

```cpp
// multiset_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: size_type i;

   ms1.insert( 1 );
   i = ms1.size( );
   cout << "The multiset length is " << i << "." << endl;

   ms1.insert( 2 );
   i = ms1.size( );
   cout << "The multiset length is now " << i << "." << endl;
}
```

```Output
The multiset length is 1.
The multiset length is now 2.
```

## <a name="multisetsize_type"></a><a name="size_type"></a> multijeu :: size_type

Type entier non signé qui peut représenter le nombre d’éléments d’un multiset.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).

## <a name="multisetswap"></a><a name="swap"></a> multijeu :: swap

Échange les éléments de deux multisets.

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Argument multiset qui fournit les éléments à échanger avec le multiset cible.

### <a name="remarks"></a>Remarques

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux multisets dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// multiset_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2, ms3;
   multiset <int>::iterator ms1_Iter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );
   ms2.insert( 100 );
   ms2.insert( 200 );
   ms3.insert( 300 );

   cout << "The original multiset ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the member function version of swap
   ms1.swap( ms2 );

   cout << "After swapping with ms2, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the specialized template version of swap
   swap( ms1, ms3 );

   cout << "After swapping with ms3, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original multiset ms1 is: 10 20 30.
After swapping with ms2, list ms1 is: 100 200.
After swapping with ms3, list ms1 is: 300.
```

## <a name="multisetupper_bound"></a><a name="upper_bound"></a> multijeu :: upper_bound

Retourne un itérateur au premier élément d’un multiset avec une valeur de clé supérieure à celle de la clé spécifiée.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Clé d’argument à comparer à la clé de tri d’un élément du multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur renvoyée

**iterator** ou `const_iterator` qui traite l’emplacement d’un élément dans un multiset ayant une clé supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le multiset si aucune correspondance n’est trouvée pour la clé.

### <a name="example"></a>Exemple

```cpp
// multiset_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "The first element of multiset ms1 with a key greater "
           << "than 20 is: " << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key greater than 30." << endl;
   else
      cout << "The element of multiset ms1 with a key > 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.begin( );
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );
   cout << "The first element of ms1 with a key greater than"
        << endl << "that of the initial element of ms1 is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The first element of multiset ms1 with a key greater than 20 is: 30.
The multiset ms1 doesn't have an element with a key greater than 30.
The first element of ms1 with a key greater than
that of the initial element of ms1 is: 20.
```

## <a name="multisetvalue_comp"></a><a name="value_comp"></a> multijeu :: value_comp

Récupère une copie de l’objet de comparaison utilisé pour trier les valeurs d’éléments d’un multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet de fonction utilisé par un multiset pour ordonner ses éléments, qui est le paramètre de modèle `Compare`.

Pour plus d’informations sur `Compare`, consultez la section Notes de la rubrique [multiset, classe](../standard-library/multiset-class.md).

### <a name="remarks"></a>Remarques

L’objet stocké définit la fonction membre :

**bool, opérateur**( **&de clé const ** `_xVal` , **clé const&** `_yVal` );

qui retourne true si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

[Key_compare](#key_compare) et [value_compare](#value_compare) sont des synonymes du paramètre de modèle `Compare` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// multiset_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of ms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of ms1."
           << endl;
   }

   set <int, greater<int> > ms2;
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.
```

## <a name="multisetvalue_compare"></a><a name="value_compare"></a> multijeu :: value_compare

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer leur ordre relatif dans le multiset.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Remarques

`value_compare` est un synonyme du paramètre de modèle `Compare`.

Les [key_compare](#key_compare) et `value_compare` sont des synonymes du paramètre de modèle `Compare` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

Pour plus d’informations sur `Compare`, consultez la section Notes de la rubrique [multiset, classe](../standard-library/multiset-class.md).

### <a name="example"></a>Exemple

Consultez l’exemple [value_comp](#value_comp) pour savoir comment déclarer et utiliser `value_compare`.

## <a name="multisetvalue_type"></a><a name="value_type"></a> multijeu :: value_type

Type qui décrit un objet stocké comme élément d’un multiset en sa capacité de valeur.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Remarques

`value_type` est un synonyme du paramètre de modèle `Key`.

Les [KEY_TYPE](#key_type) et `value_type` sont des synonymes du paramètre de modèle `Key` . Les deux types sont fournis pour les classes Set et multijeu, où ils sont identiques, pour la compatibilité avec les classes Map et multimap, où ils sont distincts.

Pour plus d’informations sur `Key`, consultez la section Notes de la rubrique.

### <a name="example"></a>Exemple

```cpp
// multiset_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;

   multiset <int> :: value_type svt_Int;   // Declare value_type
   svt_Int = 10;             // Initialize value_type

   multiset <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   ms1.insert( svt_Int );         // Insert value into s1
   ms1.insert( skt_Int );         // Insert key into s1

   // A multiset accepts key_types or value_types as elements
   cout << "The multiset has elements:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;
}
```

```Output
The multiset has elements: 10 20.
```

## <a name="see-also"></a>Voir aussi

[Recipie](./stl-containers.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
