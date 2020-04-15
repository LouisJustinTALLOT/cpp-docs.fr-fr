---
title: set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::set
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
ms.openlocfilehash: 38b0a3278efd10ef5cc989a5fc900bf82d377eae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320304"
---
# <a name="set-stlclr"></a>set (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence d’éléments de longueur variable qui a un accès bidirectionnel. Vous utilisez `set` le récipient pour gérer une séquence d’éléments comme un arbre (presque) équilibré ordonné de nœuds, chacun stockant un élément.

Dans la description `GValue` ci-dessous, est le même que `GKey`, qui à son tour est le même que La *clé* à moins que ce dernier est un type d’arbitre, auquel cas il est `Key^`.

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

*Clé*<br/>
Type du composant clé d'un élément dans la séquence contrôlée.

## <a name="requirements"></a>Spécifications

**En-tête:** \<cliext/set>

**Espace nom:** cliext

## <a name="declarations"></a>Déclarations

|Définition de types|Description|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[set::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|
|[set::difference_type (STL/CLR)](#difference_type)|Le type de distance (éventuellement signée) entre deux éléments.|
|[set::generic_container (STL/CLR)](#generic_container)|Le type d’interface générique pour le conteneur.|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Le type d’itérateur pour l’interface générique pour le conteneur.|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Le type d’itérateur inversé pour l’interface générique pour le conteneur.|
|[set::generic_value (STL/CLR)](#generic_value)|Le type d’élément pour l’interface générique pour le conteneur.|
|[set::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[set::key_compare (STL/CLR)](#key_compare)|Le délégué de commande pour deux clés.|
|[set::key_type (STL/CLR)](#key_type)|Type d'une clé de tri.|
|[set::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|
|[set::size_type (STL/CLR)](#size_type)|Le type de distance (non négative) entre deux éléments.|
|[set::value_compare (STL/CLR)](#value_compare)|Le délégué de commande pour deux valeurs d’élément.|
|[set::value_type (STL/CLR)](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|
|[set::clear (STL/CLR)](#clear)|Supprime tous les éléments.|
|[set::count (STL/CLR)](#count)|Compte les éléments correspondant à une clé spécifiée.|
|[set::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[set::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|
|[set::equal_range (STL/CLR)](#equal_range)|Recherche une plage qui correspond à une clé spécifiée.|
|[set::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|
|[set::find (STL/CLR)](#find)|Recherche un élément qui correspond à une clé spécifiée.|
|[set::insert (STL/CLR)](#insert)|Ajoute des éléments.|
|[set::key_comp (STL/CLR)](#key_comp)|Copie le délégué de commande pour deux clés.|
|[set::lower_bound (STL/CLR)](#lower_bound)|Trouve le début de la plage qui correspond à une clé spécifiée.|
|[set::make_value (STL/CLR)](#make_value)|Construit un objet de valeur.|
|[set::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|
|[set::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|
|[set::set (STL/CLR)](#set)|Construit un objet conteneur.|
|[set::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[set::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|
|[set::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée à un nouveau tableau.|
|[set::upper_bound (STL/CLR)](#upper_bound)|Trouve la fin de la plage qui correspond à une clé spécifiée.|
|[set::value_comp (STL/CLR)](#value_comp)|Copie le délégué de commande pour deux valeurs d’élément.|

|Opérateur|Description|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|
|[opérateur! (ensemble) (STL/CLR)](#op_neq)|Détermine si `set` un objet n’est pas égal à un autre `set` objet.|
|[< (ensemble) (STL/CLR)](#op_lt)|Détermine si `set` un objet est `set` inférieur à un autre objet.|
|[<de l’opérateur (ensemble) (STL/CLR)](#op_lteq)|Détermine si `set` un objet est inférieur ou `set` égal à un autre objet.|
|[operator== (set) (STL/CLR)](#op_eq)|Détermine si `set` un objet est `set` égal à un autre objet.|
|[> (ensemble) (STL/CLR)](#op_gt)|Détermine si `set` un objet est `set` plus grand qu’un autre objet.|
|[>de l’opérateur (ensemble) (STL/CLR)](#op_gteq)|Détermine si `set` un objet est supérieur `set` ou égal à un autre objet.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|<xref:System.Collections.IEnumerable>|Séquence à travers les éléments.|
|<xref:System.Collections.ICollection>|Maintenir le groupe d’éléments.|
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence à travers des éléments dactylographes.|
|<xref:System.Collections.Generic.ICollection%601>|Maintenir le groupe d’éléments dactylographes.|
|Clé\<ITree,> de valeur|Maintenir le contenant générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère le stockage pour la séquence qu’il contrôle sous forme de nœuds individuels. Il insère des éléments dans un arbre (presque) équilibré qu’il garde ordonné en modifiant les liens entre les nœuds, jamais en copiant le contenu d’un nœud à l’autre. Cela signifie que vous pouvez insérer et supprimer les éléments librement sans déranger les éléments restants.

L’objet commande la séquence qu’il contrôle en appelant un objet délégué stocké de l’ensemble de [type: :key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stocké lorsque vous construisez l’ensemble; si vous ne spécifiez `operator<(key_type, key_type)`aucun objet délégué, la valeur par défaut est la comparaison . Vous accédez à cet objet stocké en appelant l’ensemble de fonction du membre [: :key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.

Un tel objet délégué doit imposer un ordre strict faible sur les touches de type [ensemble::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Cela signifie, pour `X` deux `Y`clés et :

`key_comp()(X, Y)`retourne le même résultat Boolean à chaque appel.

Si `key_comp()(X, Y)` c’est `key_comp()(Y, X)` vrai, alors doit être faux.

Si `key_comp()(X, Y)` c’est `X` vrai, alors `Y`on dit qu’il est commandé avant .

Si `!key_comp()(X, Y) && !key_comp()(Y, X)` c’est `X` `Y` vrai, alors et on dit avoir une commande équivalente.

Pour tout `X` élément `Y` qui précède dans `key_comp()(Y, X)` la séquence contrôlée, est faux. (Pour l’objet délégué par défaut, les clés ne diminuent jamais en valeur.) Contrairement à l’ensemble de `set` classe de modèle , un objet de classe de modèle ne nécessite pas que les touches pour tous les éléments soient uniques. [set](../dotnet/set-stl-clr.md) (Deux touches ou plus peuvent avoir une commande équivalente.)

Chaque élément sert à la fois d’ey et de valeur. La séquence est représentée d’une manière qui permet la recherche, l’insertion et la suppression d’un élément arbitraire avec un certain nombre d’opérations proportionnelles au logarithme du nombre d’éléments de la séquence (temps logistique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.

Un ensemble prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez marcher vers des éléments adjacents étant donné un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud de tête spécial correspond à l’itérateur retourné par [set ::fin (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Vous pouvez décroisser cet itérateur pour atteindre le dernier élément de la séquence contrôlée, si présent. Vous pouvez incrémenter un itérateur de set pour atteindre le `end()`nœud de tête, et il sera alors comparer égal à . Mais vous ne pouvez pas déreférencer l’itérateur retourné par `end()`.

Notez que vous ne pouvez pas vous référer à un élément défini directement compte tenu de sa position numérique - qui nécessite un itérateur d’accès aléatoire.

Un itérateur défini stocke une poignée à son nœud établi associé, qui à son tour stocke une poignée à son conteneur associé. Vous ne pouvez utiliser des itérateurs qu’avec leurs objets conteneurs associés. Un itérateur défini reste valide tant que son nœud défini associé est associé à un certain ensemble. En outre, un itérateur valide est reportable - vous pouvez l’utiliser pour accéder ou modifier la valeur `end()`de l’élément qu’il désigne - tant qu’il n’est pas égal à .

L’effacement ou la suppression d’un élément appelle le destructeur pour sa valeur stockée. La destruction du conteneur efface tous les éléments. Ainsi, un conteneur dont le type d’élément est une classe d’arbitres garantit qu’aucun élément ne surviv au conteneur. Notez, cependant, qu’un conteneur de poignées ne détruit *pas* ses éléments.

## <a name="members"></a>Membres

## <a name="setbegin-stlclr"></a><a name="begin"></a>set::begin (STL/CLR)

Désigne le début de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie un itérateur bidirectionnel qui désigne le premier élément de la séquence contrôlée, ou juste au-delà de la fin d’une séquence vide. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.

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

## <a name="setclear-stlclr"></a><a name="clear"></a>set::clear (STL/CLR)

Supprime tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Notes

La fonction membre appelle effectivement [l’ensemble : : effacer (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set : : commencer (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` set [::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`())`. Vous l’utilisez pour vous assurer que la séquence contrôlée est vide.

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

## <a name="setconst_iterator-stlclr"></a><a name="const_iterator"></a>set::const_iterator (STL/CLR)

Type d'un itérateur constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de `T2` type non spécifié qui peut servir d’itérateur bidirectionnel constant pour la séquence contrôlée.

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

## <a name="setconst_reference-stlclr"></a><a name="const_reference"></a>set::const_reference (STL/CLR)

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

## <a name="setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>set::const_reverse_iterator (STL/CLR)

Le type d’un itérateur inverse constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de `T4` type non spécifié qui peut servir d’itérateur inverse constant pour la séquence contrôlée.

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

## <a name="setcount-stlclr"></a><a name="count"></a>set::count (STL/CLR)

Recherche le nombre d’éléments qui correspondent à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre renvoie le nombre d’éléments dans la séquence contrôlée qui ont une commande équivalente avec *clé*. Vous l'utilisez pour déterminer le nombre d'éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

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

## <a name="setdifference_type-stlclr"></a><a name="difference_type"></a>set::difference-type (STL/CLR)

Les types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments peut-être négatif.

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

## <a name="setempty-stlclr"></a><a name="empty"></a>set::vide (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Il est équivalent à [l’ensemble::size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si l’ensemble est vide.

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

## <a name="setend-stlclr"></a><a name="end"></a>set::fin (STL/CLR)

Désigne la fin de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie un itérateur bidirectionnel qui pointe juste au-delà de la fin de la séquence contrôlée. Vous l’utilisez pour obtenir un itérateur qui désigne la fin de la séquence contrôlée; son statut ne change pas si la longueur de la séquence contrôlée change.

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

## <a name="setequal_range-stlclr"></a><a name="equal_range"></a>set::equal_range (STL/CLR)

Recherche une plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre renvoie une `cliext::pair<iterator, iterator>(` paire d’itérateurs [ensemble::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [ensemble::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Vous l’utilisez pour déterminer la plage d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

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

## <a name="seterase-stlclr"></a><a name="erase"></a>set::erase (STL/CLR)

Supprime les éléments placés aux positions spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>Paramètres

*Première*<br/>
Début de la portée à effacer.

*key*<br/>
Valeur clé à effacer.

*Dernière*<br/>
Fin de la plage à effacer.

*Où*<br/>
Élément à effacer.

### <a name="remarks"></a>Notes

La première fonction de membre supprime l’élément de la séquence contrôlée indiquée par *l’endroit où,* et renvoie un itérateur qui désigne le premier élément restant au-delà de l’élément enlevé, ou [ensemble:::fin (STL/ CLR)](../dotnet/set-end-stl-clr.md) `()` si aucun élément de ce genre n’existe. Vous l’utilisez pour supprimer un seul élément.

La deuxième fonction de membre supprime les éléments de`first` `last`la séquence contrôlée dans la plage [, ), et renvoie `end()` un itérateur qui désigne le premier élément restant au-delà de tout élément supprimé, ou si aucun élément de ce genre n’existe. Vous l’utilisez pour supprimer zéro ou plus d’éléments contigus.

La fonction du troisième membre supprime tout élément de la séquence contrôlée dont la clé a une commande équivalente à *la clé,* et renvoie un nombre du nombre d’éléments supprimés. Vous l’utilisez pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.

Chaque effacement d’élément prend du temps proportionnelle au logarithme du nombre d’éléments dans la séquence contrôlée.

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

## <a name="setfind-stlclr"></a><a name="find"></a>set::find (STL/CLR)

Recherche un élément qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

Si au moins un élément de la séquence contrôlée a une commande équivalente avec *clé,* la fonction membre renvoie un itérateur désignant l’un de ces éléments; sinon il revient [set::fin (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Vous l’utilisez pour localiser un élément actuellement dans la séquence contrôlée qui correspond à une clé spécifiée.

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

## <a name="setgeneric_container-stlclr"></a><a name="generic_container"></a>set::generic_container (STL/CLR)

Le type d’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe de conteneurs de modèle.

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

## <a name="setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>set::generic_iterator (STL/CLR)

Le type d’itérateur pour une utilisation avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un itérateur générique qui peut être utilisé avec l’interface générique pour cette classe de conteneurs de modèle.

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

## <a name="setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>set::generic_reverse_iterator (STL/CLR)

Le type d’itérateur inversé pour une utilisation avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un itérateur inverse générique qui peut être utilisé avec l’interface générique pour cette classe de conteneurs de modèle.

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

## <a name="setgeneric_value-stlclr"></a><a name="generic_value"></a>set::generic_value (STL/CLR)

Le type d’élément à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un `GValue` objet de type qui décrit la valeur de l’élément stocké pour une utilisation avec l’interface générique pour cette classe de conteneurs de modèle.

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

## <a name="setinsert-stlclr"></a><a name="insert"></a>set::insert (STL/CLR)

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

*Première*<br/>
Début de la plage à insérer.

*Dernière*<br/>
Fin de la plage à insérer.

*Oui*<br/>
Énumération à insérer.

*Val*<br/>
Valeur clé à insérer.

*Où*<br/>
Où dans le récipient à insérer (indice seulement).

### <a name="remarks"></a>Notes

Chacune des fonctions du membre insère une séquence spécifiée par les opérandes restantes.

La première fonction de membre s’efforce d’insérer `X`un élément avec la valeur *val*, et retourne une paire de valeurs . S’il `X.second` `X.first` est vrai, désigne l’élément nouvellement inséré; désigne `X.first` autrement un élément avec une commande équivalente qui existe déjà et aucun nouvel élément n’est inséré. Vous l’utilisez pour insérer un seul élément.

La deuxième fonction de membre insère un élément avec la valeur *val*, en utilisant *où* comme un indice (pour améliorer les performances), et renvoie un itérateur qui désigne l’élément nouvellement inséré. Vous l’utilisez pour insérer un seul élément qui pourrait être adjacent à un élément que vous connaissez.

La fonction du troisième membre`first` `last`insère la séquence [, ). Vous l’utilisez pour insérer zéro ou plusieurs éléments copiés à partir d’une autre séquence.

La fonction de quatrième membre insère la séquence désignée par la *droite*. Vous l’utilisez pour insérer une séquence décrite par un enumérateur.

Chaque insertion d’élément prend du temps proportionnelle au logarithme du nombre d’éléments dans la séquence contrôlée. L’insertion peut se produire dans le temps constant amorti, cependant, étant donné un indice qui désigne un élément adjacent au point d’insertion.

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

## <a name="setiterator-stlclr"></a><a name="iterator"></a>set::iterator (STL/CLR)

Type d'un itérateur pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de `T1` type non spécifié qui peut servir d’itérateur bidirectionnel pour la séquence contrôlée.

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

## <a name="setkey_comp-stlclr"></a><a name="key_comp"></a>set::key_comp (STL/CLR)

Copie le délégué de commande pour deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie le délégué de commande utilisé pour commander la séquence contrôlée. Vous l'utilisez pour comparer deux clés.

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

## <a name="setkey_compare-stlclr"></a><a name="key_compare"></a>set::key_compare (STL/CLR)

Le délégué de commande pour deux clés.

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

## <a name="setkey_type-stlclr"></a><a name="key_type"></a>set::key_type (STL/CLR)

Type d'une clé de tri.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour le paramètre de modèle *Clé*.

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

## <a name="setlower_bound-stlclr"></a><a name="lower_bound"></a>set::lower_bound (STL/CLR)

Trouve le début de la plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine `X` le premier élément de la séquence contrôlée qui a une commande équivalente à *la clé*. S’il n’existe pas de tel élément, il renvoie [le set ::fin (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; sinon il renvoie un itérateur qui désigne `X`. Vous l’utilisez pour localiser le début d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

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

## <a name="setmake_value-stlclr"></a><a name="make_value"></a>set::make_value (STL/CLR)

Construit un objet de valeur.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur clé à utiliser.

### <a name="remarks"></a>Notes

La fonction membre `value_type` renvoie un objet dont la clé est *la clé*. Vous l’utilisez pour composer un objet adapté à une utilisation avec plusieurs autres fonctions de membre.

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

## <a name="setoperator-stlclr"></a><a name="op_as"></a>ensemble ::opérateur (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Conteneur à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* l’objet, puis renvoie `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée à *droite*.

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

## <a name="setrbegin-stlclr"></a><a name="rbegin"></a>set::rbegin (STL/CLR)

Désigne le début de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie un itérateur inversé qui désigne le dernier élément de la séquence contrôlée, ou juste au-delà du début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

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

## <a name="setreference-stlclr"></a><a name="reference"></a>set::référence (STL/CLR)

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

## <a name="setrend-stlclr"></a><a name="rend"></a>set::rend (STL/CLR)

Désigne la fin de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie un itérateur inversé qui pointe juste au-delà du début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne la fin `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

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

## <a name="setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>set::reverse_iterator (STL/CLR)

Type d'un itérateur inverse pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de `T3` type non spécifié qui peut servir d’itérateur inversé pour la séquence contrôlée.

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

## <a name="setset-stlclr"></a><a name="set"></a>set::set (STL/CLR)

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

*Première*<br/>
Début de la plage à insérer.

*Dernière*<br/>
Fin de la plage à insérer.

*Pred*<br/>
Commande prédicate pour la séquence contrôlée.

*Oui*<br/>
Objet ou plage à insérer.

### <a name="remarks"></a>Notes

Le constructeur:

`set();`

initialise la séquence contrôlée sans éléments, avec la commande `key_compare()`par défaut prédicate . Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec la commande par défaut prédicate.

Le constructeur:

`explicit set(key_compare^ pred);`

initialise la séquence contrôlée sans éléments, avec l’ordre *prédicat préd*. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec la commande spécifiée prédicate.

Le constructeur:

`set(set<Key>% right);`

initialise la séquence contrôlée avec`right.begin()`la `right.end()`séquence [, ), avec la commande par défaut prédicate. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet défini *droit*, avec la commande par défaut prédicate.

Le constructeur:

`set(set<Key>^ right);`

initialise la séquence contrôlée avec`right->begin()`la `right->end()`séquence [, ), avec la commande par défaut prédicate. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet défini *droit*, avec la commande par défaut prédicate.

Le constructeur:

`template<typename InIter> set(InIter first, InIter last);`

initialise la séquence contrôlée avec`first`la `last`séquence [, ), avec la commande par défaut prédicate. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec la commande par défaut prédicate.

Le constructeur:

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

initialise la séquence contrôlée avec`first`la `last`séquence [, ), avec la commande prédicate *préd*. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec la commande spécifiée prédicate.

Le constructeur:

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

initialise la séquence contrôlée avec la séquence désignée par le *droit*d’énumérateur, avec la commande par défaut prédicate. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un enumérateur, avec la commande par défaut prédicate.

Le constructeur:

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

initialise la séquence contrôlée avec la séquence désignée par le *droit*d’énumérateur, avec le prédicat de commande *préd*. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un enumérateur, avec la commande spécifiée prédicate.

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

## <a name="setsize-stlclr"></a><a name="size"></a>ensemble::taille (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si tout ce qui vous tient à cœur est de savoir si la séquence a la taille non zéro, voir [l’ensemble::vide (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.

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

## <a name="setsize_type-stlclr"></a><a name="size_type"></a>set::size_type (STL/CLR)

Le type de distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments non négatifs.

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

## <a name="setswap-stlclr"></a><a name="swap"></a>set::swap (STL/CLR)

Échange le contenu de deux conteneurs.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Conteneur avec lequel échanger le contenu.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre `this` et à *droite*. Il le fait en temps constant et il ne fait aucune exception. Vous l’utilisez comme un moyen rapide d’échanger le contenu de deux conteneurs.

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

## <a name="setto_array-stlclr"></a><a name="to_array"></a>set::to_array (STL/CLR)

Copie la séquence contrôlée à un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

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

## <a name="setupper_bound-stlclr"></a><a name="upper_bound"></a>set::upper_bound (STL/CLR)

Trouve la fin de la plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine `X` le dernier élément de la séquence contrôlée qui a une commande équivalente à *la clé*. S’il n’existe pas `X` de tel élément, ou s’il s’agit du dernier élément de la séquence contrôlée, il renvoie [le set ::fin (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; sinon il renvoie un itérateur qui `X`désigne le premier élément au-delà . Vous l’utilisez pour localiser la fin d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

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

## <a name="setvalue_comp-stlclr"></a><a name="value_comp"></a>set::value_comp (STL/CLR)

Copie le délégué de commande pour deux valeurs d’élément.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Notes

La fonction membre renvoie le délégué de commande utilisé pour commander la séquence contrôlée. Vous l’utilisez pour comparer deux valeurs d’élément.

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

## <a name="setvalue_compare-stlclr"></a><a name="value_compare"></a>set::value_compare (STL/CLR)

Le délégué de commande pour deux valeurs d’élément.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Notes

Le type est synonyme pour le délégué qui détermine la commande de ses arguments de valeur.

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

## <a name="setvalue_type-stlclr"></a><a name="value_type"></a>set::value_type (STL/CLR)

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

## <a name="operator-set-stlclr"></a><a name="op_neq"></a>opérateur! (ensemble) (STL/CLR)

Liste pas comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction `!(left == right)`opérateur revient . Vous l’utilisez pour tester si *la gauche* n’est pas commandée de la même façon que *droite* lorsque les deux ensembles sont comparés élément par élément.

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

## <a name="operatorlt-set-stlclr"></a><a name="op_lt"></a>(ensemble)&lt; (STL/CLR)

Liste inférieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne vrai si, pour la position `i` la plus basse pour laquelle `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Sinon, il `left->size() < right->size()` retourne Vous l’utilisez pour tester si *la gauche* est commandée avant *à droite* lorsque les deux ensembles sont comparés élément par élément.

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

## <a name="operatorlt-set-stlclr"></a><a name="op_lteq"></a>(ensemble)&lt;(STL/CLR)

Liste moins ou comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction `!(right < left)`opérateur revient . Vous l’utilisez pour tester si *la gauche* n’est pas commandée après *la droite* lorsque les deux ensembles sont comparés élément par élément.

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

## <a name="operator-set-stlclr"></a><a name="op_eq"></a>(ensemble) (STL/CLR)

Liste comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne vrai seulement si *left* les séquences contrôlées par gauche `i` `left[i] ==` `right[i]`et *droite* ont la même longueur et, pour chaque position , . Vous l’utilisez pour tester si *la gauche* est commandée de la même façon que *droite* lorsque les deux ensembles sont comparés élément par élément.

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

## <a name="operatorgt-set-stlclr"></a><a name="op_gt"></a>(ensemble)&gt; (STL/CLR)

Liste supérieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction `right` `<` `left`opérateur revient . Vous l’utilisez pour tester si *la gauche* est commandée après *droite* lorsque les deux ensembles sont comparés élément par élément.

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

## <a name="operatorgt-set-stlclr"></a><a name="op_gteq"></a>(ensemble)&gt;(STL/CLR)

Liste plus grande que la comparaison plus élevée ou égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction `!(left < right)`opérateur revient . Vous l’utilisez pour tester si *la gauche* n’est pas commandée avant *à droite* lorsque les deux ensembles sont comparés élément par élément.

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
