---
title: hash_set, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81c7572ffd5a53456cd4555b82a8d3e235286339
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961706"
---
# <a name="hashset-class"></a>hash_set, classe

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

La classe conteneur hash_set est une extension de la bibliothèque standard C++, et elle est utilisée pour le stockage et la récupération rapide des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Paramètres

*Clé* type de données de l’élément à stocker dans le hash_set.

*Caractéristiques* type qui inclut les deux objets de fonction, une de la classe comparaison qui est un prédicat binaire capable de comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif et une fonction de hachage est un opérateur unaire prédicat mapper des valeurs clés de la éléments à des entiers non signés de type `size_t`. Cet argument est facultatif et le `hash_compare` *< clé,* **moins ***\<clé >>* est la valeur par défaut.

*Allocateur* le type qui représente l’objet allocateur stocké qui encapsule des informations sur le hash_set allocation et désallocation de mémoire. Cet argument est facultatif et la valeur par défaut est **allocateur ***\<clé >.*

## <a name="remarks"></a>Notes

L'objet hash_set est :

- Un conteneur associatif de taille variable qui prend en charge la récupération efficace des valeurs d'éléments selon une valeur de clé associée. C'est également un conteneur associatif simple, car les valeurs de ses éléments sont ses valeurs de clés.

- Réversible, car elle fournit un itérateur bidirectionnel pour accéder à ses éléments

- Haché, car ses éléments sont regroupés dans des compartiments selon la valeur d'une fonction de hachage appliquée aux valeurs de clé des éléments.

- Unique dans le sens où chacun de ses éléments doit avoir une clé unique. Comme hash_set est également un simple conteneur associatif, ses éléments sont également uniques.

- Une classe de modèle, car la fonctionnalité qu'elle fournit est générique et donc indépendante du type spécifique des données contenues comme éléments ou comme clés. Les types de données utilisés pour les éléments et les clés sont eux spécifiés comme paramètres dans la classe de modèle avec la fonction de comparaison et l'allocateur.

Le principal avantage du hachage sur le tri est une meilleure efficacité : un hachage réussi effectue des insertions, des suppressions et trouve ce qui est recherché dans un délai moyen constant, alors que pour les techniques de tri, ce délai est proportionnel au logarithme du nombre d'éléments du conteneur. La valeur d'un élément appartenant à une classe set ne peut pas être modifiée directement. Vous devez supprimer les anciennes valeurs et insérer les éléments ayant de nouvelles valeurs.

Le choix du type de conteneur doit être basé en général sur le type de la recherche et de l'insertion requis par l'application. Les conteneurs associatifs hachés sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations sont efficaces quand elles sont utilisées avec une fonction de hachage bien conçue, car elles les exécutent dans un délai qui est en moyenne constant et ne dépend pas du nombre d'éléments dans le conteneur. Une fonction de hachage bien conçue produit une distribution uniforme des valeurs de hachage et réduit le nombre de collisions, qui se produisent quand des valeurs de clés distinctes sont mappées dans la même valeur de hachage. Dans le pire des cas, avec la pire des fonctions de hachage possible, le nombre d'opérations est proportionnel au nombre d'éléments de la séquence (délai linéaire).

La classe hash_set doit être sélectionnée comme conteneur associatif lorsque les conditions associant les valeurs à leurs clés sont remplies par l'application. Les éléments d'une classe hash_set sont uniques et agissent comme leurs propres clés de tri. Pour ce type de structure, il peut s'agir d'une liste triée de mots qui ne peuvent apparaître qu'une seule fois. Si plusieurs occurrences d'un mot sont autorisées, un objet hash_multiset est la structure de conteneur appropriée. Si les valeurs doivent être jointes à une liste de mots clés uniques, il convient d'utiliser une classe hash_map comme conteneur de données. Si les clés ne sont pas uniques, c'est une classe hash_multimap qu'il convient d'utiliser comme conteneur.

