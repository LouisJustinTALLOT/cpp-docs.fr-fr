---
title: hash_map, classe
ms.date: 11/04/2016
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
ms.openlocfilehash: 063b71100af536a249949a1084ab208b6266fd8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222464"
---
# <a name="hash_map-class"></a>hash_map, classe

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Stocke et récupère des données rapidement auprès d’une collection dans laquelle chaque élément est une paire qui a une clé de tri dont la valeur est unique et une valeur de données associée.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>Paramètres

*Essentiel*\
Type de données de la clé à stocker dans l'objet hash_map.

*Entrer*\
Type de données de l'élément à stocker dans l'objet hash_map.

*Caractéristiques*\
Type qui inclut les deux objets de fonction, une de comparaison de classes capable de comparer deux valeurs d'éléments comme clés de tri pour déterminer leur ordre relatif, et une fonction de hachage qui est un prédicat unaire qui mappe les valeurs de clé des éléments à des entiers non signés de type `size_t`. Cet argument est facultatif, et hash_compare<`Key` , moins<`Key`> > est la valeur par défaut.

*Allocateur*\
Type qui représente l'objet allocateur stocké qui encapsule des informations détaillées sur l'allocation et la désallocation de mémoire de la classe hash_map. Cet argument est facultatif et sa valeur par défaut est Allocator \<pair <const `Key`, `Type`>>.

## <a name="remarks"></a>Notes

L'objet hash_map est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée.

- Réversible, car elle fournit un itérateur bidirectionnel pour accéder à ses éléments

- Haché, car ses éléments sont regroupés dans des compartiments selon la valeur d'une fonction de hachage appliquée aux valeurs de clé des éléments.

- Unique dans le sens où chacun de ses éléments doit avoir une clé unique.

- Un conteneur associatif de paires, car ses valeurs de données d'éléments sont séparées de ses valeurs de clés.

- Un modèle de classe, parce que la fonctionnalité qu’il fournit est générique et donc indépendante du type spécifique des données contenues en tant qu’éléments ou clés. Les types de données utilisés pour les éléments et les clés sont eux spécifiés comme paramètres dans la classe de modèle avec la fonction de comparaison et l'allocateur.

Le principal avantage du hachage sur le tri est une meilleure efficacité : un hachage réussi effectue des insertions, des suppressions et trouve ce qui est recherché dans un délai moyen constant, alors que pour les techniques de tri, ce délai est proportionnel au logarithme du nombre d'éléments du conteneur. La valeur d'un élément d'un objet hash_map peut être modifiée directement, mais pas la valeur de la clé qui y est associée. Les valeurs de clés associées aux anciens éléments doivent être supprimées, et de nouvelles valeurs de clés doivent être associées aux nouveaux éléments insérés.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs hachés sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces quand elles sont utilisées avec une fonction de hachage bien conçue, car elles les exécutent dans un délai qui est en moyenne constant et ne dépend pas du nombre d'éléments dans le conteneur. Une fonction de hachage bien conçue produit une distribution uniforme des valeurs de hachage et réduit le nombre de collisions, qui se produisent quand des valeurs de clés distinctes sont mappées dans la même valeur de hachage. Dans le pire des cas, avec la pire des fonctions de hachage possible, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (délai linéaire).

L'objet hash_map doit être sélectionné comme conteneur associatif quand les conditions associant les valeurs à leurs clés sont remplies par l'application. Un modèle pour ce type de structure est une liste ordonnée de mots clés uniques avec des valeurs de chaîne associées qui fournissent par exemple des définitions. Si au lieu de cela, un mot a plusieurs définitions correctes, de sorte que les clés ne sont pas uniques, il convient de choisir un objet hash_multimap comme conteneur. Si en revanche seule la liste des mots doit être stockée, un objet hash_set est le conteneur correct. Si plusieurs occurrences d'un mot sont autorisées, un objet hash_multiset est la structure de conteneur appropriée.

