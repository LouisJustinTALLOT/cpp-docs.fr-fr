---
title: hash_set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_set
- cliext::hash_set::begin
- cliext::hash_set::bucket_count
- cliext::hash_set::clear
- cliext::hash_set::const_iterator
- cliext::hash_set::const_reference
- cliext::hash_set::const_reverse_iterator
- cliext::hash_set::count
- cliext::hash_set::difference_type
- cliext::hash_set::empty
- cliext::hash_set::end
- cliext::hash_set::equal_range
- cliext::hash_set::erase
- cliext::hash_set::find
- cliext::hash_set::generic_container
- cliext::hash_set::generic_iterator
- cliext::hash_set::generic_reverse_iterator
- cliext::hash_set::generic_value
- cliext::hash_set::hash_delegate
- cliext::hash_set::hash_set
- cliext::hash_set::hasher
- cliext::hash_set::insert
- cliext::hash_set::iterator
- cliext::hash_set::key_comp
- cliext::hash_set::key_compare
- cliext::hash_set::key_type
- cliext::hash_set::load_factor
- cliext::hash_set::lower_bound
- cliext::hash_set::make_value
- cliext::hash_set::max_load_factor
- cliext::hash_set::operator=
- cliext::hash_set::rbegin
- cliext::hash_set::reference
- cliext::hash_set::rehash
- cliext::hash_set::rend
- cliext::hash_set::reverse_iterator
- cliext::hash_set::size
- cliext::hash_set::size_type
- cliext::hash_set::swap
- cliext::hash_set::to_array
- cliext::hash_set::upper_bound
- cliext::hash_set::value_comp
- cliext::hash_set::value_compare
- cliext::hash_set::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_set class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- hash_delegate member [STL/CLR]
- hash_set member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: d110e356-ba3e-4e52-9e2d-d997bf975c96
ms.openlocfilehash: 92434a6617e041e4c0ab11499b8eb3535093caad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208570"
---
# <a name="hash_set-stlclr"></a>hash_set (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments disposant d’un accès bidirectionnel. Vous utilisez le conteneur `hash_set` pour gérer une séquence d’éléments comme une table de hachage, chaque entrée de table stockant une liste de nœuds liée bidirectionnelle, et chaque nœud qui stocke un élément. La valeur de chaque élément est utilisée comme clé pour le classement de la séquence.

