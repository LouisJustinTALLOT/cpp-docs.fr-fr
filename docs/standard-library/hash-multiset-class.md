---
title: hash_multiset, classe
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: b12c782ff7071987214acfe1ef8c52ca391b25ad
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333561"
---
# <a name="hashmultiset-class"></a>hash_multiset, classe

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

La classe conteneur hash_multiset est une extension de la bibliothèque de classes C++, et elle est utilisée pour le stockage et la récupération rapide des données d’une collection dans laquelle les valeurs des éléments contenus servent de valeurs de clés et ne doivent pas obligatoirement être uniques.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Paramètres

*Key*<br/>
Type de données de l'élément à stocker dans le hash_multiset.

*Caractéristiques*<br/>
Type qui inclut les deux objets de fonction, une de la classe comparer qui est un prédicat binaire capable de comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif et une fonction de hachage qui est un mappage de prédicat unaire les valeurs clés des éléments à non signé entiers de type `size_t`. Cet argument est facultatif et sa valeur par défaut est `hash_compare<Key, less<Key> >`.

*Allocateur*<br/>
Type qui représente l'objet allocateur stocké qui encapsule des informations sur l'allocation et la désallocation de mémoire du hash_multiset. Cet argument est facultatif et sa valeur par défaut est `allocator<Key>`.

## <a name="remarks"></a>Notes

Le hash_multiset est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée. C'est également un conteneur associatif simple, car les valeurs de ses éléments sont ses valeurs de clés.

- Réversible, car elle fournit un itérateur bidirectionnel pour accéder à ses éléments

- Haché, car ses éléments sont regroupés dans des compartiments selon la valeur d'une fonction de hachage appliquée aux valeurs de clé des éléments.

- Unique dans le sens où chacun de ses éléments doit avoir une clé unique. Comme hash_multiset est également un simple conteneur associatif, ses éléments sont également uniques.

- Une classe de modèle, car la fonctionnalité qu'elle fournit est générique et donc indépendante du type spécifique des données contenues comme éléments ou comme clés. Les types de données utilisés pour les éléments et les clés sont eux spécifiés comme paramètres dans la classe de modèle avec la fonction de comparaison et l'allocateur.

Le principal avantage du hachage sur le tri est une meilleure efficacité : un hachage réussi effectue des insertions, des suppressions et trouve ce qui est recherché dans un délai moyen constant, alors que pour les techniques de tri, ce délai est proportionnel au logarithme du nombre d'éléments du conteneur. La valeur d'un élément appartenant à une classe set ne peut pas être modifiée directement. Vous devez supprimer les anciennes valeurs et insérer les éléments ayant de nouvelles valeurs.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs hachés sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces quand elles sont utilisées avec une fonction de hachage bien conçue, car elles les exécutent dans un délai qui est en moyenne constant et ne dépend pas du nombre d'éléments dans le conteneur. Une fonction de hachage bien conçue produit une distribution uniforme des valeurs de hachage et réduit le nombre de collisions, qui se produisent quand des valeurs de clés distinctes sont mappées dans la même valeur de hachage. Dans le pire des cas, avec la pire des fonctions de hachage possible, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (délai linéaire).

Le hash_multiset doit être sélectionné comme conteneur associatif quand les conditions associant les valeurs à leurs clés sont remplies par l'application. Les éléments d'un hash_multiset peuvent être nombreux et être utilisés comme leurs propres clés de tri : les clés ne sont donc pas uniques. Pour ce type de structure, il peut s'agir d'une liste triée de mots qui peuvent apparaître plusieurs fois. Si les occurrences multiples de mots ne sont pas autorisées, c'est un hash_set qu'il convient d'utiliser comme structure de conteneur. Si des définitions uniques sont jointes comme valeurs à la liste de mots clés uniques, c'est un hash_map qu'il convient d'utiliser comme structure pour contenir ces données. Si les définitions ne sont pas uniques, c'est un hash_multimap qu'il convient d'utiliser comme conteneur.