L’objet hash_set ordonne la séquence qu’il contrôle en appelant un hachage stocké `Traits` objet de type [value_compare](#value_compare). Cet objet stocké est accessible en appelant la fonction membre [key_comp](#key_comp). Cet objet de fonction doit se comporter comme un objet de la classe *hash_compare<Key, less\<Key> >.* En particulier, pour toutes les valeurs `key` de type Key, l’appel Trait (`key`) génère une distribution des valeurs de type size_t.

En général, les éléments ne doivent pas être tout à fait comparables, afin que, à l'aide de deux événements quelconques donnés, il soit possible de déterminer, soit qu'ils soient équivalents (dans le sens où l'un n'est pas inférieur à l'autre), soit que l'un est inférieur à l'autre. Ceci entraîne un ordonnancement entre les éléments non équivalents. D'un point de vue plus technique, la fonction de comparaison est un prédicat binaire qui induit un ordre faible strict au sens mathématique du terme. Un prédicat binaire *f*( *x*, *y*) est un objet de fonction qui a deux objets d’arguments x et y, et la valeur de retour true ou false. Un tri appliqué à un objet hash_set est un ordonnancement faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l’équivalence est transitive, où deux objets *x* et *y* sont définis comme équivalents quand *f*( *x*, *y*) et *f*( *y*, *x*) ont la valeur false. Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.

L'ordre réel des éléments de la séquence contrôlée dépend de la fonction de hachage, de la fonction d'ordonnancement et de la taille actuelle de la table de hachage stockée dans l'objet conteneur. Vous ne pouvez pas déterminer la taille actuelle de la table de hachage, et vous ne pouvez donc généralement pas prédire l'ordre des éléments dans la séquence contrôlée. L'insertion d'éléments ne rend aucun itérateur non valide. La suppression d'éléments rend uniquement non valides les itérateurs qui pointaient spécifiquement vers les éléments supprimés.

L’itérateur fourni par la classe hash_set est un itérateur bidirectionnel. Toutefois, les fonctions membres de classe [insert](#insert) et [hash_set](#hash_set) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences de fonctionnalités sont minimales par rapport à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs forment une famille liée par les améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre ensemble de spécifications, et les algorithmes qui fonctionnent avec eux doivent limiter leurs hypothèses aux spécifications fournies par ce type d'itérateur. On peut considérer qu'un itérateur d'entrée peut être déréférencé pour faire référence à un objet et qu'il peut être incrémenté à l'itérateur suivant dans la séquence. Il s’agit d’un ensemble minimal de fonctionnalités, mais c’est suffisant pour pouvoir parler d’une plage d’itérateurs [ `first`, `last`) dans le contexte des fonctions membres de classe.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[hash_set](#hash_set)|Construit un `hash_set` vide ou une copie de l'ensemble ou d'une partie d'un autre `hash_set`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` pour l'objet `hash_set`.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un élément `const` dans le `hash_set`.|
|[const_pointer](#const_pointer)|Un type qui fournit un pointeur vers un **const** élément dans un `hash_set`.|
|[const_reference](#const_reference)|Type qui fournit une référence à un **const** élément stocké dans un `hash_set` pour lire et effectuer **const** operations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire un **const** élément dans le `hash_set`.|
|[difference_type](#difference_type)|Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'un `hash_set` au sein d'une plage, parmi les éléments pointés par les itérateurs.|
|[iterator](#iterator)|Type qui fournit un itérateur bidirectionnel, qui peut lire ou modifier tout élément d'un objet `hash_set`.|
|[key_compare](#key_compare)|Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments au sein d'un `hash_set`.|
|[key_type](#key_type)|Type qui décrit un objet stocké comme élément d'un objet `hash_set` dans sa capacité comme clé de tri.|
|[pointer](#pointer)|Type qui fournit un pointeur vers un élément d'un objet `hash_set`.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans un `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d'un `hash_set` inversé.|
|[size_type](#size_type)|Type entier non signé qui peut représenter le nombre d'éléments dans un `hash_set`.|
|[value_compare](#value_compare)|Type qui fournit deux objets de fonction, un prédicat binaire de la comparaison de classe qui peut comparer deux valeurs d'éléments d'un `hash_set` pour déterminer leur ordre relatif et un prédicat unaire qui hache les éléments.|
|[value_type](#value_type)|Type qui décrit un objet stocké comme élément d'un objet `hash_set` dans sa capacité comme valeur.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[begin](#begin)|Retourne un itérateur qui référence le premier élément d'un objet `hash_set`.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_set`.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'un `hash_set`.|
|[clear](#clear)|Efface tous les éléments d'un `hash_set`.|
|[count](#count)|Retourne le nombre d'éléments d'un `hash_set` dont la clé correspond à une clé spécifiée par un paramètre.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'un `hash_set` inversé.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'un `hash_set` inversé.|
|[emplace](#emplace)|Insère un élément construit sur place dans un `hash_set`.|
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans un `hash_set`, avec un indicateur de positionnement.|
|[empty](#empty)|Vérifie si un `hash_set` est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_set`.|
|[equal_range](#equal_range)|Retourne une paire d'itérateurs, respectivement vers le premier élément d'un objet `hash_set` avec une clé supérieure à une clé spécifiée, et vers le premier élément d'un objet `hash_set` avec une clé supérieure ou égale à la clé.|
|[erase](#erase)|Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans un `hash_set` ou supprime les éléments qui correspondent à une clé spécifiée.|
|[find](#find)|Retourne un itérateur qui référence l'emplacement d'un élément d'un objet `hash_set` qui a une clé équivalente à une clé spécifiée.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire le `hash_set`.|
|[insert](#insert)|Insère un élément ou une plage d'éléments dans un `hash_set`.|
|[key_comp](#key_comp)|Récupère une copie de l'objet de comparaison utilisé pour trier les clés au sein d'un `hash_set`.|
|[lower_bound](#lower_bound)|Retourne un itérateur au premier élément d'un `hash_set` avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale du `hash_set`.|
|[rbegin](#rbegin)|Retourne un itérateur qui traite le premier élément d'un `hash_set` inversé.|
|[rend](#rend)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un `hash_set` inversé.|
|[size](#size)|Retourne le nombre d'éléments d'un `hash_set`.|
|[swap](#swap)|Échange les éléments de deux `hash_set`.|
|[upper_bound](#upper_bound)|Retourne un itérateur au premier élément d'un `hash_set` avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.|
|[value_comp](#value_comp)|Récupère une copie de l'objet de caractéristiques de hachage utilisé pour hacher et ordonner les valeurs des clés d'éléments dans un objet `hash_set`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[hash_set::operator=](#op_eq)|Remplace les éléments d'un `hash_set` par une copie d'un autre `hash_set`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<hash_set>

**Espace de noms :** stdext

## <a name="allocator_type"></a>  hash_set::allocator_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type représentant la classe allocator pour l’objet hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Notes

`allocator_type` est un synonyme du paramètre de modèle *allocateur*.

Pour plus d’informations sur *allocateur*, consultez la section Notes de la [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

### <a name="example"></a>Exemple

Consultez l’exemple de [get_allocator](#get_allocator) pour obtenir un exemple qui utilise `allocator_type`.

## <a name="begin"></a>  hash_set::begin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur qui traite le premier élément d’une classe hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite le premier élément du hash_set ou l’emplacement qui suit un hash_set vide.

### <a name="remarks"></a>Notes

Si la valeur de retour de `begin` est affecté à un `const_iterator`, les éléments de l’objet hash_set ne peut pas être modifiés. Si la valeur de retour de `begin` est affecté à un `iterator`, les éléments de l’objet hash_set peuvent être modifiés.

### <a name="example"></a>Exemple

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="cbegin"></a>  hash_set::cbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur const qui traite le premier élément du hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite le premier élément du [hash_set](../standard-library/hash-set-class.md) ou l’emplacement qui suit un `hash_set` vide.

### <a name="remarks"></a>Notes

Avec la valeur de retour `cbegin`, les éléments de l’objet `hash_set` ne peuvent pas être modifiés.

### <a name="example"></a>Exemple

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="cend"></a>  hash_set::cend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur const qui traite l’emplacement situé après le dernier élément d’un hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel const qui traite l’emplacement suivant le dernier élément d’un [hash_set](../standard-library/hash-set-class.md). Si le `hash_set` est vide, `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Notes

`cend` est utilisé pour déterminer si un itérateur a atteint la fin de son `hash_set`. La valeur retournée par `cend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="clear"></a>  hash_set::clear

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Efface tous les éléments d’un hash_set.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="const_iterator"></a>  hash_set::const_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire un élément **const** dans le hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [begin](#begin) pour obtenir un exemple qui utilise `const_iterator`.

## <a name="const_pointer"></a>  hash_set::const_pointer

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un pointeur vers un élément **const** dans un hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Notes

Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément.

Dans la plupart des cas, vous devez utiliser un [iterator const](#const_iterator) pour accéder aux éléments dans un objet **const** hash_set.

## <a name="const_reference"></a>  hash_set::const_reference

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit une référence à un élément **const** stocké dans un hash_set pour la lecture et l’exécution d’opérations **const**.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="const_reverse_iterator"></a>  hash_set::const_reverse_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire tout élément **const** dans le hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `const_reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer le hash_set dans l’ordre inverse.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [rend](#rend) pour découvrir comment déclarer et utiliser le `const_reverse_iterator`.

## <a name="count"></a>  hash_set::count

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne le nombre d'éléments d'une classe hash_set dont la clé correspond à une clé spécifiée par un paramètre.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*clé* la clé des éléments à mettre en correspondance du hash_set.

### <a name="return-value"></a>Valeur de retour

1 si la classe hash_set contient un élément dont la clé de tri correspond à la clé de paramètre.

0 si la classe hash_set ne contient pas d'élément avec une clé correspondante.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d'éléments dans la plage suivante :

[ **lower_bound** (_ *Key* ), **upper_bound** (\_ *Key* ) ).

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_set::count.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_set::crbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur const qui traite le premier élément d’un hash_set inversé.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite le premier élément d’un [hash_set](../standard-library/hash-set-class.md) inversé ou qui traite ce qui était le dernier élément de l’objet `hash_set` non inversé.

### <a name="remarks"></a>Notes

`crbegin` est utilisé avec un hash_set inversé comme [hash_set::begin](#begin) est utilisé avec un hash_set.

Avec la valeur de retour `crbegin`, l'objet `hash_set` ne peut pas être changé.

Vous pouvez utiliser `crbegin` pour itérer un `hash_set` vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="crend"></a>  hash_set::crend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’un hash_set inversé.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’un [hash_set](../standard-library/hash-set-class.md) inversé (emplacement qui précédait celui du premier élément du `hash_set` non inversé).

### <a name="remarks"></a>Notes

`crend` est utilisé avec un `hash_set` inversé comme [hash_set::end](#end) est utilisé avec un `hash_set`.

Avec la valeur de retour `crend`, l'objet `hash_set` ne peut pas être changé.

`crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son objet `hash_set`.

### <a name="example"></a>Exemple

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="difference_type"></a>  hash_set::difference_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type entier signé qui peut être utilisé pour représenter le nombre d’éléments d’une classe hash_set dans une plage, parmi les éléments pointés par les itérateurs.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

`difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type` est généralement utilisé pour représenter le nombre d’éléments de la plage [ `first`, `last`) entre les itérateurs `first` et `last`. Il inclut l’élément vers lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) vers lequel pointe `last`.

Notez que même si `difference_type` est disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui inclut la classe des itérateurs bidirectionnels prise en charge par les conteneurs réversibles tels que set, la soustraction entre les itérateurs n’est prise en charge que par les itérateurs à accès aléatoire fournis par un conteneur à accès aléatoire, par exemple vector ou deque.

### <a name="example"></a>Exemple

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="emplace"></a>  hash_set::emplace

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Insère un élément construit sur place dans un hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur d’un élément à insérer dans le [hash_set](../standard-library/hash-set-class.md), sauf si le `hash_set` contient déjà cet élément ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente.|

### <a name="return-value"></a>Valeur de retour

Le `emplace` fonction membre retourne une paire dont **bool** composant retourne **true** si une insertion a été effectuée et **false** si le `hash_set` déjà contient un élément dont la clé avait une valeur équivalente dans l’ordre, et dont le composant itérateur retourne l’adresse où un nouvel élément a été inséré ou où l’élément se trouvait déjà.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="emplace_hint"></a>  hash_set::emplace_hint

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Insère un élément construit sur place dans un hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur d’un élément à insérer dans le [hash_set](../standard-library/hash-set-class.md), sauf si le `hash_set` contient déjà cet élément ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente.|
|*_WHERE*|Emplacement où commencer à rechercher le point d'insertion correct. (L’insertion peut se produire dans le temps fixe amorti, plutôt que de temps logarithmique, si le point d’insertion suit immédiatement *_Where*.)|

### <a name="return-value"></a>Valeur de retour

La fonction membre [hash_set::emplace](#emplace) retourne un itérateur qui pointe vers l’emplacement où le nouvel élément a été inséré dans le `hash_set`, ou vers l’emplacement où se trouve l’élément existant avec un ordonnancement équivalent.

### <a name="remarks"></a>Notes

L’insertion peut se produire dans le temps fixe amorti, plutôt que de temps logarithmique, si le point d’insertion suit immédiatement *_Where*.

### <a name="example"></a>Exemple

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="empty"></a>  hash_set::empty

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Vérifie si un hash_set est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le hash_set est vide. **false** si le hash_set n’est pas vide.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="end"></a>  hash_set::end

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément du hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel qui traite l’emplacement suivant le dernier élément d’un hash_set. Si le hash_set est vide, hash_set::end == hash_set::begin.

### <a name="remarks"></a>Notes

`end` est utilisé pour déterminer si un itérateur a atteint la fin de son hash_set. La valeur retournée par `end` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="equal_range"></a>  hash_set::equal_range

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne une paire d’itérateurs, respectivement, au premier élément d’un hash_set et ayant une clé égale à celle spécifiée, et au premier élément du hash_set ayant une clé supérieure à la clé spécifiée.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Paramètres

*clé* la clé d’argument à comparer avec la clé de tri d’un élément du hash_set recherché.

### <a name="return-value"></a>Valeur de retour

Paire d’itérateurs telle que le premier est la [lower_bound](../standard-library/set-class.md#lower_bound) de la clé et le second est la [upper_bound](../standard-library/set-class.md#upper_bound) de la clé.

Pour accéder au premier itérateur d’une paire retournée par la fonction membre, utilisez `pr`. **first**, et pour déréférencer l’itérateur de la limite inférieure, utilisez \*( `pr`. **first**). Pour accéder au second itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **second**, et pour déréférencer l’itérateur de la limite supérieure (upper_bound), utilisez \*( `pr`. **second**).

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="erase"></a>  hash_set::erase

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Supprime d'un emplacement spécifié un élément ou une plage d'éléments compris dans une classe hash_set ou supprime les éléments qui correspondent à une clé spécifiée.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Paramètres

*_WHERE* position de l’élément à supprimer du hash_set.

*première* Position du premier élément supprimé du hash_set.

*dernière* Position juste après le dernier élément supprimé du hash_set.

*clé* la clé des éléments à supprimer du hash_set.

### <a name="return-value"></a>Valeur de retour

Pour les deux premières fonctions membres, il s'agit d'un itérateur bidirectionnel qui désigne le premier élément restant après tous les éléments supprimés, ou un pointeur vers la fin du hash_set si aucun élément de ce genre n'existe. Pour la troisième fonction membre, il s'agit du nombre d'éléments qui ont été supprimés du hash_set.

### <a name="remarks"></a>Notes

Les fonctions membres ne lèvent jamais d'exception.

### <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation de la fonction membre hash_set::erase.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="find"></a>  hash_set::find

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur qui traite le premier emplacement d’un élément d’un hash_set ayant une clé équivalente à une clé spécifiée.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Paramètres

*clé* la clé d’argument qui doit correspondre à la clé de tri d’un élément du hash_set recherché.

### <a name="return-value"></a>Valeur de retour

Un `iterator` ou `const_iterator` qui traite l’emplacement d’un élément équivalent à la clé spécifiée ou qui traite l’emplacement suivant le dernier élément dans le hash_set si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur qui traite un élément du hash_set dont la clé de tri est `equivalent` à l’argument key sous un prédicat binaire qui induit un ordonnancement basé sur une-relation d’infériorité.

Si la valeur de retour de `find` est affecté à un `const_iterator`, l’objet hash_set ne peut pas être modifié. Si la valeur de retour de `find` est affecté à un `iterator`, l’objet hash_set peut être modifié.

### <a name="example"></a>Exemple

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_set::get_allocator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne une copie de l’objet allocateur utilisé pour construire le hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Allocateur utilisé par l’objet hash_set pour gérer la mémoire, ce qui est le paramètre de modèle *allocateur*.

Pour plus d’informations sur *allocateur*, consultez la section Notes de la [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

### <a name="remarks"></a>Notes

Les allocateurs de la classe hash_set spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de bibliothèque C++ Standard suffisent à satisfaire la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_set"></a>  hash_set::hash_set

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Construit un `hash_set` vide ou une copie de l'ensemble ou d'une partie d'un autre `hash_set`.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Al*|Classe d’allocateur de stockage à utiliser pour cet objet `hash_set`, qui est par défaut `Allocator`.|
|*Comp.*|Fonction de comparaison de type `const Traits` utilisée pour ordonner les éléments dans le `hash_set` (par défaut, `hash_compare`).|
|*Droite*|`hash_set` dont le `hash_set` construit doit être une copie.|
|*Premier*|Position du premier élément de la plage d'éléments à copier.|
|*Dernière*|Position du premier élément au-delà de la plage d'éléments à copier.|

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire du `hash_set` et peut être retourné ultérieurement en appelant [hash_set::get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.

Tous les constructeurs initialisent leurs hash_sets.

Tous les constructeurs stockent un objet de fonction de type `Traits`, qui est utilisé pour établir un ordre parmi les clés du `hash_set` et qui peut être retourné ultérieurement en appelant [hash_set::key_comp](#key_comp). Pour plus d’informations sur `Traits`, consultez la rubrique [hash_set, classe](../standard-library/hash-set-class.md).

Le premier constructeur crée un `hash_set` initial vide. Le deuxième spécifie le type de fonction de comparaison ( `Comp`) à utiliser pour établir l’ordre des éléments et le troisième spécifie explicitement le type d’allocateur ( `Al`) à utiliser. Le mot clé `explicit` supprime certains genres de conversions de type automatiques.

Les quatrième et cinquième constructeurs spécifient une copie de la `hash_set` `Right`.

Les sixième, septième et huitième constructeurs utilisent un objet initializer_list pour les éléments.

Les derniers constructeurs copient la plage [ `First`, `Last`) d’un `hash_set` avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison de la classe Traits et de l’allocateur.

Le huitième constructeur déplace le `hash_set` `Right`.

L’ordre réel des éléments dans un conteneur `hash_set` dépend de la fonction de hachage, de la fonction de tri et de la taille actuelle de la table de hachage. En général, il est impossible de la prédire comme avec le conteneur d’ensemble, où il était déterminé par la seule fonction de tri.

## <a name="insert"></a>  hash_set::insert

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Insère un élément ou une plage d'éléments dans un `hash_set`.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Val*|Valeur d’un élément à insérer dans le `hash_set`, sauf si le `hash_set` contient déjà cet élément ou, plus généralement, un élément dont la clé est ordonnée de façon équivalente.|
|*Where*|Emplacement où commencer à rechercher le point d'insertion correct. (L’insertion peut se produire dans le temps fixe amorti, plutôt que dans le temps logarithmique, si le point d’insertion suit immédiatement `_Where`.)|
|*Premier*|Position du premier élément à copier à partir d’un `hash_set`.|
|*Dernière*|Position juste au-delà du dernier élément à copier à partir d’un `hash_set`.|
|*IList*|Initializer_list depuis laquelle copier les éléments.|

### <a name="return-value"></a>Valeur de retour

La première `insert` fonction membre retourne une paire dont **bool** composant retourne **true** si une insertion a été effectuée et **false** si le `hash_set` déjà contient un élément dont la clé avait une valeur équivalente dans l’ordre, et dont le composant itérateur retourne l’adresse où un nouvel élément a été inséré ou où l’élément se trouvait déjà.

Pour accéder au composant itérateur d’une paire `pr` retournée par cette fonction membre, utilisez `pr.first` et, pour le déréférencer, utilisez `*(pr.first)`. Pour accéder à la **bool** composant d’une paire `pr` retournée par cette fonction membre, utilisez `pr.second`et pour le déréférencer, utilisez `*(pr.second)`.

La deuxième fonction membre `insert` retourne un itérateur qui pointe vers la position où le nouvel élément a été inséré dans le `hash_set`.

### <a name="remarks"></a>Notes

La troisième fonction membre insère les éléments dans un objet initializer_list.

La troisième fonction membre insère la séquence de valeurs d’éléments dans un `hash_set` qui correspond à chaque élément traité par un itérateur dans la plage [ `First`, `Last`) d’un `hash_set` spécifié.

## <a name="iterator"></a>  hash_set::iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Notes

Un type `iterator` peut être utilisé pour modifier la valeur d’un élément.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="key_comp"></a>  hash_set::key_comp

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Récupère une copie de l’objet de caractéristiques de hachage utilisé pour hacher et ordonner les valeurs des clés d’éléments dans un objet hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’objet de fonction utilisé par un hash_set pour ordonner ses éléments, qui est le paramètre de modèle *Traits*.

Pour plus d’informations sur *Traits* voir le [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

### <a name="remarks"></a>Notes

L’objet stocké définit la fonction membre :

**bool operator**( **const Key&** _ *xVal*, **const Key&** \_ `yVal`);

qui retourne **true** si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

Notez que [key_compare](#key_compare) et [value_compare](#value_compare) sont tous deux des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournis pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_set::key_compare

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l’ordre relatif de deux éléments dans le hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Notes

`key_compare` est un synonyme du paramètre de modèle *Traits*.

Pour plus d’informations sur *Traits* voir le [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

Notez que `key_compare` et [value_compare](#value_compare) sont tous deux des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournis pour les classes set et multiset, où ils sont identiques, pour la compatibilité avec les classes map et multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_compare`, consultez l’exemple relatif à [key_comp](#key_comp).

## <a name="key_type"></a>  hash_set::key_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui décrit un objet stocké comme élément d’un hash_set en sa capacité de clé de tri.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

`key_type` est un synonyme du paramètre de modèle *clé*.

Pour plus d’informations sur *clé*, consultez la section Notes de la [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

Notez que `key_type` et [value_type](#value_type) sont tous deux des synonymes du paramètre de modèle *Key*. Ces deux types sont fournis pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `key_type`, consultez l’exemple relatif à [value_type](#value_type).

## <a name="lower_bound"></a>  hash_set::lower_bound

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur au premier élément d’un hash_set avec une valeur de clé supérieure ou égale à celle de la clé spécifiée.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*clé* la clé d’argument à comparer avec la clé de tri d’un élément du hash_set recherché.

### <a name="return-value"></a>Valeur de retour

Un `iterator` ou `const_iterator` qui traite l’emplacement d’un élément dans un hash_set ayant une clé qui est égal à ou supérieur à la clé d’argument ou qui traite l’emplacement suivant le dernier élément dans le hash_set si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  hash_set::max_size

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne la longueur maximale du hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur maximale autorisée du hash_set.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_set::operator=

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Remplace les éléments du hash_set par une copie d’un autre hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*right*|[hash_set](../standard-library/hash-set-class.md) copié dans le `hash_set`.|

### <a name="remarks"></a>Notes

Après avoir supprimé les éléments existants dans un `hash_set`, `operator=` copie ou déplace le contenu de *droit* dans le `hash_set`.

### <a name="example"></a>Exemple

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="pointer"></a>  hash_set::pointer

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un pointeur vers un élément d’un hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Notes

Un type `pointer` peut être utilisé pour modifier la valeur d’un élément.

Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet hash_set.

## <a name="rbegin"></a>  hash_set::rbegin

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur traitant le premier élément d’un hash_set inversé.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé qui traite le premier élément d’un hash_set inversé ou qui traite ce qui était le dernier élément du hash_set non inversé.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec un hash_set inversé comme [begin](#begin) est utilisé avec un hash_set.

Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator`, l’objet hash_set ne peut pas être modifié. Si la valeur de retour de `rbegin` est assignée à un `reverse_iterator`, l’objet hash_set peut être modifié.

Vous pouvez utiliser `rbegin` pour itérer un hash_set vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="reference"></a>  hash_set::reference

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit une référence à un élément stocké dans un hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="rend"></a>  hash_set::rend

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’un hash_set inversé.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur de retour

Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’un hash_set inversé (emplacement qui précédait celui du premier élément du hash_set non inversé).

### <a name="remarks"></a>Notes

`rend` est utilisé avec un hash_set inversé comme [end](#end) est utilisé avec un hash_set.

Si la valeur de retour de `rend` est assignée à un `const_reverse_iterator`, l’objet hash_set ne peut pas être modifié. Si la valeur de retour de `rend` est assignée à un `reverse_iterator`, l’objet hash_set peut être modifié. La valeur retournée par `rend` ne doit pas être déréférencée.

Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de son hash_set.

### <a name="example"></a>Exemple

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="reverse_iterator"></a>  hash_set::reverse_iterator

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’un hash_set inversé.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Notes

Un type `reverse_iterator` est utilisé pour itérer le hash_set dans l’ordre inverse.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="size"></a>  hash_set::size

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne le nombre d’éléments du hash_set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur actuelle du hash_set.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="size_type"></a>  hash_set::size_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type entier non signé qui peut représenter le nombre d’éléments d’un hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).

## <a name="swap"></a>  hash_set::swap

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Paramètres

*droit* argument hash_set qui fournit les éléments à échanger avec le hash_set cible.

### <a name="remarks"></a>Notes

La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux hash_sets dont les éléments sont échangés.

### <a name="example"></a>Exemple

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="upper_bound"></a>  hash_set::upper_bound

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Retourne un itérateur au premier élément d’un hash_set avec une valeur de clé supérieure à celle de la clé spécifiée.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Paramètres

*clé* la clé d’argument à comparer avec la clé de tri d’un élément du hash_set recherché.

### <a name="return-value"></a>Valeur de retour

Un `iterator` ou `const_iterator` qui traite l’emplacement d’un élément dans un hash_set ayant une clé qui est égal à ou supérieur à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans le hash_set si aucune correspondance n’est trouvée pour la clé.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="value_comp"></a>  hash_set::value_comp

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Récupère une copie de l’objet de comparaison utilisé pour trier les valeurs d’éléments d’un hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’objet de fonction utilisé par un hash_set pour ordonner ses éléments, qui est le paramètre de modèle *comparer*.

Pour plus d’informations sur *comparer*, consultez la section Notes de la [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

### <a name="remarks"></a>Notes

L’objet stocké définit la fonction membre :

**bool operator**( **const Key&** _ *xVal*, **const Key&** \_ `yVal`);

qui retourne **true** si `_xVal` précède et n’est pas égal à `_yVal` dans l’ordre de tri.

Notez que les deux [value_compare](../standard-library/set-class.md#value_compare) et [key_compare](../standard-library/set-class.md#key_compare) sont des synonymes du paramètre de modèle *comparer*. Ces deux types sont fournis pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="value_compare"></a>  hash_set::value_compare

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui fournit deux objets de fonction, un prédicat binaire de la comparaison de classe qui peut comparer deux valeurs d’éléments d’un hash_set pour déterminer leur ordre relatif et un prédicat unaire qui hache les éléments.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Notes

`value_compare` est un synonyme du paramètre de modèle *Traits*.

Pour plus d’informations sur *Traits* voir le [hash_set, classe](../standard-library/hash-set-class.md) rubrique.

Notez que les deux [key_compare](#key_compare) et `value_compare` sont des synonymes du paramètre de modèle *Traits*. Ces deux types sont fournis pour les classes hash_set et hash_multiset, où ils sont identiques, pour la compatibilité avec les classes hash_map et hash_multimap, où ils sont distincts.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [value_comp](#value_comp) pour découvrir comment déclarer et utiliser `value_compare`.

## <a name="value_type"></a>  hash_set::value_type

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Type qui décrit un objet stocké comme élément d’un hash_set en sa capacité de valeur.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Exemple

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
