---
title: set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
- begin member [STL/CLR]
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
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
ms.openlocfilehash: 612c0772504043a99f3a2ae9fa7da9c791076d6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500670"
---
# <a name="set-stlclr"></a>set (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence de longueur variable constituée d’éléments qui dispose d’un accès bidirectionnel. Vous utilisez le conteneur `set` pour gérer une séquence d’éléments comme une arborescence ordonnée (presque) à charge équilibrée de nœuds, chacun stocker un élément.

Dans la description ci-dessous, `GValue` est identique à `GKey`, qui à son tour est le même que *clé* , sauf si ce dernier est un type ref, auquel cas il est `Key^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    ref class set
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Paramètres

*Key*<br/>
Le type du composant clé d’un élément dans la séquence contrôlée.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<cliext/set >

**Namespace :** cliext

## <a name="declarations"></a>Déclarations

|Définition de types|Description|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[set::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|
|[set::difference_type (STL/CLR)](#difference_type)|Le type d’une distance (éventuellement signée) entre deux éléments.|
|[set::generic_container (STL/CLR)](#generic_container)|Le type de l’interface générique pour le conteneur.|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Le type d’un itérateur pour l’interface générique pour le conteneur.|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|
|[set::generic_value (STL/CLR)](#generic_value)|Le type d’un élément pour l’interface générique pour le conteneur.|
|[set::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[set::key_compare (STL/CLR)](#key_compare)|Délégué de classement pour les deux clés.|
|[set::key_type (STL/CLR)](#key_type)|Type d'une clé de tri.|
|[set::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|
|[set::size_type (STL/CLR)](#size_type)|Le type d’une distance (négative) entre deux éléments.|
|[set::value_compare (STL/CLR)](#value_compare)|Délégué de classement pour les deux valeurs d’éléments.|
|[set::value_type (STL/CLR)](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|
|[set::clear (STL/CLR)](#clear)|Supprime tous les éléments.|
|[set::count (STL/CLR)](#count)|Compte des éléments qui correspondent à une clé spécifiée.|
|[set::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[set::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|
|[set::equal_range (STL/CLR)](#equal_range)|Recherche une plage qui correspond à une clé spécifiée.|
|[set::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|
|[set::find (STL/CLR)](#find)|Recherche un élément qui correspond à une clé spécifiée.|
|[set::insert (STL/CLR)](#insert)|Ajoute des éléments.|
|[set::key_comp (STL/CLR)](#key_comp)|Copie le délégué de classement pour les deux clés.|
|[set::lower_bound (STL/CLR)](#lower_bound)|Début de la recherche de plage qui correspond à une clé spécifiée.|
|[set::make_value (STL/CLR)](#make_value)|Construit un objet de valeur.|
|[set::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|
|[set::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|
|[set::set (STL/CLR)](#set)|Construit un objet conteneur.|
|[set::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[set::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|
|[set::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée vers un nouveau tableau.|
|[set::upper_bound (STL/CLR)](#upper_bound)|Fin de la recherche de plage qui correspond à une clé spécifiée.|
|[set::value_comp (STL/CLR)](#value_comp)|Copie le délégué de classement pour les deux valeurs d’éléments.|

|Opérateur|Description|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|
|[operator!= (set) (STL/CLR)](#op_neq)|Détermine si un `set` objet n’est pas égal à un autre `set` objet.|
|[operator< (set) (STL/CLR)](#op_lt)|Détermine si un `set` objet est inférieur à un autre `set` objet.|
|[operator<= (set) (STL/CLR)](#op_lteq)|Détermine si un `set` objet est inférieur ou égal à un autre `set` objet.|
|[operator== (set) (STL/CLR)](#op_eq)|Détermine si un `set` objet est égal à un autre `set` objet.|
|[operator> (set) (STL/CLR)](#op_gt)|Détermine si un `set` objet est supérieur à un autre `set` objet.|
|[operator>= (set) (STL/CLR)](#op_gteq)|Détermine si un `set` objet est supérieur ou égal à un autre `set` objet.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|
|ITree\<de clé, valeur >|Mettre à jour de conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels. Elle insère des éléments dans une arborescence à charge équilibrée (presque) il conserve ordonnée en modifiant les liens entre les nœuds, jamais par copie le contenu d’un nœud à un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber leurs éléments restants.

L’objet trie la séquence qu’il contrôle en appelant un objet délégué stockée de type [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez l’ensemble ; Si vous ne spécifiez aucun objet de délégué, la valeur par défaut est la comparaison `operator<(key_type, key_type)`. Vous accéder à cet objet stocké en appelant la fonction membre [set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.

Cet objet de délégué doit imposer un ordre faible strict sur les clés de type [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:

`key_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.