Le hash_multiset ordonne la séquence qu’il contrôle en appelant un objet de caractéristiques de hachage stocké de type [value_compare](#value_compare). Cet objet stocké est accessible en appelant la fonction membre [key_comp](#key_comp). Cet objet de fonction doit se comporter comme un objet de classe `hash_compare<Key, less<Key> >`. En particulier, pour toutes les valeurs *clé* de type `Key`, l’appel `Trait(Key)` génère une distribution des valeurs de type `size_t`.

En général, les éléments ne doivent pas être tout à fait comparables, afin que, à l'aide de deux événements quelconques donnés, il soit possible de déterminer, soit qu'ils soient équivalents (dans le sens où l'un n'est pas inférieur à l'autre), soit que l'un est inférieur à l'autre. Cela entraîne le tri des éléments non équivalents. D'un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire *f*( *x*, *y*) est un objet de fonction qui a deux objets d’arguments x et y, et la valeur de retour true ou false. Un tri appliqué à un hash_multiset est un ordonnancement faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l’équivalence est transitive, où deux objets x et y sont définis comme équivalents quand *f*( *x*, *y*) et *f*( *y*, *x*) ont toutes deux la valeur false. Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction d'ordonnancement et de la taille actuelle de la table de hachage stockée dans l'objet conteneur. Vous ne pouvez pas déterminer la taille actuelle de la table de hachage, et vous ne pouvez donc généralement pas prédire l'ordre des éléments dans la séquence contrôlée. L'insertion d'éléments ne rend aucun itérateur non valide. La suppression d'éléments rend uniquement non valides les itérateurs qui pointaient spécifiquement vers les éléments supprimés.

L’itérateur fourni par la classe hash_multiset est un itérateur bidirectionnel. Toutefois, les fonctions membres de classe insert et hash_multiset ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences des fonctionnalités sont inférieures à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre hash_multiset de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s’agit d’un hash_multiset minimal de fonctionnalités, mais il est suffisant pour pouvoir parler de plage d’itérateurs [`first`, `last`) dans le contexte des fonctions membres de classe.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[hash_multiset](#hash_multiset)|Construit un `hash_multiset` vide ou une copie de l'ensemble ou d'une partie d'un autre `hash_multiset`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet `hash_multiset`.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **const** élément dans le `hash_multiset`.|
|[const_pointer](#const_pointer)|Un type qui fournit un pointeur vers un **const** élément dans un `hash_multiset`.|
|[const_reference](#const_reference)|Type qui fournit une référence à un **const** élément stocké dans un `hash_multiset` pour lire et effectuer **const** operations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **const** élément dans le `hash_multiset`.|
|[difference_type](#difference_type)|Type entier signé qui fournit la différence entre deux itérateurs qui font référence à des éléments d'un même objet `hash_multiset`.|
|[iterator](#iterator)|Type qui fournit un itérateur bidirectionnel, qui peut lire ou modifier tout élément d'un objet `hash_multiset`.|
|[key_compare](#key_compare)|Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'un `hash_multiset`.|
|[key_type](#key_type)|Type qui décrit un objet stocké comme élément d'un objet `hash_set` dans sa capacité comme clé de tri.|
|[pointer](#pointer)|Type qui fournit un pointeur vers un élément d'un objet `hash_multiset`.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un `hash_multiset`.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'un `hash_multiset` inversé.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `hash_multiset`.|
|[value_compare](#value_compare)|Type qui fournit deux objets de fonction, un prédicat binaire de la comparaison de classe qui peut comparer deux valeurs d'éléments d'un `hash_multiset` pour déterminer leur ordre relatif et un prédicat unaire qui hache les éléments.|
|[value_type](#value_type)|Type qui décrit un objet stocké comme élément d'un objet `hash_multiset` dans sa capacité comme valeur.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[begin](#begin)|Retourne un itérateur qui référence le premier élément d'un objet `hash_multiset`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_multiset`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `hash_multiset`.|
|[clear](#clear)|Efface tous les éléments d'un `hash_multiset`.|
|[count](#count)|Retourne le nombre d'éléments d'un objet `hash_multiset` dont la clé correspond à une clé spécifiée par un paramètre.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_multiset` inversé.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `hash_multiset` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `hash_multiset`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `hash_multiset`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `hash_multiset` est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_multiset`.|
|[equal_range](#equal_range)|Retourne une paire d'itérateurs, respectivement vers le premier élément d'un objet `hash_multiset` avec une clé supérieure à une clé spécifiée, et vers le premier élément d'un objet `hash_multiset` avec une clé supérieure ou égale à la clé.|
|[erase](#erase)|Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un `hash_multiset` ou supprime les éléments qui correspondent à une clé spécifiée.|
|[find](#find)|Retourne un itérateur qui référence l'emplacement d'un élément d'un objet `hash_multiset` qui a une clé équivalente à une clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire le `hash_multiset`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans un `hash_multiset`.|
|[key_comp](#key_compare)|Récupère une copie de l'objet de comparaison utilisé pour trier les clés au sein d'un `hash_multiset`.|
|[lower_bound](#lower_bound)|Retourne un itérateur au premier élément d'un `hash_multiset` avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `hash_multiset`.|
|[rbegin](#rbegin)|Retourne un itérateur qui traite le premier élément d'un `hash_multiset` inversé.|
|[rend](#rend)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_multiset` inversé.|
|[size](#size)|Retourne le nombre d'éléments d'un `hash_multiset`.|
|[swap](#swap)|Échange les éléments de deux `hash_multiset`.|
|[upper_bound](#upper_bound)|Retourne un itérateur au premier élément d'un `hash_multiset` avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[value_comp](#value_comp)|Récupère une copie de l'objet de caractéristiques de hachage utilisé pour hacher et ordonner les valeurs des clés d'éléments dans un objet `hash_multiset`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[hash_multiset::operator=](#op_eq)|Remplace les éléments du hash_multiset par une copie d’un autre hash_multiset.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<hash_set>

**Espace de noms :** stdext

## <a name="allocator_type"></a>  hash_multiset::allocator_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type représentant la classe allocator pour l’objet hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="begin"></a>  hash_multiset::begin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur qui traite le premier élément du hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite le premier élément du hash_multiset ou l’emplacement qui suit un hash_multiset vide.

### <a name="remarks"></a>Notes

Si la valeur de retour de `begin` est affecté à un `const_iterator`, les éléments dans l’objet hash_multiset ne peut pas être modifiés. Si la valeur de retour de `begin` est affecté à un `iterator`, les éléments dans l’objet hash_multiset peuvent être modifiés.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="cbegin"></a>  hash_multiset::cbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur const qui traite le premier élément du hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite le premier élément du [hash_multiset](../standard-library/hash-multiset-class.md) ou l’emplacement qui suit un `hash_multiset` vide.

### <a name="remarks"></a>Notes

Avec la valeur de retour `cbegin`, les éléments de l’objet `hash_multiset` ne peuvent pas être modifiés.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>  hash_multiset::cend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur const qui traite l’emplacement situé après le dernier élément d’un hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite l’emplacement suivant le dernier élément d’un [hash_multiset](../standard-library/hash-multiset-class.md). Si le `hash_multiset` est vide, `hash_multiset::cend == hash_multiset::begin`.

### <a name="remarks"></a>Notes

`cend` est utilisé pour déterminer si un itérateur a atteint la fin de son `hash_multiset`. La valeur retournée par `cend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>  hash_multiset::clear

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Efface tous les éléments d’un hash_multiset.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multiset::const_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire un élément **const** dans le hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [begin](#begin) pour obtenir un exemple qui utilise `const_iterator`.

## <a name="const_pointer"></a>  hash_multiset::const_pointer

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un pointeur vers un élément **const** dans un hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément.

Dans la plupart des cas, vous devez utiliser un [iterator const](#const_iterator) pour accéder aux éléments dans un objet **const** hash_multiset.

## <a name="const_reference"></a>  hash_multiset::const_reference

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit une référence à un élément **const** stocké dans un hash_multiset pour la lecture et l’exécution d’opérations **const**.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multiset::const_reverse_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire tout élément **const** dans le hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer le hash_multiset dans l’ordre inverse.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [rend](#rend) pour découvrir comment déclarer et utiliser le `const_reverse_iterator`.

## <a name="count"></a>  hash_multiset::count

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne le nombre d'éléments d'un hash_multiset dont la clé correspond à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé des éléments à mettre en correspondance à partir du hash_multiset.

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments dans le hash_multiset avec la clé spécifiée par le paramètre.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d'éléments dans la plage suivante :

\[ lower_bound (*clé*), upper_bound (*clé*)).

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multiset::count.

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_multiset::crbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur const qui traite le premier élément d’un hash_multiset inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite le premier élément d’un [hash_multiset](../standard-library/hash-multiset-class.md) inversé ou qui traite ce qui était le dernier élément de l’objet `hash_multiset` non inversé.

### <a name="remarks"></a>Notes

`crbegin` est utilisé avec un `hash_multiset` inversé comme [hash_multiset::begin](#begin) est utilisé avec un `hash_multiset`.

Avec la valeur de retour `crbegin`, l'objet `hash_multiset` ne peut pas être changé.

Vous pouvez utiliser `crbegin` pour itérer un `hash_multiset` vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="crend"></a>  hash_multiset::crend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un hash_multiset inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un [hash_multiset](../standard-library/hash-multiset-class.md) inversé (emplacement qui précédait celui du premier élément du `hash_multiset` non inversé).

### <a name="remarks"></a>Notes

`crend` est utilisé avec un `hash_multiset` inversé comme [hash_multiset::end](#end) est utilisé avec un `hash_multiset`.

Avec la valeur de retour `crend`, l'objet `hash_multiset` ne peut pas être changé.

Vous pouvez utiliser `crend` pour déterminer si un itérateur inversé a atteint la fin de son hash_multiset.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="difference_type"></a>  hash_multiset::difference_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type entier signé qui fournit la différence entre deux itérateurs qui font référence à des éléments du même hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

`difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type` est généralement utilisé pour représenter le nombre d’éléments de la plage [ `first`, `last`) entre les itérateurs `first` et `last`. Il inclut l’élément sur lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) sur lequel pointe `last`.

Notez que bien que `difference_type` soit disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui inclut la classe des itérateurs bidirectionnels prise en charge par des conteneurs réversibles tels que set, la soustraction entre des itérateurs est prise en charge uniquement par les itérateurs d’accès aléatoire fournis par un conteneur à accès aléatoire tel que vector ou deque.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="emplace"></a>  hash_multiset::emplace

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Insère un élément construit sur place dans un hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur d’un élément à insérer dans le [hash_multiset](../standard-library/hash-multiset-class.md), sauf si le `hash_multiset` contient déjà cet élément ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente.|

### <a name="return-value"></a>Valeur de retour

La fonction membre `emplace` retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="emplace_hint"></a>  hash_multiset::emplace_hint

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Insère un élément construit sur place dans un hash_multiset, avec un indicateur de positionnement.

```cpp
template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur d’un élément à insérer dans le [hash_multiset](../standard-library/hash-multiset-class.md), sauf si le `hash_multiset` contient déjà cet élément ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente.|
|*_WHERE*|Emplacement où commencer à rechercher le point d'insertion correct. (L’insertion peut se produire dans le temps fixe amorti, plutôt que de temps logarithmique, si le point d’insertion suit immédiatement *_Where*.)|

### <a name="return-value"></a>Valeur de retour

La fonction membre [hash_multiset::emplace](#emplace) retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré dans le `hash_multiset`.

### <a name="remarks"></a>Notes

L’insertion peut se produire dans le temps fixe amorti, plutôt que de temps logarithmique, si le point d’insertion suit immédiatement *_Where*.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="empty"></a>  hash_multiset::empty

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Teste si un hash_multiset est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le hash_multiset est vide. **false** si le hash_multiset n’est pas vide.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="end"></a>  hash_multiset::end

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément du hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite l’emplacement suivant le dernier élément d’un hash_multiset. Si le hash_multiset est vide, hash_multiset::end == hash_multiset::begin.

### <a name="remarks"></a>Notes

`end` est utilisé pour déterminer si un itérateur a atteint la fin de son hash_multiset. La valeur retournée par `end` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="equal_range"></a>  hash_multiset::equal_range

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne une paire d’itérateurs, respectivement au premier élément d’un hash_multiset ayant une clé supérieure à celle spécifiée et au premier élément d’un hash_multiset ayant une clé supérieure ou égale à la clé spécifiée.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé d’argument à comparer à la clé de tri d’un élément du hash_multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

Paire d’itérateurs où le premier est l’itérateur [lower_bound](#lower_bound) de la clé et le second, l’itérateur [upper_bound](#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **first**, et pour déréférencer l’itérateur de la limite inférieure, utilisez \*( `pr`. **first**). Pour accéder au deuxième itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **second**, et pour déréférencer l’itérateur de la limite supérieure, utilisez \*( `pr`. **second**).

### <a name="example"></a>Exemple

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  hash_multiset::erase

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un hash_multiset ou supprime les éléments qui correspondent à une clé spécifiée.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Paramètres

*_WHERE*<br/>
Position de l'élément à supprimer du hash_multiset.

*first*<br/>
Position du premier élément supprimé du hash_multiset.

*last*<br/>
Position juste après le dernier élément supprimé du hash_multiset.

*key*<br/>
Clé des éléments à supprimer du hash_multiset.

### <a name="return-value"></a>Valeur de retour

Pour les deux premières fonctions membres, il s'agit d'un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un pointeur vers la fin du hash_multiset si aucun élément de ce genre n'existe. Pour la troisième fonction membre, il s'agit du nombre d'éléments qui ont été supprimés du hash_multiset.

### <a name="remarks"></a>Notes

Les fonctions membres ne lèvent jamais d'exception.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multiset::erase.

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="find"></a>  hash_multiset::find

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur qui traite le premier emplacement d’un élément d’un hash_multiset ayant une clé équivalente à une clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé d’argument qui doit correspondre à la clé de tri d’un élément du hash_multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement d’un élément équivalent à la clé spécifiée ou qui traite l’emplacement qui suit le dernier élément dans le hash_multiset si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur qui traite un élément du hash_multiset dont la clé de tri est `equivalent` à l’argument key sous un prédicat binaire qui induit un ordonnancement basé sur une-relation d’infériorité.

Si la valeur de retour de `find` est affecté à un `const_iterator`, l’objet hash_multiset ne peut pas être modifié. Si la valeur de retour de `find` est affecté à un `iterator`, l’objet hash_multiset peut être modifié.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_multiset::get_allocator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne une copie de l’objet allocateur utilisé pour construire le hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Allocateur utilisé par le hash_multiset pour gérer la mémoire, qui est le paramètre de modèle de la classe `Allocator`.

Pour plus d’informations sur `Allocator`, consultez la section Notes de la rubrique [hash_multiset, classe](../standard-library/hash-multiset-class.md).

### <a name="remarks"></a>Notes

Les allocateurs de la classe hash_multiset spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de bibliothèque C++ Standard suffisent à satisfaire la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
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

## <a name="hash_multiset"></a>  hash_multiset::hash_multiset

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Construit un `hash_multiset` vide ou une copie de l'ensemble ou d'une partie d'un autre `hash_multiset`.

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Al*|Classe d’allocateur de stockage à utiliser pour cet objet `hash_multiset`, qui est par défaut `Allocator`.|
|*Comp.*|Fonction de comparaison de type `const Traits` utilisée pour ordonner les éléments dans le `hash_multiset` (par défaut, `hash_compare`).|
|*Droite*|`hash_multiset` dont le `hash_multiset` construit doit être une copie.|
|*Premier*|Position du premier élément de la plage d'éléments à copier.|
|*Dernière*|Position du premier élément au-delà de la plage d'éléments à copier.|
|*IList*|initializer_list qui contient les éléments à copier.|

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du `hash_multiset` et peut être retourné ultérieurement en appelant [hash_multiset::get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leurs hash_multisets.

Tous les constructeurs stockent un objet de fonction de type `Traits`, qui est utilisé pour établir un ordre parmi les clés du `hash_multiset` et qui peut être retourné ultérieurement en appelant [hash_multiset::key_comp](#key_comp). Pour plus d’informations sur `Traits`, consultez la rubrique [hash_multiset, classe](../standard-library/hash-multiset-class.md).

Les trois premiers constructeurs spécifient une initiale vide `hash_multiset`, le deuxième spécifie le type de fonction de comparaison (*Comp*) à utiliser pour établir l’ordre des éléments et le troisième explicitement en spécifiant le type d’allocateur (*Al*) à utiliser. Le mot clé **explicit** supprime certains genres de conversions de type automatiques.

Le quatrième constructeur déplace le `hash_multiset` `Right`.

Les cinquième, sixième et septième constructeurs utilisent un objet initializer_list.

Les trois derniers constructeurs copient la plage [ `First`, `Last`) d’un `hash_multiset` avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison de la classe Compare et de l’allocateur.

L’ordre réel des éléments dans un conteneur d’ensemble haché dépend de la fonction de hachage, de la fonction de tri et de la taille actuelle de la table de hachage. En général, il est impossible de la prédire comme avec le conteneur d’ensemble, où il était déterminé par la seule fonction de tri.

## <a name="insert"></a>  hash_multiset::insert

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Insère un élément ou une plage d’éléments dans un hash_multiset.

```cpp
iterator insert(
    const Type& Val);

iterator insert(
    iterator Where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& Val);

iterator insert(
    Iterator Where,
    const Type& Val);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur d’un élément à insérer dans le hash_multiset, sauf s’il contient déjà cet élément (ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente).|
|*Where*|Emplacement où commencer à rechercher le point d'insertion correct. (L’insertion peut se produire dans le temps fixe amorti, plutôt que dans le temps logarithmique, si le point d’insertion suit immédiatement `_Where`.)|
|*Premier*|Position du premier élément à copier à partir du hash_multiset.|
|*Dernière*|Position juste au-delà du dernier élément à copier à partir du hash_multiset.|
|*IList*|initializer_list qui contient les éléments à copier.|

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions membres insert retournent un itérateur qui pointe vers l’emplacement d’insertion du nouvel élément.

Les trois fonctions membres suivantes utilisent un objet initializer_list.

La troisième fonction membre insère la séquence de valeurs d’éléments dans un hash_multiset qui correspond à chaque élément traité par un itérateur dans la plage [ `First`, `Last`) d’un hash_multiset spécifié.

### <a name="remarks"></a>Notes

L’insertion peut se produire dans le temps fixe amorti pour la version de l’indicateur d’insert, plutôt que de temps logarithmique, si le point d’insertion suit immédiatement *où*.

## <a name="iterator"></a>  hash_multiset::iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Notes

Un type `iterator` peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Consultez l’exemple pour [commencer](#begin) pour obtenir un exemple montrant comment déclarer et utiliser `iterator`.

## <a name="key_comp"></a>  hash_multiset::key_comp

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Récupère une copie de l’objet de comparaison utilisé pour trier les clés dans un hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le paramètre de modèle hash_multiset *Traits*, qui contient des objets de fonction sont utilisés pour hacher et ordonner les éléments du conteneur.

Pour plus d’informations sur *Traits* voir le [hash_multiset, classe](../standard-library/hash-multiset-class.md) rubrique.

### <a name="remarks"></a>Notes

L’objet stocké définit une fonction membre :

**bool operator**( **const Key&** *_xVal,* **const Key&** _ `yVal`);

qui retourne **true** si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

Notez que [key_compare](#key_compare) et [value_compare](#value_compare) sont tous deux des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournies pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multiset::key_compare

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit deux objets de fonction, un prédicat binaire de la comparaison de classe qui peut comparer deux valeurs d’éléments d’un hash_multiset pour déterminer leur ordre relatif et un prédicat unaire qui hache les éléments.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Notes

`key_compare` est un synonyme du paramètre de modèle *Traits*.

Pour plus d’informations sur *Traits* voir le [hash_multiset, classe](../standard-library/hash-multiset-class.md) rubrique.

Notez que `key_compare` et value_compare sont tous deux des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournis pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_compare`, consultez l’exemple relatif à [key_comp](#key_comp).

## <a name="key_type"></a>  hash_multiset::key_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un objet de fonction pouvant comparer des clés de tri pour déterminer l’ordre relatif de deux éléments dans le hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

`key_type` est un synonyme du paramètre de modèle *clé*.

Notez que `key_type` et [value_type](../standard-library/hash-set-class.md#value_type) sont tous deux des synonymes du paramètre de modèle *Key*. Ces deux types sont fournis pour les classes set et multiset, où ils sont identiques, pour la compatibilité avec les classes map et multimap, où ils sont distincts.

Pour plus d’informations sur *clé*, consultez la section Notes de la [hash_multiset, classe](../standard-library/hash-multiset-class.md) rubrique.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_type`, consultez l’exemple relatif à [value_type](#value_type).

## <a name="lower_bound"></a>  hash_multiset::lower_bound

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur au premier élément d’un hash_multiset avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé d’argument à comparer à la clé de tri d’un élément du hash_multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement du premier élément dans un hash_multiset ayant une clé supérieure ou égale à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_multiset si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="max_size"></a>  hash_multiset::max_size

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne la longueur maximale du hash_multiset.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur maximale autorisée du hash_multiset.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multiset::operator=

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Remplace les éléments du hash_multiset par une copie d’un autre hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*right*|[hash_multiset](../standard-library/hash-multiset-class.md) copié dans le `hash_multiset`.|

### <a name="remarks"></a>Notes

Après avoir supprimé les éléments existants dans un `hash_multiset`, `operator=` copie ou déplace le contenu de *droit* dans le `hash_multiset`.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  hash_multiset::pointer

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un pointeur vers un élément d’un hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Notes

Un type `pointer` peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet multiset.

## <a name="rbegin"></a>  hash_multiset::rbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur traitant le premier élément d’un hash_multiset inversé.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé traitant le premier élément d’un hash_multiset inversé ou traitant ce qui était le dernier élément du hash_multiset non inversé.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec un hash_multiset inversé comme [begin](#begin) est utilisé avec un hash_multiset.

Si la valeur de retour de `rbegin` est affectée à un `const_reverse_iterator`, l’objet hash_multiset ne peut pas être changé. Si la valeur de retour de `rbegin` est affectée à un `reverse_iterator`, l’objet hash_multiset peut être changé.

Vous pouvez utiliser `rbegin` pour itérer un hash_multiset vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="reference"></a>  hash_multiset::reference

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit une référence à un élément stocké dans un hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="rend"></a>  hash_multiset::rend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un hash_multiset inversé.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un hash_multiset inversé (emplacement qui précédait celui du premier élément du hash_multiset non inversé).

### <a name="remarks"></a>Notes

`rend` est utilisé avec un hash_multiset inversé comme [end](#end) est utilisé avec un hash_multiset.

Si la valeur de retour de `rend` est affectée à un `const_reverse_iterator`, l’objet hash_multiset ne peut pas être changé. Si la valeur de retour de `rend` est affectée à un `reverse_iterator`, l’objet hash_multiset peut être changé. La valeur retournée par `rend` ne doit pas être déréférencée.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son hash_multiset.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // throught a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="reverse_iterator"></a>  hash_multiset::reverse_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_multiset inversé.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `reverse_iterator` est utilisé pour itérer le hash_multiset dans l’ordre inverse.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="size"></a>  hash_multiset::size

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne le nombre d’éléments dans le hash_multiset.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du hash_multiset.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="size_type"></a>  hash_multiset::size_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type entier non signé qui peut représenter le nombre d’éléments d’un hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).

## <a name="swap"></a>  hash_multiset::swap

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Échange les éléments de deux hash_multisets.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Argument hash_multiset qui fournit les éléments à échanger avec le hash_multiset cible.

### <a name="remarks"></a>Notes

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux hash_multisets dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="upper_bound"></a>  hash_multiset::upper_bound

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Retourne un itérateur au premier élément d’un hash_multiset avec une valeur de clé supérieure à celle de la clé spécifiée.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé d’argument à comparer à la clé de tri d’un élément du hash_multiset dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement du premier élément dans un hash_multiset ayant une clé supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_multiset si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="value_comp"></a>  hash_multiset::value_comp

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Récupère une copie de l’objet de comparaison utilisé pour trier les valeurs d’éléments d’un hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le paramètre de modèle hash_multiset *Traits*, qui contient des objets de fonction sont utilisés pour hacher et trier les éléments du conteneur.

Pour plus d’informations sur *Traits* voir le [hash_multiset, classe](../standard-library/hash-multiset-class.md) rubrique.

### <a name="remarks"></a>Notes

L’objet stocké définit une fonction membre :

**bool operator**( **constKey&**`_xVal`, **const Key&** *_yVal*);

qui retourne **true** si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

Notez que [key_compare](#key_compare) et [value_compare](#value_compare) sont tous deux des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournies pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="value_compare"></a>  hash_multiset::value_compare

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui fournit deux objets de fonction, un prédicat binaire de la comparaison de classe qui peut comparer deux valeurs d’éléments d’un hash_multiset pour déterminer leur ordre relatif et un prédicat unaire qui hache les éléments.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Notes

`value_compare` est un synonyme du paramètre de modèle *Traits*.

Pour plus d’informations sur *Traits* voir le [hash_multiset, classe](../standard-library/hash-multiset-class.md) rubrique.

Notez que les deux [key_compare](#key_compare) et `value_compare` sont des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournis pour les classes set et multiset, où ils sont identiques, pour la compatibilité avec les classes map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [value_comp](#value_comp) pour découvrir comment déclarer et utiliser `value_compare`.

## <a name="value_type"></a>  hash_multiset::value_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Type qui décrit un objet stocké comme élément d’un hash_multiset en sa capacité de valeur.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Exemple

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
