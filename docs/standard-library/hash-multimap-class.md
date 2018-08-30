---
title: hash_multimap, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 857c0614288240aeaf3001d03aa5d6372ccee1c9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196303"
---
# <a name="hashmultimap-class"></a>hash_multimap, classe

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

La classe conteneur hash_multimap est une extension de la bibliothèque standard C++, et elle est utilisée pour le stockage et la récupération rapide des données d’une collection dans laquelle chaque élément est une paire qui a une clé de tri dont la valeur ne doit pas être unique et une valeur de données associée.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Paramètres

*Key*<br/>
 Type de données de la clé à stocker dans l'objet hash_multimap.

*Type*<br/>
 Type de données de l'élément à stocker dans l'objet hash_multimap.

*Caractéristiques*<br/>
 Type qui inclut les deux objets de fonction, une de la classe *Traits* qui est capable de comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif et une fonction de hachage est un opérateur unaire prédicat mappage des valeurs clés des éléments à les entiers de type non signés `size_t`. Cet argument est facultatif et sa valeur par défaut est `hash_compare<Key, less<Key>>`.

*Allocateur*<br/>
 Type qui représente l'objet allocateur stocké qui encapsule des informations détaillées sur l'allocation et la désallocation de mémoire de la classe hash_multimap. Cet argument est facultatif et sa valeur par défaut est `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Notes

L'objet hash_multimap est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée.

- Réversible, car elle fournit un itérateur bidirectionnel pour accéder à ses éléments

- Haché, car ses éléments sont regroupés dans des compartiments selon la valeur d'une fonction de hachage appliquée aux valeurs de clé des éléments.

- Multiple, car il n'est pas nécessaire que ses éléments possèdent des clés uniques, ce qui permet à une valeur de clé d'être associée à plusieurs valeurs de données d'éléments.

- Un conteneur associatif de paires, car ses valeurs d'éléments sont distinctes de ses valeurs de clés.

- Une classe de modèle, car la fonctionnalité qu'elle fournit est générique et donc indépendante du type de données contenues comme éléments ou comme clés. Les types de données utilisés pour les éléments et les clés sont eux spécifiés comme paramètres dans la classe de modèle avec la fonction de comparaison et l'allocateur.

Le principal avantage du hachage sur le tri est une meilleure efficacité : un hachage réussi effectue des insertions, des suppressions et trouve ce qui est recherché dans un délai moyen constant, alors que pour les techniques de tri, ce délai est proportionnel au logarithme du nombre d'éléments du conteneur. La valeur d'un élément d'une classe hash_multimap peut être modifiée directement, mais pas la valeur de clé qui y est associée. Les valeurs de clés associées aux anciens éléments doivent être supprimées, et de nouvelles valeurs de clés doivent être associées aux nouveaux éléments insérés.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs hachés sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces quand elles sont utilisées avec une fonction de hachage bien conçue, car elles les exécutent dans un délai qui est en moyenne constant et ne dépend pas du nombre d'éléments dans le conteneur. Une fonction de hachage bien conçue produit une distribution uniforme des valeurs de hachage et réduit le nombre de collisions, qui se produisent quand des valeurs de clés distinctes sont mappées dans la même valeur de hachage. Dans le pire des cas, avec la pire des fonctions de hachage possible, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (délai linéaire).

La classe hash_multimap doit être sélectionnée comme conteneur associatif quand les conditions associant les valeurs à leurs clés sont remplies par l'application. Pour ce type de structure, il peut s'agir d'une liste triée de mots clés avec des valeurs de chaîne associées fournissant par exemple des définitions, où les mots n'ont pas toujours été définis de manière unique. Si en revanche, les mots clés ont été définis de façon unique de sorte que les clés sont uniques, il convient d'utiliser un objet hash_map comme conteneur. Si en revanche seule la liste des mots doit être stockée, un objet hash_set est le conteneur correct. Si plusieurs occurrences d'un mot sont autorisées, un objet hash_multiset est la structure de conteneur appropriée.

L’objet hash_multimap ordonne la séquence qu’il contrôle en appelant un objet `Traits` de hachage stocké de type [value_compare](../standard-library/value-compare-class.md). Cet objet stocké est accessible en appelant la fonction membre [key_comp](../standard-library/hash-map-class.md#key_comp). Cet objet de fonction doit se comporter comme un objet de la classe [hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. En particulier, pour toutes les valeurs `Key` de type `Key`, l'appel `Traits (Key)` génère une distribution des valeurs de type `size_t`.

En général, les éléments ne doivent pas être tout à fait comparables, afin que, à l'aide de deux événements quelconques donnés, il soit possible de déterminer, soit qu'ils soient équivalents (dans le sens où l'un n'est pas inférieur à l'autre), soit que l'un est inférieur à l'autre. Ceci entraîne un ordonnancement entre les éléments non équivalents. D'un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire f (x, y) est un objet de fonction qui a deux objets arguments `x` et `y` et une valeur de retour de **true** ou **false**. Un tri appliqué à un objet hash_multimap est un ordonnancement faible strict si le prédicat binaire est irréflexif, Antisymétrique et transitif, et si l’équivalence est transitive, où deux objets `x` et `y` sont définis comme équivalents lorsque les deux f (x y) et f (y, x) sont **false**. Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction d'ordonnancement et de la taille actuelle de la table de hachage stockée dans l'objet conteneur. Vous ne pouvez pas déterminer la taille actuelle de la table de hachage, et vous ne pouvez donc généralement pas prédire l'ordre des éléments dans la séquence contrôlée. L'insertion d'éléments ne rend aucun itérateur non valide. La suppression d'éléments rend uniquement non valides les itérateurs qui pointaient spécifiquement vers les éléments supprimés.

L’itérateur fourni par la classe hash_multimap est un itérateur bidirectionnel. Toutefois, les fonctions membres de classe [insert](#insert) et [hash_multimap](#hash_multimap) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences des fonctionnalités sont inférieures à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur a son propre hash_multimap de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s'agit d'un hash_multimap minimal de fonctionnalités, mais il est suffisant pour pouvoir parler de plage d'itérateurs `[First, Last)` dans le contexte des fonctions membres.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[hash_multimap](#hash_multimap)|Construit une liste d'une taille spécifique ou avec des éléments d'une valeur spécifique ou avec un `allocator` spécifique, ou comme copie d'un autre objet `hash_multimap`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet `hash_multimap`.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un élément `const` dans le `hash_multimap`.|
|[const_pointer](#const_pointer)|Un type qui fournit un pointeur vers un **const** élément dans un `hash_multimap`.|
|[const_reference](#const_reference)|Type qui fournit une référence à un **const** élément stocké dans un `hash_multimap` pour lire et effectuer **const** operations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **const** élément dans le `hash_multimap`.|
|[difference_type](#difference_type)|Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'un `hash_multimap` au sein d'une plage, parmi les éléments pointés par les itérateurs.|
|[iterator](#iterator)|Type qui fournit un itérateur bidirectionnel, qui peut lire ou modifier tout élément d'un objet `hash_multimap`.|
|[key_compare](#key_compare)|Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'un `hash_multimap`.|
|[key_type](#key_type)|Type qui décrit l'objet de clé de tri qui constitue chaque élément du `hash_multimap`.|
|[mapped_type](#mapped_type)|Type qui représente le type de données stocké dans un `hash_multimap`.|
|[pointer](#pointer)|Type qui fournit un pointeur vers un élément d'un objet `hash_multimap`.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'un `hash_multimap` inversé.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `hash_multimap`.|
|[value_type](#value_type)|Type qui fournit un objet de fonction pouvant comparer deux éléments comme clés de tri pour déterminer leur ordre relatif dans le `hash_multimap`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[begin](#begin)|Retourne un itérateur traitant le premier élément d'un `hash_multimap`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_multimap`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `hash_multimap`.|
|[clear](#clear)|Efface tous les éléments d'un `hash_multimap`.|
|[count](#count)|Retourne le nombre d'éléments d'un `hash_multimap` dont la clé correspond à une clé spécifiée par un paramètre.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_multimap` inversé.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `hash_multimap` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `hash_multimap`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `hash_multimap`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `hash_multimap` est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_multimap`.|
|[equal_range](#equal_range)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_multimap`.|
|[erase](#erase)|Supprime un élément ou une plage d'éléments aux positions spécifiées d'un objet `hash_multimap`.|
|[find](#find)|Retourne un itérateur qui référence l'emplacement d'un élément d'un objet `hash_multimap` qui a une clé équivalente à une clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire le `hash_multimap`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans l'objet `hash_multimap` à un emplacement spécifié.|
|[key_comp](#key_comp)|Récupère une copie de l'objet de comparaison utilisé pour trier les clés au sein d'un `hash_multimap`.|
|[lower_bound](#lower_bound)|Retourne un itérateur pointant vers le premier élément d'un objet `hash_multimap` qui a une valeur de clé supérieure ou égale à celle d'une clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `hash_multimap`.|
|[rbegin](#rbegin)|Retourne un itérateur qui traite le premier élément d'un `hash_multimap` inversé.|
|[rend](#rend)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_multimap` inversé.|
|[size](#size)|Spécifie une nouvelle taille pour un objet `hash_multimap`.|
|[swap](#swap)|Échange les éléments de deux `hash_multimap`.|
|[upper_bound](#upper_bound)|Retourne un itérateur pointant vers le premier élément d'un objet `hash_multimap` qui a une valeur de clé supérieure à celle d'une clé spécifiée.|
|[value_comp](#value_comp)|Récupère une copie de l'objet de comparaison utilisé pour ordonner les valeurs des éléments d'un objet `hash_multimap`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[hash_multimap::operator=](#op_eq)|Remplace les éléments d'un `hash_multimap` par une copie d'un autre `hash_multimap`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<hash_map>

**Espace de noms :** stdext

## <a name="allocator_type"></a>  hash_multimap::allocator_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type représentant la classe allocator pour l’objet hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Notes

`allocator_type` est un synonyme du paramètre de modèle `Allocator`.

Pour plus d’informations sur `Allocator`, consultez la section Notes de la rubrique [hash_multimap, classe](../standard-library/hash-multimap-class.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="begin"></a>  hash_multimap::begin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur qui traite le premier élément du hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite le premier élément du hash_multimap ou l’emplacement qui suit un hash_multimap vide.

### <a name="remarks"></a>Notes

Si la valeur de retour de `begin` est affecté à un `const_iterator`, les éléments de l’objet hash_multimap ne peut pas être modifiés. Si la valeur de retour de `begin` est affecté à un `iterator`, les éléments de l’objet hash_multimap peuvent être modifiés.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="cbegin"></a>  hash_multimap::cbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur const qui traite le premier élément du hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite le premier élément du [hash_multimap](../standard-library/hash-multimap-class.md) ou l’emplacement qui suit un `hash_multimap` vide.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
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

## <a name="cend"></a>  hash_multimap::cend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur const qui traite l’emplacement situé après le dernier élément d’un hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite l’emplacement suivant le dernier élément d’un [hash_multimap](../standard-library/hash-multimap-class.md). Si le `hash_multimap` est vide, `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Notes

`cend` est utilisé pour déterminer si un itérateur a atteint la fin de son hash_multimap.

La valeur retournée par `cend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
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

## <a name="clear"></a>  hash_multimap::clear

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Efface tous les éléments d'un hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multimap::clear.

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multimap::const_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire un élément **const** dans le hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.

Le `const_iterator` défini par hash_multimap pointe vers des objets de [value_type](#value_type), qui sont de type `pair<const Key, Type>`. La valeur de la clé est disponible par l’intermédiaire du premier membre de la paire, et la valeur de l’élément mappé est disponible par l’intermédiaire du deuxième membre de la paire.

Pour déréférencer un `const_iterator` `cIter` pointant vers un élément dans un hash_multimap, utilisez le `->` opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `cIter->first`, ce qui équivaut à `(*cIter).first`. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `cIter->second`, ce qui équivaut à `(*cIter).second`.

### <a name="example"></a>Exemple

Consultez l’exemple de [begin](#begin) pour obtenir un exemple qui utilise `const_iterator`.

## <a name="const_pointer"></a>  hash_multimap::const_pointer

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un pointeur vers un élément **const** dans un hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet hash_multimap.

## <a name="const_reference"></a>  hash_multimap::const_reference

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit une référence à un élément **const** stocké dans un hash_multimap pour la lecture et l’exécution d’opérations **const**.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multimap::const_reverse_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire tout élément **const** dans le hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer le hash_multimap dans l’ordre inverse.

Le `const_reverse_iterator` défini par hash_multimap pointe vers des objets de [value_type](#value_type), qui sont de type `pair<const Key, Type>`, dont le premier membre est la clé à l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.

Pour déréférencer un `const_reverse_iterator` `crIter` pointant vers un élément dans un hash_multimap, utilisez le `->` opérateur.

Pour accéder à la valeur de la clé pour l’élément, utilisez `crIter->first`, ce qui équivaut à `(*crIter).first`. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `crIter->second`, ce qui équivaut à `(*crIter).second`.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `const_reverse_iterator`, consultez l’exemple [rend](#rend).

## <a name="count"></a>  hash_multimap::count

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne le nombre d'éléments d'un hash_multimap dont la clé correspond à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
 Clé des éléments à mettre en correspondance à partir du hash_multimap.

### <a name="return-value"></a>Valeur de retour

1 si le hash_multimap contient un élément dont la clé de tri correspond à la clé du paramètre ; 0 si le hash_multimap ne contient pas d'élément avec une clé correspondante.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d'éléments dans la plage

**[lower_bound (** `key` **), upper_bound (** `key` **) )**

qui ont une valeur de clé *clé*.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multimap::count.

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
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
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  hash_multimap::crbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur const qui traite le premier élément d’un hash_multimap inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite le premier élément d’un [hash_multimap](../standard-library/hash-multimap-class.md) inversé ou qui traite ce qui était le dernier élément de l’objet `hash_multimap` non inversé.

### <a name="remarks"></a>Notes

`crbegin` est utilisé avec un hash_multimap inversé comme [hash_multimap::begin](#begin) est utilisé avec un `hash_multimap`.

Avec la valeur de retour `crbegin`, l'objet `hash_multimap` ne peut pas être changé.

Vous pouvez utiliser `crbegin` pour itérer un `hash_multimap` vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="crend"></a>  hash_multimap::crend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un hash_multimap inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un [hash_multimap](../standard-library/hash-multimap-class.md) inversé (emplacement qui précédait celui du premier élément du `hash_multimap` non inversé).

### <a name="remarks"></a>Notes

`crend` est utilisé avec un hash_multimap inversé comme [hash_multimap::end](#end) est utilisé avec un hash_multimap.

Avec la valeur de retour `crend`, l'objet `hash_multimap` ne peut pas être changé.

Vous pouvez utiliser `crend` pour déterminer si un itérateur inversé a atteint la fin de son hash_multimap.

La valeur retournée par `crend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="difference_type"></a>  hash_multimap::difference_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type entier signé qui peut être utilisé pour représenter le nombre d’éléments d’un hash_multimap au sein d’une plage, parmi les éléments pointés par les itérateurs.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

`difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type` est généralement utilisé pour représenter le nombre d’éléments de la plage *[ first,  last)* entre les itérateurs `first` et `last`. Il inclut l’élément sur lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) sur lequel pointe `last`.

Notez que même si `difference_type` est disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui inclut la classe des itérateurs bidirectionnels prise en charge par les conteneurs réversibles tels que set, la soustraction entre les itérateurs est prise en charge uniquement par les itérateurs à accès aléatoire fournis par un conteneur à accès aléatoire (vector, par exemple).

### <a name="example"></a>Exemple

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="emplace"></a>  hash_multimap::emplace

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Insère un élément construit sur place dans un hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur utilisée pour construire un élément à insérer dans le [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Valeur de retour

La fonction membre `emplace` retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré.

### <a name="remarks"></a>Notes

Le [hash_multimap::value_type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
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

## <a name="emplace_hint"></a>  hash_multimap::emplace_hint

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Insère un élément construit sur place dans un hash_multimap, avec un indicateur de positionnement.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur utilisée pour déplacer un élément à insérer dans le [hash_multimap](../standard-library/hash-multimap-class.md), sauf si le `hash_multimap` contient déjà cet élément (ou, plus généralement, s’il contient déjà un élément dont la clé est ordonnée de façon équivalente).|
|*_WHERE*|Indicateur concernant l’emplacement où commencer à rechercher le point d’insertion correct.|

### <a name="return-value"></a>Valeur de retour

La fonction membre [hash_multimap::emplace](#emplace) retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré dans le `hash_multimap`.

### <a name="remarks"></a>Notes

Le [hash_multimap::value_type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

L’insertion peut se produire dans le temps fixe amorti, plutôt que de temps logarithmique, si le point d’insertion suit immédiatement *_Where*.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
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

## <a name="empty"></a>  hash_multimap::empty

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Teste si un hash_multimap est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le hash_multimap est vide. **false** si le hash_multimap n’est pas vide.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="end"></a>  hash_multimap::end

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément du hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite l’emplacement suivant le dernier élément d’un hash_multimap. Si le hash_multimap est vide, hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Notes

`end` est utilisé pour déterminer si un itérateur a atteint la fin de son hash_multimap.

La valeur retournée par `end` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
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

## <a name="equal_range"></a>  hash_multimap::equal_range

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne une paire d’itérateurs, respectivement au premier élément d’un hash_multimap ayant une clé supérieure à celle spécifiée et au premier élément d’un hash_multimap ayant une clé supérieure ou égale à la clé spécifiée.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
 Clé d’argument à comparer à la clé de tri d’un élément du hash_multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

Paire d’itérateurs telle que le premier est la [lower_bound](#lower_bound) de la clé et le second est la [upper_bound](#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **first**, et pour déréférencer l’itérateur de la limite inférieure, utilisez \*( `pr`. **first**). Pour accéder au deuxième itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **second**, et pour déréférencer l’itérateur de la limite supérieure, utilisez \*( `pr`. **second**).

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2\n in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2\n in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
 in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
 in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  hash_multimap::erase

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un hash_multimap ou supprime les éléments qui correspondent à une clé spécifiée.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Paramètres

*_WHERE*<br/>
 Position de l'élément à supprimer du hash_multimap.

*first*<br/>
 Position du premier élément supprimé du hash_multimap.

*last*<br/>
 Position juste après le dernier élément supprimé du hash_multimap.

*key*<br/>
 Clé des éléments à supprimer du hash_multimap.

### <a name="return-value"></a>Valeur de retour

Pour les deux premières fonctions membres, il s'agit d'un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un pointeur vers la fin du hash_multimap si aucun élément de ce genre n'existe.

Pour la troisième fonction membre, il s'agit du nombre d'éléments qui ont été supprimés du hash_multimap.

### <a name="remarks"></a>Notes

Les fonctions membres ne lèvent jamais d'exception.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multimap::erase.

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << " the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << " 2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
 the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
 2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="find"></a>  hash_multimap::find

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur qui traite le premier emplacement d’un élément dans un hash_multimap ayant une clé équivalente à une clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
 Clé qui doit correspondre à la clé de tri d’un élément du hash_multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier emplacement d’un élément ayant la clé spécifiée, ou l’emplacement qui suit le dernier élément du hash_multimap, si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur qui traite un élément du hash_multimap dont la clé de tri est `equivalent` à l’argument key sous un prédicat binaire qui induit un ordonnancement basé sur une relation d’infériorité.

Si la valeur de retour de `find` est affectée à un `const_iterator`, l’objet hash_multimap ne peut pas être changé. Si la valeur de retour de `find` est affecté à un `iterator`, l’objet hash_multimap peut être modifié.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="get_allocator"></a>  hash_multimap::get_allocator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne une copie de l’objet allocateur utilisé pour construire le hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Allocateur utilisé par le hash_multimap.

### <a name="remarks"></a>Notes

Les allocateurs de la classe hash_multimap spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de bibliothèque C++ Standard suffisent à satisfaire la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
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

## <a name="hash_multimap"></a>  hash_multimap::hash_multimap

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Construit un hash_multimap vide ou une copie de l’ensemble ou d’une partie d’un autre hash_multimap.

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);


hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
 InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
 InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Al*|Classe d’allocateur de stockage à utiliser pour cet objet hash_multimap, qui est par défaut `Allocator`.|
|*Comp.*|Fonction de comparaison de type `const Traits` utilisée pour ordonner les éléments dans le mappage (par défaut, `Traits`).|
|*Droite*|Classe map dont l’ensemble construit doit être une copie.|
|*Premier*|Position du premier élément de la plage d'éléments à copier.|
|*Dernière*|Position du premier élément au-delà de la plage d'éléments à copier.|
|*IList*|Initializer_list à partir duquel copier.|

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du hash_multimap et peut être retourné ultérieurement en appelant [get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leur hash_multimap.

Tous les constructeurs stockent un objet de fonction de type `Traits`, qui est utilisé pour établir un ordre parmi les clés du hash_multimap et qui peut être retourné ultérieurement en appelant [key_comp](#key_comp).

Les trois premiers constructeurs spécifient un hash_multimap initial vide ; le deuxième spécifie le type de fonction de comparaison (*Comp*) à utiliser pour établir l’ordre des éléments et le troisième explicitement Spécifie le type d’allocateur (`_Al`) à utiliser. Le mot clé `explicit` supprime certains genres de conversions de type automatiques.

Le quatrième constructeur spécifie une copie du hash_multimap `Right`.

Les trois constructeurs suivants copient la plage `First, Last)` d’une classe map avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison de la classe `Traits` et de l’allocateur.

Le huitième constructeur déplace le hash_multimap `Right`.

Les trois derniers constructeurs utilisent un initializer_list.

## <a name="insert"></a>  hash_multimap::insert

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Insère un élément ou une plage d’éléments dans une classe hash_multimap.

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

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
|*Val*|Valeur d’un élément à insérer dans la classe hash_multimap sauf si elle contient déjà cet élément ou, plus généralement, si elle contient déjà un élément dont la clé est classée de façon équivalente.|
|*Where*|Indication de l’emplacement de départ de la recherche du point d’insertion correct.|
|*Premier*|Position du premier élément à copier à partir d’une carte.|
|*Dernière*|Position juste au-delà du dernier élément à copier à partir d’une carte.|

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions membres `insert` retournent un itérateur qui pointe vers l’emplacement d’insertion du nouvel élément.

La troisième fonction membre utilise un initializer_list pour les éléments à insérer.

La quatrième fonction membre insère la séquence de valeurs d’éléments dans une carte qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` d’un jeu spécifié.

Les deux dernières fonctions membres `insert` ont le même comportement que les deux premières, sauf qu’elles déplacent/construisent la valeur insérée.

### <a name="remarks"></a>Notes

Le [value-type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.

L’insertion peut se produire dans le temps fixe amorti pour la version indicative de `insert`, au lieu de temps logarithmique, si le point d’insertion suit immédiatement *où*.

## <a name="iterator"></a>  hash_multimap::iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Notes

Le `iterator` défini par hash_multimap pointe vers des objets de [value_type](#value_type), qui sont de type `pair` \< **const Key, Type**>, dont le premier membre est la clé à l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.

Pour déréférencer un **itérateur** `Iter` pointant vers un élément dans un hash_multimap, utilisez le `->` opérateur.

Pour accéder à la valeur de la clé de l’élément, utilisez `Iter` -> **first**, ce qui équivaut à (\* `Iter`). **first**. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `Iter` -> **second**, ce qui équivaut à (\* `Iter`). **first**.

Un type `iterator` peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="key_comp"></a>  hash_multimap::key_comp

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Récupère une copie de l’objet de comparaison utilisé pour trier les clés dans un hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’objet de fonction utilisé par un hash_multimap pour ordonner ses éléments.

### <a name="remarks"></a>Notes

L’objet stocké définit la fonction membre

**bool operator(const Key&** `left` **, const Key&** `right` **);**

qui retourne **true** si `left` précède et n’est pas égal à `right` dans l’ordre de tri.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multimap::key_compare

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l’ordre relatif de deux éléments dans le hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Notes

`key_compare` est un synonyme du paramètre de modèle *Traits*.

Pour plus d’informations sur *Traits* voir le [hash_multimap, classe](../standard-library/hash-multimap-class.md) rubrique.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_compare`, consultez l’exemple de [key_comp](#key_comp).

## <a name="key_type"></a>  hash_multimap::key_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui décrit l’objet de clé de tri qui constitue chaque élément du hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

`key_type` est un synonyme du paramètre de modèle *clé*.

Pour plus d’informations sur *clé*, consultez la section Notes de la [hash_multimap, classe](../standard-library/hash-multimap-class.md) rubrique.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_compare`, consultez l’exemple de [value_type](#value_type).

## <a name="lower_bound"></a>  hash_multimap::lower_bound

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur au premier élément d’un hash_multimap avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
 Clé d’argument à comparer à la clé de tri d’un élément du hash_multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement d’un élément dans un hash_multimap ayant une clé supérieure ou égale à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_multimap si aucune correspondance n’est trouvée pour la clé.

Si la valeur de retour de `lower_bound` est affectée à un `const_iterator`, l’objet hash_multimap ne peut pas être changé. Si la valeur de retour de `lower_bound` est affecté à un `iterator`, l’objet hash_multimap peut être modifié.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << " that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
 that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="mapped_type"></a>  hash_multimap::mapped_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui représente le type de données stockées dans un hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Notes

`mapped_type` est un synonyme du paramètre de modèle *Type*.

Pour plus d’informations sur *Type* voir le [hash_multimap, classe](../standard-library/hash-multimap-class.md) rubrique.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `key_type`, consultez l’exemple de [value_type](#value_type).

## <a name="max_size"></a>  hash_multimap::max_size

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne la longueur maximale du hash_multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur maximale autorisée du hash_multimap.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multimap::operator=

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Remplace les éléments du hash_multimap par une copie d’un autre hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*right*|[hash_multimap](../standard-library/hash-multimap-class.md) copié dans le `hash_multimap`.|

### <a name="remarks"></a>Notes

Après avoir supprimé les éléments existants dans un `hash_multimap`, `operator=` copie ou déplace le contenu de *droit* dans le `hash_multimap`.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>  hash_multimap::pointer

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un pointeur vers un élément d’un hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Notes

Un type `pointer` peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet hash_multimap.

## <a name="rbegin"></a>  hash_multimap::rbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur traitant le premier élément d’un hash_multimap inversé.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé traitant le premier élément d’un hash_multimap inversé ou traitant ce qui était le dernier élément du hash_multimap non inversé.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec un hash_multimap inversé comme [begin](#begin) est utilisé avec un hash_multimap.

Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator`, l’objet hash_multimap ne peut pas être changé. Si la valeur de retour de `rbegin` est assignée à un `reverse_iterator`, l’objet hash_multimap peut être changé.

Vous pouvez utiliser `rbegin` pour itérer un hash_multimap vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element"
        << "\n in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
 in the reversed hash_multimap is 2.
```

## <a name="reference"></a>  hash_multimap::reference

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit une référence à un élément stocké dans un hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  hash_multimap::rend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un hash_multimap inversé.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un hash_multimap inversé (emplacement qui précédait celui du premier élément du hash_multimap non inversé).

### <a name="remarks"></a>Notes

`rend` est utilisé avec un hash_multimap inversé comme [end](#end) est utilisé avec un hash_multimap.

Si la valeur de retour de `rend` est affectée à un [const_reverse_iterator](#const_reverse_iterator), l’objet hash_multimap ne peut pas être changé. Si la valeur de retour de `rend` est affectée à un [reverse_iterator](#reverse_iterator), l’objet hash_multimap peut être changé.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son hash_multimap.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="reverse_iterator"></a>  hash_multimap::reverse_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_multimap inversé.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `reverse_iterator` est utilisé pour itérer le hash_multimap dans l’ordre inverse.

Le `reverse_iterator` défini par le hash_multimap pointe vers des objets de [value_type](#value_type), qui sont de type `pair`\< **const Key, Type**>. La valeur de la clé est disponible par l’intermédiaire du premier membre de la paire, et la valeur de l’élément mappé est disponible par l’intermédiaire du deuxième membre de la paire.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="size"></a>  hash_multimap::size

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne le nombre d'éléments figurant dans le hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du hash_multimap.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_multimap::size.

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="size_type"></a>  hash_multimap::size_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type entier non signé qui compte le nombre d’éléments d’un hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `size_type`, consultez l’exemple [size](#size).

## <a name="swap"></a>  hash_multimap::swap

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Échange les éléments de deux hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
 hash_multimap qui fournit les éléments à échanger ou hash_multimap dont les éléments doivent être échangés avec ceux du hash_multimap.

### <a name="remarks"></a>Notes

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux hash_multimaps dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="upper_bound"></a>  hash_multimap::upper_bound

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Retourne un itérateur au premier élément d’un hash_multimap avec une valeur de clé supérieure à celle de la clé spécifiée.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
 Clé d’argument à comparer à la clé de tri d’un élément du hash_multimap dans lequel la recherche est effectuée.

### <a name="return-value"></a>Valeur de retour

[iterator](#iterator) ou [const_iterator](#const_iterator) qui traite l’emplacement d’un élément dans un hash_multimap ayant une clé supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_multimap si aucune correspondance n’est trouvée pour la clé.

Si la valeur de retour de `upper_bound` est affectée à un `const_iterator`, l’objet hash_multimap ne peut pas être changé. Si la valeur de retour de `upper_bound` est affecté à un `iterator`, l’objet hash_multimap peut être modifié.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n with a key "
        << " greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << " that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
 with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
 that of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>  hash_multimap::value_comp

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

La fonction membre retourne un objet de fonction qui détermine l’ordre des éléments d’un hash_multimap en comparant leurs valeurs de clés.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’objet de fonction de comparaison utilisé par un hash_multimap pour ordonner ses éléments.

### <a name="remarks"></a>Notes

Pour un hash_multimap *m*, si deux éléments *e*1( *k*1 *, d*1) and *e*2( *k*2 *, d*2) sont des objets de type [value_type](#value_type), où *k*1 et *k*2 ont des clés de type [key_type](#key_type) et `d`1 et `d`2 ont des données de type [mapped_type](#mapped_type), alors *m.*`value_comp`( )( *e*1 *, e*2) équivaut à *m.*`key_comp`( ) ( *k*1 *, k*2). Un objet stocké définit la fonction membre

**bool operator**( **value_type&**`left`, **value_type&** `right`);

qui retourne **true** si la valeur de clé de `left` précède et n’est pas égale à la valeur clé de `right` dans l’ordre de tri.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

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

## <a name="value_type"></a>  hash_multimap::value_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Type qui représente le type d’objet stocké dans un hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Notes

`value_type` est déclaré comme étant paire\<const [key_type](#key_type), [mapped_type](#mapped_type)> et ne Couplez pas\<key_type, mapped_type >, car les clés d’un conteneur associatif ne peuvent pas être modifiées. à l’aide d’un itérateur non constant ou une référence.

### <a name="example"></a>Exemple

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitely to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
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
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
