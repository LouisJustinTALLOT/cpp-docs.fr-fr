---
title: multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multiset
- cliext::multiset::begin
- cliext::multiset::clear
- cliext::multiset::const_iterator
- cliext::multiset::const_reference
- cliext::multiset::const_reverse_iterator
- cliext::multiset::count
- cliext::multiset::difference_type
- cliext::multiset::empty
- cliext::multiset::end
- cliext::multiset::equal_range
- cliext::multiset::erase
- cliext::multiset::find
- cliext::multiset::generic_container
- cliext::multiset::generic_iterator
- cliext::multiset::generic_reverse_iterator
- cliext::multiset::generic_value
- cliext::multiset::insert
- cliext::multiset::iterator
- cliext::multiset::key_comp
- cliext::multiset::key_compare
- cliext::multiset::key_type
- cliext::multiset::lower_bound
- cliext::multiset::make_value
- cliext::multiset::multiset
- cliext::multiset::operator=
- cliext::multiset::rbegin
- cliext::multiset::reference
- cliext::multiset::rend
- cliext::multiset::reverse_iterator
- cliext::multiset::size
- cliext::multiset::size_type
- cliext::multiset::swap
- cliext::multiset::to_array
- cliext::multiset::upper_bound
- cliext::multiset::value_comp
- cliext::multiset::value_compare
- cliext::multiset::value_type
- cliext::multiset::operator!=
- cliext::multiset::operator<
- cliext::multiset::operator<=
- cliext::multiset::operator==
- cliext::multiset::operator>
- cliext::multiset::operator>=
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
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
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
ms.openlocfilehash: 811b96cca1fbf661def181d16dcb6a02c6c398d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208492"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments disposant d’un accès bidirectionnel. Vous utilisez le conteneur `multiset` pour gérer une séquence d’éléments sous la forme d’une arborescence ordonnée équilibrée (presque), chacune stockant un élément.