Le hash_map commande la séquence qu’il contrôle en appelant un objet de *caractéristiques* de hachage stocké de la classe [value_compare](../standard-library/value-compare-class.md). Cet objet stocké est accessible en appelant la fonction membre [key_comp](#key_comp). Un objet de fonction de ce type doit se comporter de la même manière qu’un objet de classe [hash_compare](../standard-library/hash-compare-class.md)<clé, moins \<Key>>. Plus précisément, pour toutes les valeurs *Key* de type *Key*, l’appel `Traits` ( `Key` ) génère une distribution des valeurs de type `size_t` .

En général, les éléments ne doivent pas être tout à fait comparables, afin que, à l'aide de deux événements quelconques donnés, il soit possible de déterminer, soit qu'ils soient équivalents (dans le sens où l'un n'est pas inférieur à l'autre), soit que l'un est inférieur à l'autre. Cela entraîne le tri des éléments non équivalents. D’un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire f (x y) est un objet de fonction qui a deux objets d’argument `x` et `y` une valeur de retour **`true`** ou **`false`** . Un ordonnancement appliqué à un objet hash_map est un ordonnancement faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l'équivalence est transitive (où deux objets x et y sont définis comme équivalents quand f(x, y) et f(y, x) ont la valeur false). Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction d'ordonnancement et de la taille actuelle de la table de hachage stockée dans l'objet conteneur. Vous ne pouvez pas déterminer la taille actuelle de la table de hachage, et vous ne pouvez donc généralement pas prédire l'ordre des éléments dans la séquence contrôlée. L'insertion d'éléments ne rend aucun itérateur non valide. La suppression d'éléments rend uniquement non valides les itérateurs qui pointaient spécifiquement vers les éléments supprimés.

L’itérateur fourni par la classe hash_map est un itérateur bidirectionnel. Toutefois, les fonctions membres de classe [insert](#insert) et [hash_map](#hash_map) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences de fonctionnalités sont minimales par rapport à celles qui sont garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre ensemble de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s'agit d'un ensemble minimal de fonctionnalités, mais c'est suffisant pour pouvoir parler d'une plage d'itérateurs `[First, Last)` dans le contexte des fonctions membres de la classe.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[hash_map](#hash_map)|Construit un `hash_map` vide ou une copie de l'ensemble ou d'une partie d'un autre `hash_map`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet `hash_map`.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément dans le `hash_map` .|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un **`const`** élément d’un `hash_map` .|
|[const_reference](#const_reference)|Type qui fournit une référence à un **`const`** élément stocké dans un `hash_map` pour la lecture et l’exécution d' **`const`** opérations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément de `hash_map` .|
|[difference_type](#difference_type)|Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'un `hash_map` au sein d'une plage, parmi les éléments pointés par les itérateurs.|
|[répétiteur](#iterator)|Type qui fournit un itérateur bidirectionnel, qui peut lire ou modifier tout élément d'un objet `hash_map`.|
|[key_compare](#key_compare)|Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'un `hash_map`.|
|[key_type](#key_type)|Type qui décrit l'objet de clé de tri qui constitue chaque élément de la classe `hash_map`.|
|[mapped_type](#mapped_type)|Type qui représente le type de données stocké dans un `hash_map`.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un élément d'un objet `hash_map`.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un `hash_map`.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'un `hash_map` inversé.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `hash_map`.|
|[value_type](#value_type)|Type qui fournit un objet de fonction pouvant comparer deux éléments comme clés de tri pour déterminer leur ordre relatif dans le `hash_map`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[at](#at)|Recherche un élément dans un objet `hash_map` avec une valeur de clé spécifiée.|
|[commencer](#begin)|Retourne un itérateur traitant le premier élément d'un `hash_map`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_map`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `hash_map`.|
|[clear](#clear)|Efface tous les éléments d'un `hash_map`.|
|[count](#count)|Retourne le nombre d'éléments d'un `hash_map` dont la clé correspond à une clé spécifiée par un paramètre.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_map` inversé.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `hash_map` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `hash_map`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `hash_map`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `hash_map` est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_map`.|
|[equal_range](#equal_range)|Retourne une paire d'itérateurs, respectivement vers le premier élément d'un objet `hash_map` avec une clé supérieure à une clé spécifiée, et vers le premier élément d'un objet `hash_map` avec une clé supérieure ou égale à la clé.|
|[erase](#erase)|Supprime un élément ou une plage d'éléments aux positions spécifiées d'un objet `hash_map`.|
|[find](#find)|Retourne un itérateur qui référence l'emplacement d'un élément d'un objet `hash_map` qui a une clé équivalente à une clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire le `hash_map`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans un `hash_map`.|
|[key_comp](#key_comp)|Retourne un itérateur pointant vers le premier élément d'un objet `hash_map` qui a une valeur de clé supérieure ou égale à celle d'une clé spécifiée.|
|[lower_bound](#lower_bound)|Retourne un itérateur pointant vers le premier élément d'un objet `hash_map` qui a une valeur de clé supérieure ou égale à celle d'une clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `hash_map`.|
|[rbegin](#rbegin)|Retourne un itérateur qui traite le premier élément d'un `hash_map` inversé.|
|[rend](#rend)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_map` inversé.|
|[size](#size)|Retourne le nombre d'éléments d'un `hash_map`.|
|[swap](#swap)|Échange les éléments de deux `hash_map`.|
|[upper_bound](#upper_bound)|Retourne un itérateur pointant vers le premier élément d'un objet `hash_map` qui a une valeur de clé supérieure à celle d'une clé spécifiée.|
|[value_comp](#value_comp)|Récupère une copie de l'objet de comparaison utilisé pour ordonner les valeurs des éléments d'un objet `hash_map`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator&#91;&#93;](#op_at)|Insère un élément dans un objet `hash_map` avec une valeur de clé spécifiée.|
|[hash_map::operator=](#op_eq)|Remplace les éléments d'un `hash_map` par une copie d'un autre `hash_map`.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<hash_map>

**Espace de noms :** stdext

## <a name="hash_mapallocator_type"></a><a name="allocator_type"></a>hash_map :: allocator_type

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type représentant la classe allocator pour l’objet hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="hash_mapat"></a><a name="at"></a>hash_map :: à

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Recherche un élément dans un hash_map avec une valeur de clé spécifiée.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*key*|Valeur de clé de l’élément à rechercher.|

### <a name="return-value"></a>Valeur de retour

Référence à la valeur de données de l'élément trouvé.

### <a name="remarks"></a>Notes

Si la valeur de clé de l’argument est introuvable, la fonction lève un objet de classe [out_of_range Class](../standard-library/out-of-range-class.md).

### <a name="example"></a>Exemple

```cpp
// hash_map_at.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;

   // Insert data values
   hm1.insert ( cInt2Int ( 1, 10 ) );
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The values of the mapped elements are:";
   for ( int i = 1 ; i <= hm1.size() ; i++ )
      cout << " " << hm1.at(i);
   cout << "." << endl;
}
```

## <a name="hash_mapbegin"></a><a name="begin"></a>hash_map :: Begin

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur qui traite le premier élément du hash_map.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite le premier élément du hash_map ou l’emplacement qui suit un hash_map vide.

### <a name="example"></a>Exemple

```cpp
// hash_map_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now "
        << hm1_cIter -> first << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_mapcbegin"></a><a name="cbegin"></a>hash_map :: cbegin

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur const qui traite le premier élément du hash_map.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite le premier élément du [hash_map](../standard-library/hash-map-class.md) ou l’emplacement qui suit un `hash_map` vide.

### <a name="example"></a>Exemple

```cpp
// hash_map_cbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="hash_mapcend"></a><a name="cend"></a>hash_map :: CEND

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur const qui traite l’emplacement situé après le dernier élément d’un hash_map.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite l’emplacement suivant le dernier élément d’un [hash_map](../standard-library/hash-map-class.md). Si le `hash_map` est vide, `hash_map::cend == hash_map::begin`.

### <a name="remarks"></a>Notes

`cend` est utilisé pour déterminer si un itérateur a atteint la fin de son `hash_map`.

La valeur retournée par `cend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_map_cend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="hash_mapclear"></a><a name="clear"></a>hash_map :: Clear

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Efface tous les éléments d'un hash_map.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_map::clear.

```cpp
// hash_map_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_map is initially "
         << i << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_map is initially 2.
The size of the hash_map after clearing is 0.
```

## <a name="hash_mapconst_iterator"></a><a name="const_iterator"></a>hash_map :: const_iterator

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément du hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.

Le `const_iterator` défini par hash_map pointe vers des éléments qui sont des objets de [Value_type](#value_type), qui est de type `pair< const Key, Type >` , dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.

Pour déréférencer un `const_iterator` `cIter` pointant sur un élément dans un hash_map, utilisez l' `->` opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `cIter->first` , qui est équivalent à `(*cIter).first` . Pour accéder à la valeur de la référence mappée de l’élément, utilisez `cIter->second` , qui est équivalent à `(*cIter).second` .

### <a name="example"></a>Exemple

Consultez l’exemple de [begin](#begin) pour obtenir un exemple qui utilise `const_iterator`.

## <a name="hash_mapconst_pointer"></a><a name="const_pointer"></a>hash_map :: const_pointer

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un pointeur vers un **`const`** élément d’un hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet hash_map.

## <a name="hash_mapconst_reference"></a><a name="const_reference"></a>hash_map :: const_reference

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit une référence à un **`const`** élément stocké dans une hash_map pour la lecture et l’exécution d' **`const`** opérations.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of the first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of the first element in the hash_map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the hash_map is 1.
The data value of the first element in the hash_map is 10.
```

## <a name="hash_mapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_map :: const_reverse_iterator

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire un **`const`** élément de la hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer le hash_map dans l’ordre inverse.

Le `const_reverse_iterator` défini par hash_map pointe vers des éléments qui sont des objets de [Value_type](#value_type), qui est de type `pair` \< **const Key, Type**> , dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.

Pour déréférencer un `const_reverse_iterator` `crIter` pointant sur un élément dans un hash_map, utilisez l’opérateur **->**.

Pour accéder à la valeur de la clé de l’élément, utilisez `crIter` -> **first**, ce qui équivaut à (\* `crIter`) **.first**. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `crIter` -> **second**, ce qui équivaut à (\* `crIter`). **tout d’abord**.

### <a name="example"></a>Exemple

Consultez l’exemple [rend](#rend) pour savoir comment déclarer et utiliser le type `const_reverse_iterator`.

## <a name="hash_mapcount"></a><a name="count"></a>hash_map :: Count

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne le nombre d'éléments d'un hash_map dont la clé correspond à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé des éléments à mettre en correspondance à partir du hash_map.

### <a name="return-value"></a>Valeur de retour

1 si le hash_map contient un élément dont la clé de tri correspond à la clé du paramètre ; 0 si le hash_map ne contient pas d'élément avec une clé correspondante.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d’éléments *x* dans la plage

\[lower_bound (*clé*), upper_bound (*clé*))

qui est 0 ou 1 dans le cas de hash_map, qui est un conteneur associatif unique.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_map::count.

```cpp
// hash_map_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair (1, 1));
    hm1.insert(Int_Pair (2, 1));
    hm1.insert(Int_Pair (1, 4));
    hm1.insert(Int_Pair (2, 1));

    // Keys must be unique in hash_map, so duplicates are ignored
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 1.
The number of elements in hm1 with a sort key of 2 is: 1.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_mapcrbegin"></a><a name="crbegin"></a>hash_map :: crbegin

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur const qui traite le premier élément d’un hash_map inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite le premier élément d’un [hash_map](../standard-library/hash-map-class.md) inversé ou qui traite ce qui était le dernier élément de l’objet `hash_map` non inversé.

### <a name="remarks"></a>Notes

`crbegin` est utilisé avec un hash_map inversé comme [begin](#begin) est utilisé avec un `hash_map`.

Avec la valeur de retour `crbegin`, l'objet `hash_map` ne peut pas être changé.

`crbegin` peut servir à itérer un `hash_map` vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_map_crbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapcrend"></a><a name="crend"></a>hash_map :: crend

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un hash_map inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un [hash_map](../standard-library/hash-map-class.md) inversé (emplacement qui précédait celui du premier élément du `hash_map` non inversé).

### <a name="remarks"></a>Notes

`crend` est utilisé avec un `hash_map` inversé comme [hash_map::end](#end) est utilisé avec un `hash_map`.

Avec la valeur de retour `crend`, l'objet `hash_map` ne peut pas être changé.

`crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son objet `hash_map`.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_map_crend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 3.
```

## <a name="hash_mapdifference_type"></a><a name="difference_type"></a>hash_map ::d ifference_type

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type entier signé qui peut être utilisé pour représenter le nombre d’éléments d’un hash_map au sein d’une plage, parmi les éléments pointés par les itérateurs.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="example"></a>Exemple

```cpp
// hash_map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );

   // The following won't insert, because map keys are unique
   hm1.insert ( Int_Pair ( 2, 30 ) );

   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
   hm1_bIter = hm1.begin( );
   hm1_eIter = hm1.end( );

   // Count the number of elements in a hash_map
   hash_map <int, int>::difference_type  df_count = 0;
   hm1_Iter = hm1.begin( );
   while ( hm1_Iter != hm1_eIter)
   {
      df_count++;
      hm1_Iter++;
   }

   cout << "The number of elements in the hash_map hm1 is: "
        << df_count << "." << endl;

   cout  << "The keys of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> second;
   cout << "." << endl;
}
```

```Output
The number of elements in the hash_map hm1 is: 3.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 20.
```

## <a name="hash_mapemplace"></a><a name="emplace"></a>hash_map :: emplace

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Insère un élément construit sur place dans un hash_map.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*multiples*|Valeur utilisée pour déplacer un élément à insérer dans le [hash_map](../standard-library/hash-map-class.md), sauf si le `hash_map` contient déjà cet élément (ou, plus généralement, s’il contient déjà un élément dont la clé est ordonnée de façon équivalente).|

### <a name="return-value"></a>Valeur de retour

La fonction membre `emplace` retourne une paire dont le composant booléen retourne true si une insertion a été effectuée et false si le `hash_map` contenait déjà un élément dont la clé avait une valeur équivalente dans l’ordre, et dont le composant itérateur retourne l’adresse où un nouvel élément a été inséré, ou l’emplacement où l’élément se trouvait déjà.

Pour accéder au composant itérateur d’une paire `pr` retournée par cette fonction membre, utilisez `pr.first` et, pour le déréférencer, utilisez `*(pr.first)`. Pour accéder au **`bool`** composant d’une paire `pr` retournée par cette fonction membre, utilisez `pr.second` et pour le déréférencer, utilisez `*(pr.second)` .

### <a name="remarks"></a>Notes

Le [hash_map::value_type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

### <a name="example"></a>Exemple

```cpp
// hash_map_emplace.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_mapemplace_hint"></a><a name="emplace_hint"></a>hash_map :: emplace_hint

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Insère un élément construit sur place dans un hash_map, avec un indicateur de positionnement.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*multiples*|Valeur utilisée pour déplacer un élément à insérer dans le [hash_map](../standard-library/hash-map-class.md), sauf si le `hash_map` contient déjà cet élément (ou, plus généralement, s’il contient déjà un élément dont la clé est ordonnée de façon équivalente).|
|*_Where*|Indicateur concernant l’emplacement où commencer à rechercher le point d’insertion correct.|

### <a name="return-value"></a>Valeur de retour

La fonction membre [hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) retourne un itérateur qui pointe vers l’emplacement où le nouvel élément a été inséré dans le `hash_map`, ou vers l’emplacement où se trouve l’élément existant avec un ordonnancement équivalent.

### <a name="remarks"></a>Notes

Le [hash_map::value_type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

L’insertion peut se produire dans le temps constant amorti, plutôt que dans le temps logarithmique, si le point d’insertion suit immédiatement *_WHERE*.

### <a name="example"></a>Exemple

```cpp
// hash_map_emplace_hint.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_mapempty"></a><a name="empty"></a>hash_map :: Empty

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Teste si un hash_map est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si le hash_map est vide ; **`false`** si la hash_map n’est pas vide.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_map hm1 is empty." << endl;
   else
      cout << "The hash_map hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_map hm2 is empty." << endl;
   else
      cout << "The hash_map hm2 is not empty." << endl;
}
```

```Output
The hash_map hm1 is not empty.
The hash_map hm2 is empty.
```

## <a name="hash_mapend"></a><a name="end"></a>hash_map :: fin

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément du hash_map.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite l’emplacement suivant le dernier élément d’un hash_map. Si le hash_map est vide, hash_map::end == hash_map::begin.

### <a name="remarks"></a>Notes

`end`est utilisé pour déterminer si un itérateur a atteint la fin de son hash_map.

La valeur retournée par `end` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_map_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="hash_mapequal_range"></a><a name="equal_range"></a>hash_map :: equal_range

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne une paire d’itérateurs, respectivement au premier élément d’un hash_map ayant une clé supérieure à celle spécifiée et au premier élément d’un hash_map ayant une clé supérieure ou égale à la clé spécifiée.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé d’argument à comparer à la clé de tri d’un élément du hash_map dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

Paire d’itérateurs telle que le premier est la [lower_bound](#lower_bound) de la clé et le second est la [upper_bound](#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **tout d’abord** , et pour déréférencer l’itérateur de la limite inférieure, utilisez \* ( `pr` . **tout d’abord**). Pour accéder au second itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **ensuite** , pour déréférencer l’itérateur de la limite supérieure, utilisez \* ( `pr` . **seconde**).

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_map <int, int> IntMap;
   IntMap hm1;
   hash_map <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_map hm1 doesn't have an element "
             << "with a key less than 40." << endl;
   else
      cout << "The element of hash_map hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_map hm1 doesn't have an element with a key less than 40.
```

## <a name="hash_maperase"></a><a name="erase"></a>hash_map :: Erase

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un hash_map ou supprime les éléments qui correspondent à une clé spécifiée.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Paramètres

*_Where*\
Position de l'élément à supprimer du hash_map.

*premier*\
Position du premier élément supprimé du hash_map.

*famille*\
Position juste après le dernier élément supprimé du hash_map.

*essentiel*\
Valeur de clé des éléments à supprimer du hash_map.

### <a name="return-value"></a>Valeur de retour

Pour les deux premières fonctions membres, il s'agit d'un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un pointeur vers la fin du hash_map si aucun élément de ce genre n'existe.

Pour la troisième fonction membre, retourne le nombre d'éléments qui ont été supprimés du hash_map.

### <a name="remarks"></a>Notes

Les fonctions membres ne lèvent jamais d'exception.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_map::erase.

```cpp
// hash_map_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2, hm3;
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_map<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i));
        hm2.insert(Int_Pair (i, i*i));
        hm3.insert(Int_Pair (i, i-1));
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_map hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_map hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that"
         << endl;
    cout  << "of the 2nd element is deleted, "
          << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_map hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_map hm3 is: 0 2 3.
The number of elements removed from hm3 is: 1.
After another element with a key equal to that
of the 2nd element is deleted, the hash_map hm3 is: 0 3.
```

## <a name="hash_mapfind"></a><a name="find"></a>hash_map :: find

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur qui traite le premier emplacement d’un élément d’un hash_map ayant une clé équivalente à une clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé qui doit correspondre à la clé de tri d’un élément du hash_map dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite l’emplacement d’un élément ayant la clé spécifiée, ou emplacement qui suit le dernier élément du hash_map, si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

`find`retourne un itérateur qui traite un élément du hash_map dont la clé de tri est équivalente à la clé d’argument sous un prédicat binaire qui induit un classement basé sur une relation d’infériorité.

Si la valeur de retour de `find` est assignée à un [const_iterator](#const_iterator), l’objet hash_map ne peut pas être modifié. Si la valeur de retour de `find` est assignée à un [iterator](#iterator), l’objet hash_map peut être modifié.

### <a name="example"></a>Exemple

```cpp
// hash_map_find.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.find( 2 );
   cout << "The element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.find( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.find( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapget_allocator"></a><a name="get_allocator"></a>hash_map :: get_allocator

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne une copie de l’objet allocateur utilisé pour construire le hash_map.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Allocateur utilisé par le hash_map.

### <a name="remarks"></a>Notes

Les allocateurs de la classe hash_map spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// hash_map_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int>::allocator_type hm1_Alloc;
   hash_map <int, int>::allocator_type hm2_Alloc;
   hash_map <int, double>::allocator_type hm3_Alloc;
   hash_map <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_map <int, int> hm1;
   hash_map <int, int> hm2;
   hash_map <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_map hm4
   // with the allocator of hash_map hm1.
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_maphash_map"></a><a name="hash_map"></a>hash_map :: hash_map

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Construit un hash_map vide ou une copie de l’ensemble ou d’une partie d’un autre hash_map.

```cpp
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,
    const key_compare& Comp,
    const allocator_type& Al);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*&*|Classe d’allocateur de stockage à utiliser pour cet objet hash_map, qui a comme valeur par défaut `Allocator` .|
|*Conformes*|Fonction de comparaison de type const `Traits` utilisée pour ordonner les éléments dans le hash_map (par défaut, `hash_compare`).|
|*Right*|hash_map dont le mappage construit doit être une copie.|
|*First*|Position du premier élément de la plage d'éléments à copier.|
|*Famille*|Position du premier élément au-delà de la plage d'éléments à copier.|
|*IList*|initializer_list|

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du hash_map et peut être retourné ultérieurement en appelant [get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe, et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leur hash_map.

Tous les constructeurs stockent un objet de fonction de type `Traits`, qui est utilisé pour établir un ordre parmi les clés du hash_map et qui peut être retourné ultérieurement en appelant [key_comp](#key_comp).

Les trois premiers constructeurs spécifient un hash_map initial vide. en outre, le second spécifie le type de fonction de comparaison (*COMP*) à utiliser pour établir l’ordre des éléments et le troisième spécifie explicitement le type d’allocateur (*al*) à utiliser. Le mot clé **`explicit`** supprime certains genres de conversion de type automatique.

Le quatrième constructeur spécifie une copie du hash_map *droit*.

Les trois constructeurs suivants copient la plage `[First, Last)` d’un hash_map avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison de la classe `Traits` et de l’allocateur.

Le dernier constructeur déplace le hash_map *droit*.

## <a name="hash_mapinsert"></a><a name="insert"></a>hash_map :: Insert

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Insère un élément ou une plage d’éléments dans un hash_map.

```cpp
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,
    const value_type& val);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
pair <iterator, bool>
insert(
    ValTy&& val);

template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*multiples*|Valeur d’un élément à insérer dans le hash_map, sauf s’il contient déjà cet élément (ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente).|
|*_Where*|Indicateur concernant l’emplacement où commencer à rechercher le point d’insertion correct.|
|*first*|Position du premier élément à copier à partir du hash_map.|
|*last*|Position juste au-delà du dernier élément à copier à partir du hash_map.|

### <a name="return-value"></a>Valeur de retour

La première `insert` fonction membre retourne une paire dont le composant bool retourne la valeur true si une insertion a été effectuée et false si le hash_map contient déjà un élément dont la clé avait une valeur équivalente dans le classement, et dont le composant itérateur retourne l’adresse où un nouvel élément a été inséré ou l’emplacement où l’élément se trouvait déjà.

Pour accéder au composant itérateur d’une paire `pr` retournée par cette fonction membre, utilisez `pr`. **tout d’abord**, et pour le déréférencer, utilisez \* ( `pr` . **tout d’abord**). Pour accéder au **`bool`** composant d’une paire `pr` retournée par cette fonction membre, utilisez `pr` . **Deuxièmement**, et pour le déréférencer, utilisez \* ( `pr` . **seconde**).

La deuxième `insert` fonction membre, la version d’indicateur, retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré dans le hash_map.

Les deux dernières `insert` fonctions membres se comportent de la même façon que les deux premières, sauf qu’elles déplacent la valeur insérée.

### <a name="remarks"></a>Notes

Le [value_type](../standard-library/map-class.md#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

L’insertion peut se produire dans le temps constant amorti pour la version d’indicateur de Insert, au lieu du temps logarithmique, si le point d’insertion suit immédiatement *_WHERE*.

La troisième fonction membre insère la séquence de valeurs d’éléments dans un hash_map qui correspond à chaque élément traité par un itérateur dans la plage *[First, Last)* d’un jeu spécifié.

### <a name="example"></a>Exemple

```cpp
// hash_map_insert.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;

    hash_map<int, int> hm1, hm2;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 30));
    hm1.insert(Int_Pair(4, 40));

    cout << "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout << "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout << "The element 10 already exists in hm1\n"
            << "with a key value of "
            << "((pr.first) -> first) = " << (pr.first)->first
            << "." << endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout << "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout << "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << hm4.begin()->first
      << " => " << hm4.begin()->second
      << endl;
}
```

```Output
The original elements (Key => Value) of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
The element 10 already exists in hm1
with a key value of ((pr.first) -> first) = 1.
After the insertions, the elements of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
5 => 50
After the insertions, the elements of hm2 are:
2 => 20
10 => 100
3 => 30
4 => 40
After the move insertion, hm3 contains:
1 => a
After the move insertion, hm4 contains:
2 => b
```

## <a name="hash_mapiterator"></a><a name="iterator"></a>hash_map :: Iterator

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Notes

Le `iterator` défini par hash_map pointe vers des éléments qui sont des objets de [Value_type](#value_type), qui est de type **paire \<const Key, Type> ,** dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.

Pour déréférencer un **itérateur** `Iter` pointant vers un élément d’un multimap, utilisez l' `->` opérateur.

Pour accéder à la valeur de la clé de l’élément, utilisez `Iter` -> **first**, ce qui équivaut à (\* `Iter`). **tout d’abord**. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `Iter` -> **second**, ce qui équivaut à (\* `Iter`). **seconde**.

Un type `iterator` peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [Begin](#begin) pour obtenir un exemple de la façon de déclarer et d’utiliser `iterator` .

## <a name="hash_mapkey_comp"></a><a name="key_comp"></a>hash_map :: key_comp

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Récupère une copie de l’objet de comparaison utilisé pour trier les clés dans un hash_map.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’objet de fonction utilisé par un hash_map pour ordonner ses éléments.

### <a name="remarks"></a>Notes

L’objet stocké définit la fonction membre

**bool operator**( **const Key&** `left`**, const Key&** `right`);

cela retourne **`true`** si `left` précède et n’est pas égal à `right` dans l’ordre de tri.

### <a name="example"></a>Exemple

```cpp
// hash_map_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare
      kc1 = hm1.key_comp( ) ;

   // Operator stored in kc1 tests order & returns bool value
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }

   hash_map <int, int, hash_compare<int, greater<int> > > hm2;
   hash_map <int, int, hash_compare<int, greater<int> > >
      ::key_compare kc2 = hm2.key_comp( );

   // Operator stored in kc2 tests order & returns bool value
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
}
```

## <a name="hash_mapkey_compare"></a><a name="key_compare"></a>hash_map :: key_compare

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l’ordre relatif de deux éléments dans la classe map.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Notes

`key_compare` est un synonyme du paramètre de modèle `Traits`.

Pour plus d’informations sur `Traits`, consultez la rubrique [hash_map, classe](../standard-library/hash-map-class.md).

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_compare`, consultez l’exemple relatif à [key_comp](#key_comp).

## <a name="hash_mapkey_type"></a><a name="key_type"></a>hash_map :: key_type

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui décrit l’objet de clé de tri qui constitue chaque élément du hash_map.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

`key_type` est un synonyme du paramètre de modèle `Key`.

Pour plus d’informations sur `Key`, consultez la section Notes de la rubrique [hash_map, classe](../standard-library/hash-map-class.md).

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_type`, consultez l’exemple relatif à [value_type](#value_type).

## <a name="hash_maplower_bound"></a><a name="lower_bound"></a>hash_map :: lower_bound

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur pointant vers le premier élément d’un hash_map qui a une valeur de clé supérieure ou égale à celle d’une clé spécifiée.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé d’argument à comparer à la clé de tri d’un élément du hash_map dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement d’un élément dans un hash_map ayant une clé égale ou supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_map si aucune correspondance n’est trouvée pour la clé.

Si la valeur de retour de `lower_bound` est affectée à un `const_iterator`, l’objet hash_map ne peut pas être changé. Si la valeur de retour de `lower_bound` est assignée à `iterator` , l’objet hash_map peut être modifié.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The first element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1. lower_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // An element at a specific location in the hash_map can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="hash_mapmapped_type"></a><a name="mapped_type"></a>hash_map :: mapped_type

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui représente le type de données stockées dans un hash_map.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Notes

Le type `mapped_type` est un synonyme du paramètre de modèle `Type`.

Pour plus d’informations sur `Type`, consultez la rubrique [hash_map, classe](../standard-library/hash-map-class.md).

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_type`, consultez l’exemple relatif à [value_type](#value_type).

## <a name="hash_mapmax_size"></a><a name="max_size"></a>hash_map :: max_size

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne la longueur maximale du hash_map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur maximale autorisée du hash_map.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="hash_mapoperator"></a><a name="op_at"></a>hash_map :: Operator []

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Insère un élément dans un objet `hash_map` avec une valeur de clé spécifiée.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*key*|Valeur de clé de l’élément à insérer.|

### <a name="return-value"></a>Valeur de retour

Référence à la valeur de données de l'élément inséré.

### <a name="remarks"></a>Notes

Si la valeur de clé d’argument est introuvable, elle est insérée avec la valeur par défaut du type de données.

Vous pouvez utiliser `operator[]` pour insérer des éléments dans un `hash_map m` à l’aide de

`m[ key] = DataValue`;

où DataValue est la valeur du `mapped_type` de l’élément avec une valeur de clé de *clé*.

Quand vous utilisez `operator[]` pour insérer des éléments, la référence retournée n’indique pas si l’insertion va modifier un élément existant ou en créer un nouveau. Vous pouvez utiliser les fonctions membres [find](../standard-library/map-class.md#find) et [insert](../standard-library/map-class.md#insert) pour déterminer si un élément avec une clé spécifiée était déjà présent avant l’insertion.

### <a name="example"></a>Exemple

```cpp
// hash_map_op_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a hash_map using the operator[] member function
   hm1[ 1 ] = 10;

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   hm1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   hm1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // operator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="hash_mapoperator"></a><a name="op_eq"></a>hash_map :: Operator =

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Remplace les éléments du hash_map par une copie d’un autre hash_map.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Oui*|[Classe hash_map](../standard-library/hash-map-class.md) copiée dans le `hash_map`.|

### <a name="remarks"></a>Notes

Après l’effacement des éléments existants dans un `hash_map` , `operator=` copie ou déplace le contenu de *droite* dans le `hash_map` .

### <a name="example"></a>Exemple

```cpp
// hash_map_operator_as.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> v1, v2, v3;
   hash_map<int, int>::iterator iter;

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

## <a name="hash_mappointer"></a><a name="pointer"></a>hash_map ::p ointer

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un pointeur vers un élément d’un hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Notes

Un type `pointer` peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet hash_map.

## <a name="hash_maprbegin"></a><a name="rbegin"></a>hash_map :: rbegin

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur traitant le premier élément d’un hash_map inversé.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé traitant le premier élément d’un hash_map inversé ou traitant ce qui était le dernier élément du hash_map non inversé.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec un hash_map inversé comme [begin](#begin) est utilisé avec un hash_map.

Si la valeur de retour de `rbegin` est affectée à un [const_reverse_iterator](#const_reverse_iterator), l’objet hash_map ne peut pas être changé. Si la valeur de retour de `rbegin` est affectée à un [reverse_iterator](#reverse_iterator), l’objet hash_map peut être changé.

Vous pouvez utiliser `rbegin` pour itérer un hash_map vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_map_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the first element in the reversed hash_map is 2.
```

## <a name="hash_mapreference"></a><a name="reference"></a>hash_map :: référence

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit une référence à un élément stocké dans un hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_map is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The modified data value of first element is 15.
```

## <a name="hash_maprend"></a><a name="rend"></a>hash_map :: rend

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un hash_map inversé.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un hash_map inversé (emplacement qui précédait celui du premier élément du hash_map non inversé).

### <a name="remarks"></a>Notes

`rend` est utilisé avec un hash_map inversé comme [end](#end) est utilisé avec un hash_map.

Si la valeur de retour de `rend` est affectée à un [const_reverse_iterator](#const_reverse_iterator), l’objet hash_map ne peut pas être changé. Si la valeur de retour de `rend` est affectée à un [reverse_iterator](#reverse_iterator), l’objet hash_map peut être changé.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son hash_map.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_map_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );
   hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );
      hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 1.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the last element in the reversed hash_map is 2.
```

## <a name="hash_mapreverse_iterator"></a><a name="reverse_iterator"></a>hash_map :: reverse_iterator

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_map inversé.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer le hash_map dans l’ordre inverse.

Le `reverse_iterator` défini par hash_map pointe vers des éléments qui sont des objets de [Value_type](#value_type), qui est de type **paire \<const Key, Type> **, dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.

Pour déréférencer un `reverse_iterator` `rIter` pointant sur un élément dans un hash_map, utilisez l’opérateur ->.

Pour accéder à la valeur de la clé de l’élément, utilisez `rIter` -> **first**, ce qui équivaut à (\* `rIter`). **tout d’abord**. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `rIter` -> **second**, ce qui équivaut à (\* `rIter`). **tout d’abord**.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="hash_mapsize"></a><a name="size"></a>hash_map :: Size

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne le nombre d'éléments figurant dans le hash_map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du hash_map.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_map::size.

```cpp
// hash_map_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_map length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_map length is now " << i << "." << endl;
}
```

```Output
The hash_map length is 1.
The hash_map length is now 2.
```

## <a name="hash_mapsize_type"></a><a name="size_type"></a>hash_map :: size_type

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type entier non signé qui peut représenter le nombre d’éléments d’un hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).

## <a name="hash_mapswap"></a><a name="swap"></a>hash_map :: swap

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Échange les éléments de deux hash_maps.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Argument hash_map qui fournit les éléments à échanger avec le hash_map cible.

### <a name="remarks"></a>Notes

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux hash_maps dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// hash_map_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   hash_map <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   // hm2 is said to be the argument hash_map;
   // hm1 is said to be the target hash_map
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_map hm1 is: 10 20 30.
After swapping with hm2, hash_map hm1 is: 100 200.
After swapping with hm3, hash_map hm1 is: 300.
```

## <a name="hash_mapupper_bound"></a><a name="upper_bound"></a>hash_map :: upper_bound

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un itérateur pointant vers le premier élément d’un hash_map qui a une valeur de clé supérieure à celle d’une clé spécifiée.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*essentiel*\
Valeur de clé d’argument à comparer à la valeur de clé de tri d’un élément du hash_map dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement d’un élément dans un hash_map ayant une clé supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_map si aucune correspondance n’est trouvée pour la clé.

Si la valeur de retour est affectée à un `const_iterator`, l’objet hash_map ne peut pas être changé. Si la valeur de retour est assignée à `iterator` , l’objet hash_map peut être modifié.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_map_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_map hm1 with a key "
        << "greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   hm1_RcIter = hm1. upper_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key > 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );
   cout << "The 1st element of hm1 with a key greater than that\n"
        << "of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
of the initial element of hm1 is: 20.
```

## <a name="hash_mapvalue_comp"></a><a name="value_comp"></a>hash_map :: value_comp

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Retourne un objet de fonction qui détermine l’ordre des éléments d’un hash_map en comparant leurs valeurs de clés.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’objet de fonction de comparaison utilisé par un hash_map pour ordonner ses éléments.

### <a name="remarks"></a>Notes

Pour un hash_map *m*, si deux éléments *E1* (*K1*, *D1*) et *E2* (*K2*, *D2*) sont des objets de [type Value_type](#value_type), *où K1* et *K2* sont leurs clés de type [KEY_TYPE](#key_type) et *D1* et *D2* sont leurs données de type [mapped_type](#mapped_type), `m.value_comp()(e1, e2)` est équivalent à `m.key_comp()(k1, k2)` . Un objet stocké définit la fonction membre

`bool operator(value_type& left, value_type& right);`

qui retourne **`true`** si la valeur de clé de `left` précède et n’est pas égale à la valeur de clé de `right` dans l’ordre de tri.

### <a name="example"></a>Exemple

```cpp
// hash_map_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >
   ::value_compare vc1 = hm1.value_comp( );
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;

   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1 ( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_mapvalue_type"></a><a name="value_type"></a>hash_map :: value_type

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Type qui représente le type d’objet stocké dans un hash_map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Notes

`value_type`est déclaré comme étant `pair<const key_type, mapped_type>` et non `pair<key_type, mapped_type>` , car les clés d’un conteneur associatif ne peuvent pas être modifiées à l’aide d’un itérateur ou d’une référence non constante.

### <a name="example"></a>Exemple

```cpp
// hash_map_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: key_type key1;
   hash_map <int, int> :: mapped_type mapped1;
   hash_map <int, int> :: value_type value1;
   hash_map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