Dans la description ci-dessous, `GValue` est identique à `GKey`, qui est, à son tour, identique à la *clé* , sauf si ce dernier est un type REF, auquel cas il est `Key^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    ref class hash_set
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Paramètres

*Clé*<br/>
Type du composant clé d'un élément dans la séquence contrôlée.

## <a name="requirements"></a>Spécifications

**En-tête :** \<cliext/hash_set >

**Espace de noms :** cliext

## <a name="declarations"></a>Déclarations

|Définition de types|Description|
|---------------------|-----------------|
|[hash_set::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[hash_set::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[hash_set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|
|[hash_set::difference_type (STL/CLR)](#difference_type)|Type d’une distance (éventuellement signée) entre deux éléments.|
|[hash_set::generic_container (STL/CLR)](#generic_container)|Type de l’interface générique pour le conteneur.|
|[hash_set::generic_iterator (STL/CLR)](#generic_iterator)|Type d’un itérateur pour l’interface générique pour le conteneur.|
|[hash_set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Type d’un itérateur inverse pour l’interface générique pour le conteneur.|
|[hash_set::generic_value (STL/CLR)](#generic_value)|Type d’un élément pour l’interface générique pour le conteneur.|
|[hash_set::hasher (STL/CLR)](#hasher)|Délégué de hachage pour une clé.|
|[hash_set::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[hash_set::key_compare (STL/CLR)](#key_compare)|Délégué de classement de deux clés.|
|[hash_set::key_type (STL/CLR)](#key_type)|Type d'une clé de tri.|
|[hash_set::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[hash_set::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|
|[hash_set::size_type (STL/CLR)](#size_type)|Type d’une distance (non négative) entre deux éléments.|
|[hash_set::value_compare (STL/CLR)](#value_compare)|Délégué de classement pour deux valeurs d’élément.|
|[hash_set::value_type (STL/CLR)](#value_type)|Type d'un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[hash_set::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|
|[hash_set::bucket_count (STL/CLR)](#bucket_count)|Compte le nombre de compartiments.|
|[hash_set::clear (STL/CLR)](#clear)|Supprime tous les éléments.|
|[hash_set::count (STL/CLR)](#count)|Compte les éléments qui correspondent à une clé spécifiée.|
|[hash_set::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[hash_set::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|
|[hash_set::equal_range (STL/CLR)](#equal_range)|Recherche une plage qui correspond à une clé spécifiée.|
|[hash_set::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|
|[hash_set::find (STL/CLR)](#find)|Recherche un élément qui correspond à une clé spécifiée.|
|[hash_set::hash_delegate (STL/CLR)](#hash_delegate)|Copie le délégué de hachage pour une clé.|
|[hash_set::hash_set (STL/CLR)](#hash_set)|Construit un objet conteneur.|
|[hash_set::insert (STL/CLR)](#insert)|Ajoute des éléments.|
|[hash_set::key_comp (STL/CLR)](#key_comp)|Copie le délégué de classement pour deux clés.|
|[hash_set::load_factor (STL/CLR)](#load_factor)|Compte le nombre moyen d'éléments par compartiment.|
|[hash_set::lower_bound (STL/CLR)](#lower_bound)|Recherche le début de la plage qui correspond à une clé spécifiée.|
|[hash_set::make_value (STL/CLR)](#make_value)|Construit un objet de valeur.|
|[hash_set::max_load_factor (STL/CLR)](#max_load_factor)|Obtient ou définit le nombre maximal d’éléments par compartiment.|
|[hash_set::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|
|[hash_set::rehash (STL/CLR)](#rehash)|Régénère la table de hachage.|
|[hash_set::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|
|[hash_set::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[hash_set::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|
|[hash_set::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée dans un nouveau tableau.|
|[hash_set::upper_bound (STL/CLR)](#upper_bound)|Recherche la fin de la plage qui correspond à une clé spécifiée.|
|[hash_set::value_comp (STL/CLR)](#value_comp)|Copie le délégué de classement pour deux valeurs d’élément.|

|Opérateur|Description|
|--------------|-----------------|
|[hash_set::operator= (STL/CLR)](#op)|Remplace la séquence contrôlée.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|<xref:System.Collections.IEnumerable>|Séquencez les éléments.|
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|
|<xref:System.Collections.Generic.IEnumerable%601>|Séquencez les éléments typés.|
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|
|IHash\<clé, valeur >|Conserver le conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels dans une liste liée bidirectionnelle. Pour accélérer l’accès, l’objet gère également un tableau de longueurs variables de pointeurs dans la liste (table de hachage), en gérant efficacement la liste entière sous la forme d’une séquence de sous-listes ou de compartiments. Elle insère des éléments dans un compartiment qu’elle continue de trier en modifiant les liens entre les nœuds, jamais en copiant le contenu d’un nœud vers un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber les éléments restants.

L’objet trie chaque compartiment qu’il contrôle en appelant un objet délégué stocké de type [hash_set :: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stocké quand vous construisez le hash_set ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<=(key_type, key_type)`.