Dans la description ci-dessous, `GValue` est identique à `GKey`, qui est, à son tour, identique à la *clé* , sauf si ce dernier est un type REF, auquel cas il est `Key^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    ref class multiset
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

**En-tête :** \<cliext/set >

**Espace de noms :** cliext

## <a name="declarations"></a>Déclarations

|Définition de types|Description|
|---------------------|-----------------|
|[multiset::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[multiset::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|
|[multiset::difference_type (STL/CLR)](#difference_type)|Type d’une distance (éventuellement signée) entre deux éléments.|
|[multiset::generic_container (STL/CLR)](#generic_container)|Type de l’interface générique pour le conteneur.|
|[multiset::generic_iterator (STL/CLR)](#generic_iterator)|Type d’un itérateur pour l’interface générique pour le conteneur.|
|[multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Type d’un itérateur inverse pour l’interface générique pour le conteneur.|
|[multiset::generic_value (STL/CLR)](#generic_value)|Type d’un élément pour l’interface générique pour le conteneur.|
|[multiset::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[multiset::key_compare (STL/CLR)](#key_compare)|Délégué de classement de deux clés.|
|[multiset::key_type (STL/CLR)](#key_type)|Type d'une clé de tri.|
|[multiset::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|
|[multiset::size_type (STL/CLR)](#size_type)|Type d’une distance (non négative) entre deux éléments.|
|[multiset::value_compare (STL/CLR)](#value_compare)|Délégué de classement pour deux valeurs d’élément.|
|[multiset::value_type (STL/CLR)](#value_type)|Type d'un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[multiset::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|
|[multiset::clear (STL/CLR)](#clear)|Supprime tous les éléments.|
|[multiset::count (STL/CLR)](#count)|Compte les éléments qui correspondent à une clé spécifiée.|
|[multiset::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[multiset::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|
|[multiset::equal_range (STL/CLR)](#equal_range)|Recherche une plage qui correspond à une clé spécifiée.|
|[multiset::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|
|[multiset::find (STL/CLR)](#find)|Recherche un élément qui correspond à une clé spécifiée.|
|[multiset::insert (STL/CLR)](#insert)|Ajoute des éléments.|
|[multiset::key_comp (STL/CLR)](#key_comp)|Copie le délégué de classement pour deux clés.|
|[multiset::lower_bound (STL/CLR)](#lower_bound)|Recherche le début de la plage qui correspond à une clé spécifiée.|
|[multiset::make_value (STL/CLR)](#make_value)|Construit un objet de valeur.|
|[multiset::multiset (STL/CLR)](#multiset)|Construit un objet conteneur.|
|[multiset::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|
|[multiset::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|
|[multiset::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[multiset::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|
|[multiset::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée dans un nouveau tableau.|
|[multiset::upper_bound (STL/CLR)](#upper_bound)|Recherche la fin de la plage qui correspond à une clé spécifiée.|
|[multiset::value_comp (STL/CLR)](#value_comp)|Copie le délégué de classement pour deux valeurs d’élément.|

|Opérateur|Description|
|--------------|-----------------|
|[multiset::operator= (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|
|[operator!= (multiset) (STL/CLR)](#op_neq)|Détermine si un objet `multiset` n’est pas égal à un autre objet `multiset`.|
|[operator< (multiset) (STL/CLR)](#op_lt)|Détermine si un objet `multiset` est inférieur à un autre objet `multiset`.|
|[operator<= (multiset) (STL/CLR)](#op_lteq)|Détermine si un objet `multiset` est inférieur ou égal à un autre objet `multiset`.|
|[operator== (multiset) (STL/CLR)](#op_eq)|Détermine si un objet `multiset` est égal à un autre objet `multiset`.|
|[operator> (multiset) (STL/CLR)](#op_gt)|Détermine si un objet `multiset` est supérieur à un autre objet `multiset`.|
|[operator>= (multiset) (STL/CLR)](#op_gteq)|Détermine si un objet `multiset` est supérieur ou égal à un autre objet `multiset`.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|<xref:System.Collections.IEnumerable>|Séquencez les éléments.|
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|
|<xref:System.Collections.Generic.IEnumerable%601>|Séquencez les éléments typés.|
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|
|ITree\<clé, valeur >|Conserver le conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels. Elle insère des éléments dans une arborescence (quasi) équilibrée qu’elle continue de trier en modifiant les liens entre les nœuds, jamais en copiant le contenu d’un nœud vers un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber les éléments restants.

L’objet trie la séquence qu’il contrôle en appelant un objet délégué stocké de type [multijeu :: key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stocké quand vous construisez le multiensemble ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(key_type, key_type)`. Vous accédez à cet objet stocké en appelant la fonction membre multiensemble [:: key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.

Un tel objet délégué doit imposer un classement faible strict sur les clés de type multiensemble [:: KEY_TYPE (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). Autrement dit, pour deux clés `X` et `Y`:

`key_comp()(X, Y)` retourne le même résultat booléen pour chaque appel.

Si `key_comp()(X, Y)` a la valeur true, `key_comp()(Y, X)` doit avoir la valeur false.

Si `key_comp()(X, Y)` a la valeur true, `X` est dit trié avant `Y`.

Si `!key_comp()(X, Y) && !key_comp()(Y, X)` a la valeur true, `X` et `Y` sont considérés comme ayant un ordre équivalent.

Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet délégué par défaut, les clés ne diminuent jamais la valeur.) Contrairement à la classe de modèle [Set (STL/CLR)](../dotnet/set-stl-clr.md), un objet de classe de modèle `multiset` ne requiert pas que les clés pour tous les éléments soient uniques. (Au moins deux clés peuvent avoir un classement équivalent.)

Chaque élément sert à la fois de EY et de valeur. La séquence est représentée de façon à permettre la recherche, l’insertion et la suppression d’un élément arbitraire avec un nombre d’opérations proportionnel au logarithme du nombre d’éléments dans la séquence (temps logarithmique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.

Un multiensemble prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez effectuer un pas à pas vers des éléments adjacents en fonction d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [multijeu :: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur pour atteindre le dernier élément de la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de multiensemble pour atteindre le nœud principal, et il est alors considéré comme égal à `end()`. Toutefois, vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.

Notez que vous ne pouvez pas faire référence à un élément de multiensemble directement en fonction de sa position numérique, qui requiert un itérateur à accès aléatoire.

Un itérateur de multiensemble stocke un handle vers son nœud multiensemble associé, qui à son tour stocke un handle vers son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec leurs objets conteneur associés. Un itérateur de multiensemble reste valide tant que son nœud multiensemble associé est associé à un multiensemble. En outre, un itérateur valide est déréférençable. vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne, tant qu’il n’est pas égal à `end()`.

L’effacement ou la suppression d’un élément appelle le destructeur pour sa valeur stockée. La destruction du conteneur efface tous les éléments. Ainsi, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne se trouve dans le conteneur. Notez, toutefois, qu’un conteneur de handles ne détruit *pas* ses éléments.

## <a name="members"></a>Membres

## <a name="multisetbegin-stlclr"></a><a name="begin"></a>multijeu :: Begin (STL/CLR)

Désigne le début de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur bidirectionnel qui désigne le premier élément de la séquence contrôlée, ou juste après la fin d’une séquence vide. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::iterator it = c1.begin();
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

## <a name="multisetclear-stlclr"></a><a name="clear"></a>multijeu :: Clear (STL/CLR)

Supprime tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Notes

La fonction membre appelle efficacement multiensemble [:: Erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)`(` [multijeu :: Begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)`(),` [multijeu :: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`())`. Vous pouvez l’utiliser pour vous assurer que la séquence contrôlée est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetconst_iterator-stlclr"></a><a name="const_iterator"></a>multijeu :: const_iterator (STL/CLR)

Type d'un itérateur constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T2` qui peut servir d’itérateur bidirectionnel constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reference-stlclr"></a><a name="const_reference"></a>multijeu :: const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>multijeu :: const_reverse_iterator (STL/CLR)

Type d’un itérateur inverse constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T4` qui peut servir d’itérateur inverse constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetcount-stlclr"></a><a name="count"></a>multijeu :: Count (STL/CLR)

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
// cliext_multiset_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetdifference_type-stlclr"></a><a name="difference_type"></a>multiensemble ::d ifference_type (STL/CLR)

Types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments éventuellement négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::difference_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultiset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="multisetempty-stlclr"></a><a name="empty"></a>multijeu :: Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle est équivalente à multiensemble [:: Size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)`() == 0`. Vous l’utilisez pour tester si le multiensemble est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetend-stlclr"></a><a name="end"></a>multijeu :: end (STL/CLR)

Désigne la fin de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur bidirectionnel qui pointe juste après la fin de la séquence contrôlée. Vous l’utilisez pour obtenir un itérateur qui désigne la fin de la séquence contrôlée ; son état ne change pas si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Mymultiset::iterator it = c1.end();
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

## <a name="multisetequal_range-stlclr"></a><a name="equal_range"></a>multijeu :: equal_range (STL/CLR)

Recherche une plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne une paire d’itérateurs `cliext::pair<iterator, iterator>(` [multijeu :: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)`(key),` [multijeu :: upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`. Vous l’utilisez pour déterminer la plage d’éléments actuellement dans la séquence contrôlée qui correspond à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
typedef Mymultiset::pair_iter_iter Pairii;
int main()
    {
    Mymultiset c1;
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

## <a name="multiseterase-stlclr"></a><a name="erase"></a>multijeu :: Erase (STL/CLR)

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

La première fonction membre supprime l’élément de la séquence contrôlée vers *laquelle*pointe, et retourne un itérateur qui désigne le premier élément restant après l’élément supprimé, ou [multijeu :: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()` si aucun élément de ce type n’existe. Vous l’utilisez pour supprimer un seul élément.

La deuxième fonction membre supprime les éléments de la séquence contrôlée dans la plage [`first`, `last`) et retourne un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `end()` si aucun élément de ce type n’existe. Vous l’utilisez pour supprimer zéro, un ou plusieurs éléments contigus.

La troisième fonction membre supprime tout élément de la séquence contrôlée dont la clé a un classement équivalent à la *clé*, et retourne le nombre d’éléments supprimés. Vous l’utilisez pour supprimer et compter tous les éléments qui correspondent à une clé spécifiée.

Chaque effacement d’élément prend du temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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
    Mymultiset::iterator it = c1.end();
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

## <a name="multisetfind-stlclr"></a><a name="find"></a>multijeu :: Find (STL/CLR)

Recherche un élément qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

Si au moins un élément de la séquence contrôlée a un classement équivalent avec la *clé*, la fonction membre retourne un itérateur désignant l’un de ces éléments ; Sinon, elle retourne [multijeu :: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Vous l’utilisez pour rechercher un élément actuellement dans la séquence contrôlée qui correspond à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetgeneric_container-stlclr"></a><a name="generic_container"></a>multijeu :: generic_container (STL/CLR)

Type de l’interface générique pour le conteneur.

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
// cliext_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
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

## <a name="multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>multijeu :: generic_iterator (STL/CLR)

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
// cliext_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>multijeu :: generic_reverse_iterator (STL/CLR)

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
// cliext_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="multisetgeneric_value-stlclr"></a><a name="generic_value"></a>multijeu :: generic_value (STL/CLR)

Type d’un élément à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké à utiliser avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetinsert-stlclr"></a><a name="insert"></a>multijeu :: Insert (STL/CLR)

Ajoute des éléments.

### <a name="syntax"></a>Syntaxe

```cpp
iterator insert(value_type val);
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

La première fonction membre insère un élément avec la valeur *Val*et retourne un itérateur qui désigne l’élément nouvellement inséré. Vous l’utilisez pour insérer un élément unique.

La deuxième fonction membre insère un élément avec la valeur *Val*, en utilisant *Where* comme indicateur (pour améliorer les performances) et retourne un itérateur qui désigne l’élément nouvellement inséré. Vous l’utilisez pour insérer un élément unique qui peut être adjacent à un élément que vous connaissez.

La troisième fonction membre insère la séquence [`first`, `last`). Vous l’utilisez pour insérer zéro, un ou plusieurs éléments copiés à partir d’une autre séquence.

La quatrième fonction membre insère la séquence désignée par la *droite*. Vous l’utilisez pour insérer une séquence décrite par un énumérateur.

Chaque insertion d’élément prend un temps proportionnel au logarithme du nombre d’éléments dans la séquence contrôlée. L’insertion peut se produire dans le temps constant amorti, en fonction d’une indication qui désigne un élément adjacent au point d’insertion.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

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
    Mymultiset c2;
    Mymultiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultiset c3;
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
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="multisetiterator-stlclr"></a><a name="iterator"></a>multijeu :: iterator (STL/CLR)

Type d'un itérateur pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur bidirectionnel pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetkey_comp-stlclr"></a><a name="key_comp"></a>multijeu :: key_comp (STL/CLR)

Copie le délégué de classement pour deux clés.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l'utilisez pour comparer deux clés.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
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

## <a name="multisetkey_compare-stlclr"></a><a name="key_compare"></a>multijeu :: key_compare (STL/CLR)

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
// cliext_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
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

## <a name="multisetkey_type-stlclr"></a><a name="key_type"></a>multijeu :: key_type (STL/CLR)

Type d'une clé de tri.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la *clé*de paramètre de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetlower_bound-stlclr"></a><a name="lower_bound"></a>multijeu :: lower_bound (STL/CLR)

Recherche le début de la plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine le premier élément `X` dans la séquence contrôlée qui a un classement équivalent à la *clé*. Si aucun élément de ce type n’existe, il retourne [multijeu :: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; Sinon, elle retourne un itérateur qui désigne `X`. Vous l’utilisez pour localiser le début d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetmake_value-stlclr"></a><a name="make_value"></a>multijeu :: make_value (STL/CLR)

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
// cliext_multiset_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(Mymultiset::make_value(L'a'));
    c1.insert(Mymultiset::make_value(L'b'));
    c1.insert(Mymultiset::make_value(L'c'));

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetmultiset-stlclr"></a><a name="multiset"></a>multijeu :: multimultijeu (STL/CLR)

Construit un objet conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
multiset();
explicit multiset(key_compare^ pred);
multiset(multiset<Key>% right);
multiset(multiset<Key>^ right);
template<typename InIter>
    multisetmultiset(InIter first, InIter last);
template<typename InIter>
    multiset(InIter first, InIter last,
        key_compare^ pred);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*prédit*<br/>
Prédicat de classement pour la séquence contrôlée.

*right*<br/>
Objet ou plage à insérer.

### <a name="remarks"></a>Notes

Le constructeur :

`multiset();`

Initialise la séquence contrôlée sans éléments, avec le prédicat de tri par défaut `key_compare()`. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de classement par défaut.

Le constructeur :

`explicit multiset(key_compare^ pred);`

Initialise la séquence contrôlée sans éléments, avec le prédicat de classement *prédit*. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide, avec le prédicat de tri spécifié.

Le constructeur :

`multiset(multiset<Key>% right);`

Initialise la séquence contrôlée avec la séquence [`right.begin()`, `right.end()`), avec le prédicat de classement par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de multiensemble *droit*, avec le prédicat de classement par défaut.

Le constructeur :

`multiset(multiset<Key>^ right);`

Initialise la séquence contrôlée avec la séquence [`right->begin()`, `right->end()`), avec le prédicat de classement par défaut. Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de multiensemble *droit*, avec le prédicat de classement par défaut.

Le constructeur :

`template<typename InIter> multiset(InIter first, InIter last);`

Initialise la séquence contrôlée avec la séquence [`first`, `last`), avec le prédicat de classement par défaut. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec le prédicat de classement par défaut.

Le constructeur :

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

Initialise la séquence contrôlée avec la séquence [`first`, `last`), avec le prédicat de classement *prédit*. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence, avec le prédicat de tri spécifié.

Le constructeur :

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Initialise la séquence contrôlée avec la séquence désignée par l’énumérateur à *droite*, avec le prédicat de classement par défaut. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec le prédicat de tri par défaut.

Le constructeur :

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Initialise la séquence contrôlée avec la séquence désignée par le *droit*d’énumérateur, avec le prédicat de classement *prédit*. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur, avec le prédicat de tri spécifié.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
// construct an empty container
    Mymultiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mymultiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultiset c8(%c3);
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

## <a name="multisetoperator-stlclr"></a><a name="op_as"></a>multijeu :: Operator = (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Conteneur à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* vers l’objet, puis retourne `*this`. Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *Right*.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Mymultiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="multisetrbegin-stlclr"></a><a name="rbegin"></a>multijeu :: rbegin (STL/CLR)

Désigne le début de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultiset::reverse_iterator rit = c1.rbegin();
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

## <a name="multisetreference-stlclr"></a><a name="reference"></a>multijeu :: Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetrend-stlclr"></a><a name="rend"></a>multijeu :: rend (STL/CLR)

Désigne la fin de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne la fin `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::reverse_iterator rit = c1.rend();
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

## <a name="multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>multijeu :: reverse_iterator (STL/CLR)

Type d'un itérateur inverse pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T3` qui peut servir d’itérateur inverse pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetsize-stlclr"></a><a name="size"></a>multijeu :: Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous vous intéressez uniquement si la séquence a une taille différente de zéro, consultez multiensemble [:: Empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetsize_type-stlclr"></a><a name="size_type"></a>multijeu :: size_type (STL/CLR)

Type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments non négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::size_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="multisetswap-stlclr"></a><a name="swap"></a>multijeu :: swap (STL/CLR)

Échange le contenu de deux conteneurs.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*right*<br/>
Conteneur avec lequel échanger le contenu.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre `this` et *Right*. Elle le fait en temps constant et ne lève aucune exception. Vous l’utilisez comme un moyen rapide d’échanger le contenu de deux conteneurs.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultiset c2;
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

## <a name="multisetto_array-stlclr"></a><a name="to_array"></a>multijeu :: to_array (STL/CLR)

Copie la séquence contrôlée dans un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetupper_bound-stlclr"></a><a name="upper_bound"></a>multijeu :: upper_bound (STL/CLR)

Recherche la fin de la plage qui correspond à une clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à rechercher.

### <a name="remarks"></a>Notes

La fonction membre détermine le dernier élément `X` dans la séquence contrôlée qui a un classement équivalent à la *clé*. Si aucun élément de ce type n’existe, ou si `X` est le dernier élément de la séquence contrôlée, elle retourne [multijeu :: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; Sinon, elle retourne un itérateur qui désigne le premier élément au-delà de `X`. Vous l’utilisez pour localiser la fin d’une séquence d’éléments actuellement dans la séquence contrôlée qui correspondent à une clé spécifiée.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
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

## <a name="multisetvalue_comp-stlclr"></a><a name="value_comp"></a>multijeu :: value_comp (STL/CLR)

Copie le délégué de classement pour deux valeurs d’élément.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Notes

La fonction membre retourne le délégué de classement utilisé pour ordonner la séquence contrôlée. Vous l’utilisez pour comparer deux valeurs d’éléments.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

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

## <a name="multisetvalue_compare-stlclr"></a><a name="value_compare"></a>multijeu :: value_compare (STL/CLR)

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
// cliext_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

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

## <a name="multisetvalue_type-stlclr"></a><a name="value_type"></a>multijeu :: value_type (STL/CLR)

Type d'un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `generic_value`.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-multiset-stlclr"></a><a name="op_neq"></a>Operator ! = (multiensemble) (STL/CLR)

Comparaison de liste non équivalente.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne `!(left == right)`. Vous l’utilisez pour tester si *Left* n’est pas *ordonné de la même façon que* lorsque les deux multijeux sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
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

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lt"></a>&lt; d’opérateur (multiensemble) (STL/CLR)

Liste inférieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne true si, pour la position la plus basse `i` pour laquelle `!(right[i] < left[i])` il est également vrai que `left[i] < right[i]`. Dans le cas contraire, elle retourne `left->size() < right->size()` vous l’utilisez pour déterminer si la *gauche* est triée avant *le* moment où les deux multijeux sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
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

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lteq"></a>opérateur&lt;= (multiensemble) (STL/CLR)

Liste des comparaisons inférieures ou égales.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne `!(right < left)`. Vous l’utilisez pour tester si *Left* n’est pas ordonné après *le* moment où les deux multijeux sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
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

## <a name="operator-multiset-stlclr"></a><a name="op_eq"></a>opérateur = = (multiensemble) (STL/CLR)

Comparaison d’égalité de liste.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne true uniquement si les séquences contrôlées par *Left* et *Right* ont la même longueur et, pour chaque position `i`, `left[i] ==` `right[i]`. Vous l’utilisez pour tester si *Left* est *ordonné de la même façon que* lorsque les deux multijeux sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
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

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gt"></a>&gt; d’opérateur (multiensemble) (STL/CLR)

Liste supérieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne `right` `<` `left`. Vous l’utilisez pour tester si la *gauche* est triée après *le* moment où les deux multijeux sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
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

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gteq"></a>opérateur&gt;= (multiensemble) (STL/CLR)

Liste de comparaison supérieure ou égale à.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Paramètres

*left*<br/>
Conteneur de gauche à comparer.

*right*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne `!(left < right)`. Vous l’utilisez pour tester si *Left* n’est pas ordonné *avant le moment où* les deux multijeux sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_multiset_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
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