Si `key_comp()(X, Y)` est true, puis `key_comp()(Y, X)` doit avoir la valeur false.

Si `key_comp()(X, Y)` est true, puis `X` est dit être ordonnées avant `Y`.

Si `!key_comp()(X, Y) && !key_comp()(Y, X)` est true, puis `X` et `Y` sont réputées pour avoir un classement équivalent.

Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés va jamais en diminuant valeur.) Contrairement à la classe de modèle [définir](../dotnet/set-stl-clr.md), un objet de classe de modèle `set` ne nécessite pas que les clés pour tous les éléments sont uniques. (Deux ou plusieurs clés peuvent avoir un classement équivalent.)

Chaque élément est utilisé comme une clé et une valeur. La séquence est représentée d’une façon qui autorise la recherche, d’insertion et suppression d’un élément arbitraire avec un nombre d’opérations proportionnels au logarithme du nombre d’éléments dans la séquence (temps logarithmique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.

Un ensemble prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents, étant données un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de jeu pour atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.

Notez que vous ne pouvez pas faire référence à un élément de jeu directement étant donné sa position numérique--nécessitant un itérateur à accès aléatoire.

Un itérateur défini stocke un handle vers son nœud de jeu associé, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec leurs objets conteneur associé. Un itérateur ensemble reste valide tant que son nœud de jeu associé est associé à un jeu. En outre, un itérateur valide est déréférençable : vous pouvez l’utiliser pour accéder ou de modifier la valeur de l’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.

Effacer ou de suppression d’un élément appelle le destructeur pour sa valeur stockée. Détruire le conteneur efface tous les éléments. Par conséquent, un conteneur dont le type élément est une classe ref garantit qu’aucun élément ne survivre le conteneur. Notez, toutefois, qu’un conteneur de handles ne *pas* détruire ses éléments.

## <a name="members"></a>Membres

## <a name="begin"></a>Set::Begin (STL/CLR)

Désigne le début de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur bidirectionnel qui désigne le premier élément de la séquence contrôlée, ou juste après la fin d’une séquence vide. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_set_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="clear"></a>Set::Clear (STL/CLR)

Supprime tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md) `())`. Vous l’utilisez pour vous assurer que la séquence contrôlée est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_set_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="const_iterator"></a>Set::const_iterator (STL/CLR)

Type d'un itérateur constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T2` qui peut servir d’itérateur de constante bidirectionnel pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a>Set::const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a>Set::const_reverse_iterator (STL/CLR)

Le type d’un itérateur inverse constant pour la séquence contrôlée...

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T4` qui peut servir d’itérateur inverse constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="count"></a>Set::Count (STL/CLR)

Recherche le nombre d’éléments qui correspondent à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d’éléments dans la séquence contrôlée qui ont un classement équivalent à *clé*. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="difference_type"></a>Set::difference_type (STL/CLR)

Les types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments éventuellement négatif.

### <a name="example"></a>Exemple

```cpp
// cliext_set_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="empty"></a>Set::Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Il est équivalent à [set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si le jeu est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_set_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="end"></a>Set::end (STL/CLR)

Désigne la fin de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur bidirectionnel qui pointe juste après la fin de la séquence contrôlée. Vous l’utilisez pour obtenir un itérateur qui désigne la fin de la séquence contrôlée ; son état ne change pas si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_set_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    Myset::iterator it = c1.end();
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

## <a name="equal_range"></a>Set::equal_range (STL/CLR)