Vous accédez à l’objet délégué stocké en appelant la fonction membre [hash_set :: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Un objet délégué de ce type doit définir un ordre équivalent entre les clés de type [hash_set :: KEY_TYPE (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Autrement dit, pour deux clés `X` et `Y`:

`key_comp()(X, Y)` retourne le même résultat booléen pour chaque appel.

Si `key_comp()(X, Y) && key_comp()(Y, X)` a la valeur true, `X` et `Y` sont considérés comme ayant un ordre équivalent.

Toute règle de classement qui se comporte comme `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` ou `operator==(key_type, key_type)` définit le classement eqivalent.

Notez que le conteneur garantit uniquement que les éléments dont les clés ont un classement équivalent (et le hachage à la même valeur entière) sont adjacents dans un compartiment. Contrairement à la classe de modèle [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md), un objet de la classe de modèle `hash_set` garantit que les clés pour tous les éléments sont uniques. (Deux clés n’ont pas le même classement.)

L’objet détermine le compartiment qui doit contenir une clé de tri donnée en appelant un objet délégué stocké de type [hash_set :: Hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Vous accédez à cet objet stocké en appelant la fonction membre [hash_set :: hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` pour obtenir une valeur entière qui dépend de la valeur de clé. Vous pouvez spécifier l’objet délégué stocké quand vous construisez le hash_set ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la `System::Object::hash_value(key_type)`de la fonction. Cela signifie, pour toutes les clés `X` et `Y`:

`hash_delegate()(X)` retourne le même résultat entier lors de chaque appel.

Si `X` et `Y` ont un classement équivalent, `hash_delegate()(X)` doit retourner le même résultat entier que `hash_delegate()(Y)`.

Chaque élément sert à la fois de clé et de valeur. La séquence est représentée de façon à permettre la recherche, l’insertion et la suppression d’un élément arbitraire avec un certain nombre d’opérations indépendantes du nombre d’éléments dans la séquence (temps constant)--au moins dans le meilleur des cas. De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.

Toutefois, si les valeurs hachées ne sont pas distribuées uniformément, une table de hachage peut être dégénérée. Dans l’extrême, pour une fonction de hachage qui retourne toujours la même valeur, la recherche, l’insertion et la suppression sont proportionnelles au nombre d’éléments dans la séquence (temps linéaire). Le conteneur s’efforce de choisir une fonction de hachage raisonnable, une taille de compartiment moyenne et une taille de table de hachage (nombre total de compartiments), mais vous pouvez remplacer tout ou partie de ces choix. Consultez, par exemple, les fonctions [hash_set :: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) et [hash_set :: rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).

Un hash_set prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez effectuer un pas à pas vers des éléments adjacents en fonction d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [hash_set :: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur pour atteindre le dernier élément de la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de hash_set pour atteindre le nœud principal, et il sera alors comparé à `end()`. Toutefois, vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.

Notez que vous ne pouvez pas faire référence à un élément hash_set directement en fonction de sa position numérique, qui requiert un itérateur à accès aléatoire.

Un itérateur de hash_set stocke un handle vers son nœud de hash_set associé, qui à son tour stocke un handle vers son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec leurs objets conteneur associés. Un itérateur de hash_set reste valide tant que son nœud de hash_set associé est associé à des hash_set. En outre, un itérateur valide est déréférençable. vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne, tant qu’il n’est pas égal à `end()`.

L’effacement ou la suppression d’un élément appelle le destructeur pour sa valeur stockée. La destruction du conteneur efface tous les éléments. Ainsi, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne se trouve dans le conteneur. Notez, toutefois, qu’un conteneur de handles ne détruit *pas* ses éléments.

## <a name="members"></a>Membres

## <a name="hash_setbegin-stlclr"></a><a name="begin"></a>hash_set :: Begin (STL/CLR)

Désigne le début de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur bidirectionnel qui désigne le premier élément de la séquence contrôlée, ou juste après la fin d’une séquence vide. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_set::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

## <a name="hash_setbucket_count-stlclr"></a><a name="bucket_count"></a>hash_set :: bucket_count (STL/CLR)

Compte le nombre de compartiments.

### <a name="syntax"></a>Syntaxe

```cpp
int bucket_count();
```

### <a name="remarks"></a>Notes

Les fonctions membres retournent le nombre actuel de compartiments. Vous l’utilisez pour déterminer la taille de la table de hachage.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_setclear-stlclr"></a><a name="clear"></a>hash_set :: Clear (STL/CLR)

Supprime tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Notes

La fonction membre appelle efficacement [hash_set :: Erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md)`(` [hash_set :: Begin (STL/clr)](../dotnet/hash-set-begin-stl-clr.md)`(),` [HASH_SET :: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`())`. Vous pouvez l’utiliser pour vous assurer que la séquence contrôlée est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="hash_setconst_iterator-stlclr"></a><a name="const_iterator"></a>hash_set :: const_iterator (STL/CLR)

Type d'un itérateur constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T2` qui peut servir d’itérateur bidirectionnel constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_set::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setconst_reference-stlclr"></a><a name="const_reference"></a>hash_set :: const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_set::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_set::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>hash_set :: const_reverse_iterator (STL/CLR)

Type d’un itérateur inverse constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T4` qui peut servir d’itérateur inverse constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_set::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_setcount-stlclr"></a><a name="count"></a>hash_set :: Count (STL/CLR)

Recherche le nombre d’éléments qui correspondent à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d’éléments dans la séquence contrôlée qui ont un classement équivalent avec la *clé*. Vous l'utilisez pour déterminer le nombre d'éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="hash_setdifference_type-stlclr"></a><a name="difference_type"></a>hash_set ::d ifference_type (STL/CLR)

Types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments éventuellement négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_set::difference_type diff = 0;
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_set::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="hash_setempty-stlclr"></a><a name="empty"></a>hash_set :: Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle équivaut à [hash_set :: Size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si le hash_set est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="hash_setend-stlclr"></a><a name="end"></a>hash_set :: end (STL/CLR)

Désigne la fin de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur bidirectionnel qui pointe juste après la fin de la séquence contrôlée. Vous l’utilisez pour obtenir un itérateur qui désigne la fin de la séquence contrôlée ; son état ne change pas si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_set::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="hash_setequal_range-stlclr"></a><a name="equal_range"></a>hash_set :: equal_range (STL/CLR)

Recherche une plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne une paire d’itérateurs `cliext::pair<iterator, iterator>(` [hash_set :: lower_bound (STL/CLR)](../dotnet/hash-set-lower-bound-stl-clr.md)`(key),` [hash_set :: upper_bound (STL/CLR)](../dotnet/hash-set-upper-bound-stl-clr.md)`(key))`. Vous l’utilisez pour déterminer la plage d’éléments actuellement dans la séquence contrôlée qui correspond à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
typedef Myhash_set::pair_iter_iter Pairii;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="hash_seterase-stlclr"></a><a name="erase"></a>hash_set :: Erase (STL/CLR)

Supprime les éléments placés aux positions spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la plage à effacer.

*key*<br/>
Valeur de clé à effacer.

*last*<br/>
Fin de la plage à effacer.

*where*<br/>
Élément à effacer.

### <a name="remarks"></a>Notes

La première fonction membre supprime l’élément de la séquence contrôlée vers *laquelle*pointe, et retourne un itérateur qui désigne le premier élément restant après l’élément supprimé, ou [hash_set :: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()` si aucun élément de ce type n’existe. Vous l’utilisez pour supprimer un seul élément.

La deuxième fonction membre supprime les éléments de la séquence contrôlée dans la plage [`first`, `last`) et retourne un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `end()` si aucun élément de ce type n’existe. Vous l’utilisez pour supprimer zéro, un ou plusieurs éléments contigus.

La troisième fonction membre supprime tout élément de la séquence contrôlée dont la clé a un classement équivalent à la *clé*, et retourne le nombre d’éléments supprimés. Vous l’utilisez pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.

Chaque effacement d’élément prend du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Myhash_set::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="hash_setfind-stlclr"></a><a name="find"></a>hash_set :: Find (STL/CLR)

Recherche un élément qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

Si au moins un élément de la séquence contrôlée a un classement équivalent avec la *clé*, la fonction membre retourne un itérateur désignant l’un de ces éléments ; Sinon, elle retourne [hash_set :: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`. Vous l’utilisez pour rechercher un élément actuellement dans la séquence contrôlée qui correspond à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="hash_setgeneric_container-stlclr"></a><a name="generic_container"></a>hash_set :: generic_container (STL/CLR)

Type de l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="hash_setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>hash_set :: generic_iterator (STL/CLR)

Type d’un itérateur à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un itérateur générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_set::generic_iterator gcit = gc1->begin();
    Myhash_set::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>hash_set :: generic_reverse_iterator (STL/CLR)

Type d’un itérateur inverse à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un itérateur inverse générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_set::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_set::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="hash_setgeneric_value-stlclr"></a><a name="generic_value"></a>hash_set :: generic_value (STL/CLR)

Type d’un élément à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké à utiliser avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_set::generic_iterator gcit = gc1->begin();
    Myhash_set::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_sethash_delegate-stlclr"></a><a name="hash_delegate"></a>hash_set :: hash_delegate (STL/CLR)

Recherche un élément qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué utilisé pour convertir une valeur de clé en entier. Vous l’utilisez pour hacher une clé.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_sethash_set-stlclr"></a><a name="hash_set"></a>hash_set :: hash_set (STL/CLR)

Construit un objet conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
hash_set();
explicit hash_set(key_compare^ pred);
hash_set(key_compare^ pred, hasher^ hashfn);
hash_set(hash_set<Key>% right);
hash_set(hash_set<Key>^ right);
template<typename InIter>
    hash_sethash_set(InIter first, InIter last);
template<typename InIter>
    hash_set(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_set(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la plage à insérer.

*hashfn*<br/>
Fonction de hachage pour le mappage des clés aux compartiments.

*last*<br/>
Fin de la plage à insérer.

*prédit*<br/>
Prédicat de classement pour la séquence contrôlée.

*right*<br/>
Objet ou plage à insérer.

### <a name="remarks"></a>Notes

Le constructeur :

`hash_set();`

Initialise la séquence contrôlée sans éléments, avec le prédicat de classement par défaut `key_compare()`et avec la fonction de hachage par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de tri par défaut et la fonction de hachage.

Le constructeur :

`explicit hash_set(key_compare^ pred);`

Initialise la séquence contrôlée sans éléments, avec le prédicat de classement *prédit*et avec la fonction de hachage par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de tri spécifié et la fonction de hachage par défaut.

Le constructeur :

`hash_set(key_compare^ pred, hasher^ hashfn);`

Initialise la séquence contrôlée sans éléments, avec le prédicat de classement *prédit*et avec la fonction de hachage *hashfn*. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de classement et la fonction de hachage spécifiés.

Le constructeur :

`hash_set(hash_set<Key>% right);`

Initialise la séquence contrôlée avec la séquence [`right.begin()`, `right.end()`), avec le prédicat de tri par défaut et avec la fonction de hachage par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par le hash_set objet à *droite*, avec le prédicat de tri par défaut et la fonction de hachage.

Le constructeur :

`hash_set(hash_set<Key>^ right);`

Initialise la séquence contrôlée avec la séquence [`right->begin()`, `right->end()`), avec le prédicat de tri par défaut et avec la fonction de hachage par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par le hash_set objet à *droite*, avec le prédicat de tri par défaut et la fonction de hachage.

Le constructeur :

`template<typename InIter> hash_set(InIter first, InIter last);`

Initialise la séquence contrôlée avec la séquence [`first`, `last`), avec le prédicat de tri par défaut et avec la fonction de hachage par défaut. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri par défaut et la fonction de hachage.

Le constructeur :

`template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`

Initialise la séquence contrôlée avec la séquence [`first`, `last`), avec le prédicat de classement *prédit*et avec la fonction de hachage par défaut. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri spécifié et la fonction de hachage par défaut.

Le constructeur :

`template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

Initialise la séquence contrôlée avec la séquence [`first`, `last`), avec le prédicat de classement *prédit*et avec la fonction de hachage *hashfn*. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri et la fonction de hachage spécifiés.

Le constructeur :

`hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`

Initialise la séquence contrôlée avec la séquence désignée par le *droit*de l’énumérateur, avec le prédicat de tri par défaut et avec la fonction de hachage par défaut. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec le prédicat de tri par défaut et la fonction de hachage.

Le constructeur :

`hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Initialise la séquence contrôlée avec la séquence désignée par le *droit*d’énumérateur, avec le prédicat de classement *prédit*et avec la fonction de hachage par défaut. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec le prédicat de tri spécifié et la fonction de hachage par défaut.

Le constructeur :

`hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

Initialise la séquence contrôlée avec la séquence désignée par le *droit*d’énumérateur, avec le prédicat de classement *prédit*, et avec la fonction de hachage *hashfn*. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec le prédicat de tri et la fonction de hachage spécifiés.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
// construct an empty container
    Myhash_set c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_set c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_set::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_set c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_set c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_set c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_set::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_set c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_set c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_set c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_set::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_set c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_set c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hash_sethasher-stlclr"></a><a name="hasher"></a>hash_set :: hacheur (STL/CLR)

Délégué de hachage pour une clé.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>Notes

Le type décrit un délégué qui convertit une valeur de clé en entier.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_setinsert-stlclr"></a><a name="insert"></a>hash_set :: Insert (STL/CLR)

Ajoute des éléments.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, bool> insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*right*<br/>
Énumération à insérer.

*val*<br/>
Valeur de clé à insérer.

*where*<br/>
Où dans le conteneur à insérer (hint uniquement).

### <a name="remarks"></a>Notes

Chacune des fonctions membres insère une séquence spécifiée par les opérandes restants.

La première fonction membre s’efforce d’insérer un élément avec la valeur *Val*et retourne une paire de valeurs `X`. Si `X.second` a la valeur true, `X.first` désigne l’élément nouvellement inséré ; sinon `X.first` désigne un élément avec un classement équivalent qui existe déjà et aucun nouvel élément n’est inséré. Vous l’utilisez pour insérer un élément unique.

La deuxième fonction membre insère un élément avec la valeur *Val*, en utilisant *Where* comme indicateur (pour améliorer les performances) et retourne un itérateur qui désigne l’élément nouvellement inséré. Vous l’utilisez pour insérer un élément unique qui peut être adjacent à un élément que vous connaissez.

La troisième fonction membre insère la séquence [`first`, `last`). Vous l’utilisez pour insérer zéro, un ou plusieurs éléments copiés à partir d’une autre séquence.

La quatrième fonction membre insère la séquence désignée par la *droite*. Vous l’utilisez pour insérer une séquence décrite par un énumérateur.

Chaque insertion d’élément prend un temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée. L’insertion peut se produire dans le temps constant amorti, en fonction d’une indication qui désigne un élément adjacent au point d’insertion.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
typedef Myhash_set::pair_iter_bool Pairib;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    Pairib pair1 = c1.insert(L'x');
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",
        *pair1.first, pair1.second);

    pair1 = c1.insert(L'b');
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",
        *pair1.first, pair1.second);

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Myhash_set c2;
    Myhash_set::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_set c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = [x True]
insert(L'b') = [b False]
a b c x
insert(begin(), L'y') = y
a b c x y
a b c x
a b c x y
```

## <a name="hash_setiterator-stlclr"></a><a name="iterator"></a>hash_set :: iterator (STL/CLR)

Type d'un itérateur pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur bidirectionnel pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_set::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setkey_comp-stlclr"></a><a name="key_comp"></a>hash_set :: key_comp (STL/CLR)

Copie le délégué de classement pour deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l'utilisez pour comparer deux clés.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_set c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_setkey_comp-stlclr"></a><a name="key_comp"></a>hash_set :: key_comp (STL/CLR)

Copie le délégué de classement pour deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l'utilisez pour comparer deux clés.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_set c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_setkey_compare-stlclr"></a><a name="key_compare"></a>hash_set :: key_compare (STL/CLR)

Délégué de classement de deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du délégué qui détermine l’ordre de ses arguments de clé.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_set c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_setkey_type-stlclr"></a><a name="key_type"></a>hash_set :: key_type (STL/CLR)

Type d'une clé de tri.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la *clé*de paramètre de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_set::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setload_factor-stlclr"></a><a name="load_factor"></a>hash_set :: load_factor (STL/CLR)

Compte le nombre moyen d'éléments par compartiment.

### <a name="syntax"></a>Syntaxe

```cpp
float load_factor();
```

### <a name="remarks"></a>Notes

La fonction membre retourne `(float)`[hash_set :: Size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md)`() /` [hash_set :: bucket_count (STL/CLR)](../dotnet/hash-set-bucket-count-stl-clr.md)`()`. Vous l’utilisez pour déterminer la taille moyenne des compartiments.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_setlower_bound-stlclr"></a><a name="lower_bound"></a>hash_set :: lower_bound (STL/CLR)

Recherche le début de la plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine le premier élément `X` dans la séquence contrôlée qui hache vers le même compartiment que la *clé* et qui a un classement équivalent à la *clé*. Si aucun élément de ce type n’existe, il retourne [hash_set :: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`; Sinon, elle retourne un itérateur qui désigne `X`. Vous l’utilisez pour localiser le début d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="hash_setmake_value-stlclr"></a><a name="make_value"></a>hash_set :: make_value (STL/CLR)

Construit un objet de valeur.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à utiliser.

### <a name="remarks"></a>Notes

La fonction membre retourne un objet `value_type` dont la clé est *clé*. Vous l’utilisez pour composer un objet pouvant être utilisé avec plusieurs autres fonctions membres.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(Myhash_set::make_value(L'a'));
    c1.insert(Myhash_set::make_value(L'b'));
    c1.insert(Myhash_set::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_set::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setmax_load_factor-stlclr"></a><a name="max_load_factor"></a>hash_set :: max_load_factor (STL/CLR)

Obtient ou définit le nombre maximal d’éléments par compartiment.

### <a name="syntax"></a>Syntaxe

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>Paramètres

*new_factor*<br/>
Nouveau facteur de charge maximal à stocker.

### <a name="remarks"></a>Notes

La première fonction membre retourne le facteur de charge maximale stockée actuel. Vous l’utilisez pour déterminer la taille de compartiment moyenne maximale.

La deuxième fonction membre remplace le facteur de charge maximale du magasin par *new_factor*. Aucun rehachage automatique ne se produit jusqu’à l’insertion suivante.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

## <a name="hash_setoperator-stlclr"></a><a name="op"></a>hash_set :: Operator = (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
hash_set<Key>% operator=(hash_set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Conteneur à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* vers l’objet, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *Right*.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_set::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_set c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_set::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="hash_setrbegin-stlclr"></a><a name="rbegin"></a>hash_set :: rbegin (STL/CLR)

Désigne le début de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_set::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="hash_setreference-stlclr"></a><a name="reference"></a>hash_set :: Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_set::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_set::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setrehash-stlclr"></a><a name="rehash"></a>hash_set :: rehash (STL/CLR)

Régénère la table de hachage.

### <a name="syntax"></a>Syntaxe

```cpp
void rehash();
```

### <a name="remarks"></a>Notes

La fonction membre reconstruit la table de hachage, en veillant à ce que [hash_set :: load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md)`() <=` [hash_set :: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md). Sinon, la taille de la table de hachage augmente uniquement si nécessaire après une insertion. (La taille n’est jamais réduite automatiquement.) Vous l’utilisez pour ajuster la taille de la table de hachage.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_setrend-stlclr"></a><a name="rend"></a>hash_set :: rend (STL/CLR)

Désigne la fin de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne la fin `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_set::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="hash_setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>hash_set :: reverse_iterator (STL/CLR)

Type d'un itérateur inverse pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T3` qui peut servir d’itérateur inverse pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_set::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_setsize-stlclr"></a><a name="size"></a>hash_set :: Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous vous intéressez uniquement si la séquence a une taille différente de zéro, consultez [hash_set :: Empty (STL/CLR)](../dotnet/hash-set-empty-stl-clr.md)`()`.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="hash_setsize_type-stlclr"></a><a name="size_type"></a>hash_set :: size_type (STL/CLR)

Type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments non négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_set::size_type diff = 0;
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="hash_setswap-stlclr"></a><a name="swap"></a>hash_set :: swap (STL/CLR)

Échange le contenu de deux conteneurs.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(hash_set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Conteneur avec lequel échanger le contenu.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre `this` et *Right*. Elle le fait en temps constant et ne lève aucune exception. Vous l’utilisez comme un moyen rapide d’échanger le contenu de deux conteneurs.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_set c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
d e f
d e f
a b c
```

## <a name="hash_setto_array-stlclr"></a><a name="to_array"></a>hash_set :: to_array (STL/CLR)

Copie la séquence contrôlée dans un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="hash_setupper_bound-stlclr"></a><a name="upper_bound"></a>hash_set :: upper_bound (STL/CLR)

Recherche la fin de la plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine le dernier élément `X` dans la séquence contrôlée qui hache vers le même compartiment que la *clé* et qui a un classement équivalent à la *clé*. Si aucun élément de ce type n’existe, ou si `X` est le dernier élément de la séquence contrôlée, elle retourne [hash_set :: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`; Sinon, elle retourne un itérateur qui désigne le premier élément au-delà de `X`. Vous l’utilisez pour localiser la fin d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="hash_setvalue_comp-stlclr"></a><a name="value_comp"></a>hash_set :: value_comp (STL/CLR)

Copie le délégué de classement pour deux valeurs d’élément.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l’utilisez pour comparer deux valeurs d’éléments.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_setvalue_compare-stlclr"></a><a name="value_compare"></a>hash_set :: value_compare (STL/CLR)

Délégué de classement pour deux valeurs d’élément.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du délégué qui détermine l’ordre de ses arguments de valeur.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_setvalue_type-stlclr"></a><a name="value_type"></a>hash_set :: value_type (STL/CLR)

Type d'un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `generic_value`.

### <a name="example"></a>Exemple

```cpp
// cliext_hash_set_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_set::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```