Recherche une plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne une paire d’itérateurs `cliext::pair<iterator, iterator>(` [set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Vous l’utilisez pour déterminer la plage d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_iter Pairii;
int main()
    {
    Myset c1;
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

## <a name="erase"></a>Set::Erase (STL/CLR)

Supprime les éléments placés aux positions spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
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

La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé *où*et retourne un itérateur qui désigne le premier élément restant après l’élément supprimé, ou [set::end (STL/CLR) ](../dotnet/set-end-stl-clr.md) `()` si cet élément n’existe. Il permet de supprimer un élément unique.

La deuxième fonction membre supprime les éléments de la séquence contrôlée dans la plage [`first`, `last`) et retourne un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `end()` si aucun élément existe... Il permet de supprimer de zéro ou plusieurs éléments contigus.

La troisième fonction membre supprime tout élément de la séquence contrôlée, dont la clé a un classement équivalent à *clé*et retourne le nombre d’éléments supprimés. Utilisez-le pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.

Effacement de chaque élément prend du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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
    Myset::iterator it = c1.end();
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

## <a name="find"></a>Set::Find (STL/CLR)

Recherche un élément qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

Si au moins un élément dans la séquence contrôlée a un classement équivalent à *clé*, la fonction membre retourne un itérateur qui désigne un de ces éléments ; sinon, elle retourne [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Il permet de rechercher un élément actuellement dans la séquence contrôlée qui correspond à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="generic_container"></a>Set::generic_container (STL/CLR)

Le type de l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_set_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
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

## <a name="generic_iterator"></a> Set::generic_iterator (STL/CLR)

Le type d’un itérateur pour une utilisation avec l’interface générique pour le conteneur.

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
// cliext_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="generic_reverse_iterator"></a> Set::generic_reverse_iterator (STL/CLR)

Le type d’un itérateur inverse pour une utilisation avec l’interface générique pour le conteneur.

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
// cliext_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_reverse_iterator gcit = gc1->rbegin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="generic_value"></a> Set::generic_value (STL/CLR)

Le type d’un élément pour une utilisation avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stockée pour une utilisation avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_set_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="insert"></a> Set::Insert (STL/CLR)

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

*Val*<br/>
Valeur de clé à insérer.

*where*<br/>
Emplacement dans le conteneur à insérer (hint uniquement).

### <a name="remarks"></a>Notes

Chacune des fonctions membres insère une séquence spécifiée par les opérandes restants.

La première fonction membre s’efforce d’insérer un élément avec la valeur *val*et retourne une paire de valeurs `X`. Si `X.second` a la valeur true, `X.first` désigne l’élément nouvellement inséré ; sinon `X.first` désigne un élément avec les équivalents classement qui déjà existe et aucun nouvel élément est inséré. Vous l’utilisez pour insérer un élément unique.

La deuxième fonction membre insère un élément avec la valeur *val*, à l’aide *où* en tant qu’indicateur (pour améliorer les performances) et retourne un itérateur qui désigne l’élément nouvellement inséré. Vous l’utilisez pour insérer un élément unique qui peut être adjacent à un élément que vous connaissez.

La troisième fonction membre insère la séquence [`first`, `last`). Il permet d’insérer de zéro ou plusieurs des éléments copiés à partir d’une autre séquence.

La quatrième fonction membre insère la séquence désignée par le *droit*. Il permet d’insérer une séquence décrite par un énumérateur.

Chaque insertion des éléments prend du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée. Insertion peut se produire dans le temps fixe amorti, toutefois, étant donné un indicateur qui désigne un élément adjacent au point d’insertion.

### <a name="example"></a>Exemple

```cpp
// cliext_set_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_bool Pairib;
int main()
    {
    Myset c1;
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
    Myset c2;
    Myset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    Myset c3;
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

## <a name="iterator"></a> Set::iterator (STL/CLR)

Type d'un itérateur pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur bidirectionnel pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="key_comp"></a> Set::key_comp (STL/CLR)

Copie le délégué de classement pour les deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l’utilisez pour comparer deux clés.

### <a name="example"></a>Exemple

```cpp
// cliext_set_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_compare"></a> Set::key_compare (STL/CLR)

Délégué de classement pour les deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour le délégué qui détermine l’ordre de ses arguments clés.

### <a name="example"></a>Exemple

```cpp
// cliext_set_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_type"></a> Set::KEY_TYPE (STL/CLR)

Type d'une clé de tri.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *clé*.

### <a name="example"></a>Exemple

```cpp
// cliext_set_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using key_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="lower_bound"></a> Set::lower_bound (STL/CLR)

Début de la recherche de plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine le premier élément `X` dans la séquence contrôlée qui a un classement équivalent à *clé*. Si cet élément n’existe pas, elle retourne [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; sinon, elle retourne un itérateur qui désigne `X`. Il permet de localiser le début d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="make_value"></a> Set::make_value (STL/CLR)

Construit un objet de valeur.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à utiliser.

### <a name="remarks"></a>Notes

La fonction membre retourne un `value_type` objet dont la clé est *clé*. Vous l’utilisez pour composer un objet pouvant être utilisé avec plusieurs autres fonctions membres.

### <a name="example"></a>Exemple

```cpp
// cliext_set_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(Myset::make_value(L'a'));
    c1.insert(Myset::make_value(L'b'));
    c1.insert(Myset::make_value(L'c'));

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_as"></a> Set::operator = (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Conteneur à copier.

### <a name="remarks"></a>Notes

Les copies d’opérateur membre *droit* à l’objet, puis retourne `*this`. Utilisez-le pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *droit*.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="rbegin"></a> Set::rbegin (STL/CLR)

Désigne le début de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` début de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_set_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    Myset::reverse_iterator rit = c1.rbegin();
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

## <a name="reference"></a> Set::Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rend"></a> Set::rend (STL/CLR)

Désigne la fin de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l’utilisez pour obtenir un itérateur qui désigne le `current` fin de la séquence contrôlée vue dans l’ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_set_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::reverse_iterator rit = c1.rend();
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

## <a name="reverse_iterator"></a> Set::reverse_iterator (STL/CLR)

Type d'un itérateur inverse pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T3` qui peut servir d’itérateur inverse pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="set"></a> Set::Set (STL/CLR)

Construit un objet conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
set();
explicit set(key_compare^ pred);
set(set<Key>% right);
set(set<Key>^ right);
template<typename InIter>
    setset(InIter first, InIter last);
template<typename InIter>
    set(InIter first, InIter last,
        key_compare^ pred);
set(System::Collections::Generic::IEnumerable<GValue>^ right);
set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*Pred*<br/>
Classement de prédicat pour la séquence contrôlée.

*right*<br/>
Objet ou plage à insérer.

### <a name="remarks"></a>Notes

Le constructeur :

`set();`

Initialise la séquence contrôlée sans éléments, avec la valeur par défaut classement prédicat `key_compare()`. Il permet de spécifier une séquence contrôlée initiale vide, avec la valeur par défaut de classement de prédicat.

Le constructeur :

`explicit set(key_compare^ pred);`

Initialise la séquence contrôlée sans éléments, avec le prédicat de tri *pred*. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide avec le prédicat de tri spécifié.

Le constructeur :

`set(set<Key>% right);`

Initialise la séquence contrôlée par la séquence [`right.begin()`, `right.end()`), avec la valeur par défaut de classement de prédicat. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de jeu *droit*, avec la valeur par défaut de classement de prédicat.

Le constructeur :

`set(set<Key>^ right);`

Initialise la séquence contrôlée par la séquence [`right->begin()`, `right->end()`), avec la valeur par défaut de classement de prédicat. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de jeu *droit*, avec la valeur par défaut de classement de prédicat.

Le constructeur :

`template<typename InIter> set(InIter first, InIter last);`

Initialise la séquence contrôlée par la séquence [`first`, `last`), avec la valeur par défaut de classement de prédicat. Il permet de rendre la séquence contrôlée d’une copie d’une autre séquence, avec la valeur par défaut de classement de prédicat.

Le constructeur :

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

Initialise la séquence contrôlée par la séquence [`first`, `last`), avec le prédicat de tri *pred*. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri spécifié.

Le constructeur :

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

Initialise la séquence contrôlée par la séquence désignée par l’énumérateur *droit*, avec la valeur par défaut de classement de prédicat. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec la valeur par défaut de classement de prédicat.

Le constructeur :

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Initialise la séquence contrôlée par la séquence désignée par l’énumérateur *droit*, avec le prédicat de tri *pred*. Il permet d’effectuer la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec le prédicat de tri spécifié.

### <a name="example"></a>Exemple

```cpp
// cliext_set_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
// construct an empty container
    Myset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an ordering rule
    Myset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    Myset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range and an ordering rule
    Myset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    Myset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration and an ordering rule
    Myset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct from a generic container
    Myset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myset c8(%c3);
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
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="size"></a> Set::Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous intéresse est si la séquence a une taille différente de zéro, consultez [set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.

### <a name="example"></a>Exemple

```cpp
// cliext_set_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="size_type"></a> Set::size_type (STL/CLR)

Le type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments de non négatif.

### <a name="example"></a>Exemple

```cpp
// cliext_set_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::size_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> Set::swap (STL/CLR)

Échange le contenu de deux conteneurs.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Conteneur avec lequel échanger le contenu.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre `this` et *droit*. Elle le fait en temps constant et ne lève aucune exception. Vous l’utilisez comme un moyen rapide pour échanger le contenu de deux conteneurs.

### <a name="example"></a>Exemple

```cpp
// cliext_set_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    Myset c2;
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

## <a name="to_array"></a> Set::to_array (STL/CLR)

Copie la séquence contrôlée vers un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_set_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="upper_bound"></a> Set::upper_bound (STL/CLR)

Fin de la recherche de plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine le dernier élément `X` dans la séquence contrôlée qui a un classement équivalent à *clé*. Si cet élément n’existe, ou si `X` est le dernier élément dans la séquence contrôlée, elle retourne [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; sinon, elle retourne un itérateur qui désigne le premier élément au-delà de `X`. Il permet de localiser la fin d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_set_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="value_comp"></a> Set::value_comp (STL/CLR)

Copie le délégué de classement pour les deux valeurs d’éléments.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l’utilisez pour comparer deux valeurs d’éléments.

### <a name="example"></a>Exemple

```cpp
// cliext_set_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_compare"></a> Set::value_compare (STL/CLR)

Délégué de classement pour les deux valeurs d’éléments.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour le délégué qui détermine l’ordre de ses arguments de valeur.

### <a name="example"></a>Exemple

```cpp
// cliext_set_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_type"></a> Set::Value_type (STL/CLR)

Type d’un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `generic_value`.

### <a name="example"></a>Exemple

```cpp
// cliext_set_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using value_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> opérateur ! = (set) (STL/CLR)

Liste différent de comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si *gauche* n’est pas ordonné identique *droit* lorsque les deux jeux sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> opérateur&lt; (set) (STL/CLR)

Liste inférieur comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

L’opérateur fonction retourne true si, pour la position la plus basse `i` pour lequel `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Sinon, elle retourne `left->size() < right->size()` vous l’utiliser pour tester si *gauche* est classé avant *droit* lorsque les deux jeux sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> opérateur&lt;= (set) (STL/CLR)

Liste inférieure ou égale comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `!(right < left)`. Il permet de tester si *gauche* n’est pas ordonné après *droit* lorsque les deux jeux sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> opérateur == (set) (STL/CLR)

Liste de comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne true uniquement si les séquences contrôlées par *gauche* et *droit* ont la même longueur et, pour chaque position `i`, `left[i] ==` `right[i]`. Il permet de tester si *gauche* est ordonné identique *droit* lorsque les deux jeux sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> opérateur&gt; (set) (STL/CLR)

Comparaison de supériorité de la liste.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `right` `<` `left`. Il permet de tester si *gauche* est trié après *droit* lorsque les deux jeux sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> opérateur&gt;= (set) (STL/CLR)

Liste supérieur ou égal à comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction d’opérateur retourne `!(left < right)`. Il permet de tester si *gauche* n’est pas classé avant *droit* lorsque les deux jeux sont comparé élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_set_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```