---
title: deque (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::deque
- cliext::deque::assign
- cliext::deque::at
- cliext::deque::back
- cliext::deque::back_item
- cliext::deque::begin
- cliext::deque::clear
- cliext::deque::const_iterator
- cliext::deque::const_reference
- cliext::deque::const_reverse_iterator
- cliext::deque::deque
- cliext::deque::difference_type
- cliext::deque::empty
- cliext::deque::end
- cliext::deque::erase
- cliext::deque::front
- cliext::deque::front_item
- cliext::deque::generic_container
- cliext::deque::generic_iterator
- cliext::deque::generic_reverse_iterator
- cliext::deque::generic_value
- cliext::deque::insert
- cliext::deque::iterator
- cliext::deque::operator!=
- cliext::deque::operator[]
- cliext::deque::pop_back
- cliext::deque::pop_front
- cliext::deque::push_back
- cliext::deque::push_front
- cliext::deque::rbegin
- cliext::deque::reference
- cliext::deque::rend
- cliext::deque::resize
- cliext::deque::reverse_iterator
- cliext::deque::size
- cliext::deque::size_type
- cliext::deque::swap
- cliext::deque::to_array
- cliext::deque::value_type
- cliext::deque::operator<
- cliext::deque::operator<=
- cliext::deque::operator=
- cliext::deque::operator==
- cliext::deque::operator>
- cliext::deque::operator>=
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- deque member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator!= member [STL/CLR]
- operator member [] [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
ms.openlocfilehash: 75c83240b9125628fd5121368af547a5266bfb5c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221495"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)

La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès aléatoire. Vous utilisez le conteneur `deque` pour gérer une séquence d’éléments qui ressemble à un bloc de stockage contigu, mais qui peut croître ou diminuer à la fin sans avoir besoin de copier les éléments restants. Il peut donc implémenter efficacement un `double-ended queue` . (Par conséquent, le nom.)

Dans la description ci-dessous, `GValue` est identique `Value` à, sauf si ce dernier est un type REF, auquel cas il s’agit de `Value^` .

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    ref class deque
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IDeque<GValue>
    { ..... };
```

### <a name="parameters"></a>Paramètres

*GValue*<br/>
Type générique d’un élément dans la séquence contrôlée.

*Valeur*<br/>
Type d'un élément dans la séquence contrôlée.

## <a name="requirements"></a>Spécifications

**En-tête :**\<cliext/deque>

**Espace de noms :** cliext

## <a name="declarations"></a>Déclarations

|Définition de type|Description|
|---------------------|-----------------|
|[deque::const_iterator (STL/CLR)](#const_iterator)|Type d'un itérateur constant pour la séquence contrôlée.|
|[deque::const_reference (STL/CLR)](#const_reference)|Type d'une référence constante à un élément.|
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Type d'un itérateur inserve constant pour la séquence contrôlée.|
|[deque::difference_type (STL/CLR)](#difference_type)|Type d'une distance signée entre deux éléments.|
|[deque::generic_container (STL/CLR)](#generic_container)|Type de l’interface générique pour le conteneur.|
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|Type d’un itérateur pour l’interface générique pour le conteneur.|
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Type d’un itérateur inverse pour l’interface générique pour le conteneur.|
|[deque::generic_value (STL/CLR)](#generic_value)|Type d’un élément pour l’interface générique pour le conteneur.|
|[deque::iterator (STL/CLR)](#iterator)|Type d'un itérateur pour la séquence contrôlée.|
|[deque::reference (STL/CLR)](#reference)|Type d'une référence à un élément.|
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|Type d'un itérateur inverse pour la séquence contrôlée.|
|[deque::size_type (STL/CLR)](#size_type)|Type d'une distance signée entre deux éléments.|
|[deque::value_type (STL/CLR)](#value_type)|Type d’un élément.|

|Fonction membre|Description|
|---------------------|-----------------|
|[deque::assign (STL/CLR)](#assign)|Remplace tous les éléments.|
|[deque::at (STL/CLR)](#at)|Accède à un élément à une position spécifiée.|
|[deque::back (STL/CLR)](#back)|Accède au dernier élément.|
|[deque::begin (STL/CLR)](#begin)|Désigne le début de la séquence contrôlée.|
|[deque::clear (STL/CLR)](#clear)|Supprime tous les éléments.|
|[deque::deque (STL/CLR)](#deque)|Construit un objet conteneur.|
|[deque::empty (STL/CLR)](#empty)|Vérifie l'absence d'éléments.|
|[deque::end (STL/CLR)](#end)|Désigne la fin de la séquence contrôlée.|
|[deque::erase (STL/CLR)](#erase)|Supprime les éléments placés aux positions spécifiées.|
|[deque::front (STL/CLR)](#front)|Accède au premier élément.|
|[deque::insert (STL/CLR)](#insert)|Ajoute des éléments à une position spécifiée.|
|[deque::pop_back (STL/CLR)](#pop_back)|Supprime le dernier élément.|
|[deque::pop_front (STL/CLR)](#pop_front)|Supprime le premier élément.|
|[deque::push_back (STL/CLR)](#push_back)|Ajoute un nouveau dernier élément.|
|[deque::push_front (STL/CLR)](#push_front)|Ajoute un nouveau premier élément.|
|[deque::rbegin (STL/CLR)](#rbegin)|Désigne le début de la séquence contrôlée inverse.|
|[deque::rend (STL/CLR)](#rend)|Désigne la fin de la séquence contrôlée inverse.|
|[deque::resize (STL/CLR)](#resize)|Change le nombre d'éléments.|
|[deque::size (STL/CLR)](#size)|Compte le nombre d'éléments.|
|[deque::swap (STL/CLR)](#swap)|Échange le contenu de deux conteneurs.|
|[deque::to_array (STL/CLR)](#to_array)|Copie la séquence contrôlée dans un nouveau tableau.|

|Propriété|Description|
|--------------|-----------------|
|[deque::back_item (STL/CLR)](#back_item)|Accède au dernier élément.|
|[deque::front_item (STL/CLR)](#front_item)|Accède au premier élément.|

|Opérateur|Description|
|--------------|-----------------|
|[deque::operator!= (STL/CLR)](#op_neq)|Détermine si deux objets `deque` ne sont pas égaux.|
|[deque::operator(STL/CLR)](#operator)|Accède à un élément à une position spécifiée.|
|[< d’opérateur (deque) (STL/CLR)](#op_lt)|Détermine si un `deque` objet est inférieur à un autre `deque` objet.|
|[operator<= (deque) (STL/CLR)](#op_lteq)|Détermine si un `deque` objet est inférieur ou égal à un autre `deque` objet.|
|[opérateur = (deque) (STL/CLR)](#op_as)|Remplace la séquence contrôlée.|
|[opérateur = = (deque) (STL/CLR)](#op_eq)|Détermine si un `deque` objet est égal à un autre `deque` objet.|
|[> d’opérateur (deque) (STL/CLR)](#op_gt)|Détermine si un `deque` objet est supérieur à un autre `deque` objet.|
|[opérateur>= (deque) (STL/CLR)](#op_gteq)|Détermine si un `deque` objet est supérieur ou égal à un autre `deque` objet.|

## <a name="interfaces"></a>Interfaces

|Interface|Description|
|---------------|-----------------|
|<xref:System.ICloneable>|Dupliquer un objet.|
|<xref:System.Collections.IEnumerable>|Séquencez les éléments.|
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|
|<xref:System.Collections.Generic.IEnumerable%601>|Séquencez les éléments typés.|
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|
|<xref:System.Collections.Generic.IList%601>|Gérer le groupe ordonné d’éléments typés.|
|Valeur de<IDeque\>|Conserver le conteneur générique.|

## <a name="remarks"></a>Notes

L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un tableau stocké de handles qui désignent des blocs d' `Value` éléments. Le tableau s’étend à la demande. La croissance se produit de telle sorte que le coût de l’attente ou de l’ajout d’un nouvel élément est constant et qu’aucun élément restant ne soit perturbé. Vous pouvez également supprimer un élément à la fin en temps constant et sans perturber les éléments restants. Par conséquent, un deque est un bon candidat pour le conteneur sous-jacent pour la file d’attente de classe de modèle [(STL/CLR)](../dotnet/queue-stl-clr.md) ou la pile de classes de modèle [(STL/CLR)](../dotnet/stack-stl-clr.md).

Un `deque` objet prend en charge les itérateurs à accès aléatoire, ce qui signifie que vous pouvez faire référence à un élément directement en fonction de sa position numérique, en comptant de zéro pour le premier élément (avant), à [deque :: Size (STL/CLR)](#size) `() - 1` pour le dernier élément (précédent). Cela signifie également qu’un deque est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Un itérateur deque stocke un handle vers l’objet deque associé, ainsi que le décalage de l’élément qu’il désigne. Vous pouvez utiliser des itérateurs uniquement avec leurs objets conteneur associés. Le décalage d’un élément deque n’est *pas* nécessairement le même que sa position. Le premier élément inséré a le biais du décalage zéro, l’élément ajouté suivant a le biais 1, mais l’élément ajouté suivant a la valeur Bias-1.

L’insertion ou l’effacement d’éléments à la fin n’altère *pas* la valeur d’un élément stocké à un biais valide. Toutefois, l’insertion ou l’effacement d’un élément intérieur *peut* modifier la valeur de l’élément stocké à un écart donné, de sorte que la valeur désignée par un itérateur peut également changer. (Le conteneur peut devoir copier des éléments vers le haut ou vers le haut pour créer un trou avant une insertion ou pour remplir un trou après une opération d’effacement.) Néanmoins, un itérateur deque reste valide tant que son biais désigne un élément valide. En outre, un itérateur valide reste déréférençable. vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne, tant que son biais n’est pas égal au décalage pour l’itérateur retourné par `end()` .

L’effacement ou la suppression d’un élément appelle le destructeur pour sa valeur stockée. La destruction du conteneur efface tous les éléments. Ainsi, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne se trouve dans le conteneur. Notez, toutefois, qu’un conteneur de handles ne détruit *pas* ses éléments.

## <a name="members"></a>Membres

## <a name="dequeassign-stlclr"></a><a name="assign"></a>deque :: assign (STL/CLR)

Remplace tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre d’éléments à insérer.

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*Oui*<br/>
Énumération à insérer.

*multiples*<br/>
Valeur de l’élément à insérer.

### <a name="remarks"></a>Notes

La première fonction membre remplace la séquence contrôlée par une répétition des éléments *Count* de la valeur *Val*. Vous l’utilisez pour remplir le conteneur avec des éléments ayant tous la même valeur.

Si `InIt` est un type entier, la deuxième fonction membre se comporte de la même façon que `assign((size_type)first, (value_type)last)` . Dans le cas contraire, elle remplace la séquence contrôlée par la séquence [ `first` , `last` ). Vous l’utilisez pour faire en sorte que la séquence contrôlée copie une autre séquence.

La troisième fonction membre remplace la séquence contrôlée par la séquence désignée par le *droit*de l’énumérateur. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une séquence décrite par un énumérateur.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_assign.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::deque<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="dequeat-stlclr"></a><a name="at"></a>deque :: at (STL/CLR)

Accède à un élément à une position spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Paramètres

*imprim*<br/>
Position de l'élément auquel accéder.

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à l’élément de la séquence contrôlée à la position *pos*. Vous l’utilisez pour lire ou écrire un élément dont vous connaissez la position.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_at.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

    // change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="dequeback-stlclr"></a><a name="back"></a>deque :: Back (STL/CLR)

Accède au dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
reference back();
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence au dernier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour accéder au dernier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

    // alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="dequeback_item-stlclr"></a><a name="back_item"></a>deque :: back_item (STL/CLR)

Accède au dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Notes

La propriété accède au dernier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour lire ou écrire le dernier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_back_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

    // alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="dequebegin-stlclr"></a><a name="begin"></a>deque :: Begin (STL/CLR)

Désigne le début de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur à accès aléatoire qui désigne le premier élément de la séquence contrôlée, ou juste après la fin d’une séquence vide. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_begin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="dequeclear-stlclr"></a><a name="clear"></a>deque :: Clear (STL/CLR)

Supprime tous les éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [deque :: Erase (STL/CLR)](#erase) `(` [deque :: Begin (STL/CLR)](#begin) `(),` [deque :: end (STL/CLR)](#end) `())` . Vous pouvez l’utiliser pour vous assurer que la séquence contrôlée est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_clear.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

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

## <a name="dequeconst_iterator-stlclr"></a><a name="const_iterator"></a>deque :: const_iterator (STL/CLR)

Type d'un itérateur constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T2` qui peut servir d’itérateur à accès aléatoire constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_const_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reference-stlclr"></a><a name="const_reference"></a>deque :: const_reference (STL/CLR)

Type d'une référence constante à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence constante à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_const_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::deque<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>deque :: const_reverse_iterator (STL/CLR)

Type d’un itérateur inverse constant pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T4` qui peut servir d’itérateur inverse constant pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::deque<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="dequedeque-stlclr"></a><a name="deque"></a>deque ::d eque (STL/CLR)

Construit un objet conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
deque();
deque(deque<Value>% right);
deque(deque<Value>^ right);
explicit deque(size_type count);
deque(size_type count, value_type val);
template<typename InIt>
    deque(InIt first, InIt last);
deque(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre d’éléments à insérer.

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*Oui*<br/>
Objet ou plage à insérer.

*multiples*<br/>
Valeur de l’élément à insérer.

### <a name="remarks"></a>Notes

Le constructeur :

`deque();`

Initialise la séquence contrôlée sans éléments. Vous l’utilisez pour spécifier une séquence contrôlée initiale vide.

Le constructeur :

`deque(deque<Value>% right);`

Initialise la séquence contrôlée à l’aide de la séquence [ `right.begin()` , `right.end()` ). Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par le *droit*de l’objet deque. Pour plus d’informations sur les itérateurs, consultez [deque :: Begin (STL/CLR)](#begin) et [deque :: end (STL/CLR)](#end).

Le constructeur :

`deque(deque<Value>^ right);`

Initialise la séquence contrôlée à l’aide de la séquence [ `right->begin()` , `right->end()` ). Vous l’utilisez pour spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet deque dont le descripteur est *correct*.

Le constructeur :

`explicit deque(size_type count);`

Initialise la séquence contrôlée avec les éléments *Count* chacun avec la valeur `value_type()` . Vous l’utilisez pour remplir le conteneur avec des éléments qui ont tous la valeur par défaut.

Le constructeur :

`deque(size_type count, value_type val);`

Initialise la séquence contrôlée avec les éléments *Count* chacun avec la valeur *Val*. Vous l’utilisez pour remplir le conteneur avec des éléments ayant tous la même valeur.

Le constructeur :

`template<typename InIt>`

`deque(InIt first, InIt last);`

Initialise la séquence contrôlée à l’aide de la séquence [ `first` , `last` ). Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence.

Le constructeur :

`deque(System::Collections::Generic::IEnumerable<Value>^ right);`

Initialise la séquence contrôlée avec la séquence désignée par le *droit*de l’énumérateur. Vous l’utilisez pour faire de la séquence contrôlée une copie d’une autre séquence décrite par un énumérateur.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_construct.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container
    cliext::deque<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::deque<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::deque<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::deque<wchar_t>::iterator it = c3.end();
    cliext::deque<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::deque<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::deque<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="dequedifference_type-stlclr"></a><a name="difference_type"></a>deque ::d ifference_type (STL/CLR)

Types d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments signés.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_difference_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::difference_type diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="dequeempty-stlclr"></a><a name="empty"></a>deque :: Empty (STL/CLR)

Vérifie l'absence d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true pour une séquence contrôlée vide. Elle équivaut à [deque :: Size (STL/CLR)](#size) `() == 0` . Vous l’utilisez pour vérifier si le deque est vide.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_empty.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

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

## <a name="dequeend-stlclr"></a><a name="end"></a>deque :: end (STL/CLR)

Désigne la fin de la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur à accès aléatoire qui pointe juste après la fin de la séquence contrôlée. Vous l'utilisez pour obtenir un itérateur qui désigne la fin `current` de la séquence contrôlée, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_end.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::deque<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="dequeerase-stlclr"></a><a name="erase"></a>deque :: Erase (STL/CLR)

Supprime les éléments placés aux positions spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la plage à effacer.

*last*<br/>
Fin de la plage à effacer.

*where*<br/>
Élément à effacer.

### <a name="remarks"></a>Notes

La première fonction membre supprime l’élément de la séquence contrôlée vers *laquelle*pointe. Vous l’utilisez pour supprimer un seul élément.

La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Vous l’utilisez pour supprimer zéro, un ou plusieurs éléments contigus.

Les deux fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [deque :: end (STL/CLR)](#end) `()` si aucun élément de ce type n’existe.

Lors de l’effacement des éléments, le nombre de copies d’éléments est linéaire dans le nombre d’éléments entre la fin de l’effacement et l’extrémité la plus proche de la séquence. (Lors de l’effacement d’un ou plusieurs éléments à la fin de la séquence, aucune copie d’élément ne se produit.)

### <a name="example"></a>Exemple

```cpp
// cliext_deque_erase.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequefront-stlclr"></a><a name="front"></a>deque :: Front (STL/CLR)

Accède au premier élément.

### <a name="syntax"></a>Syntaxe

```cpp
reference front();
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence au premier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

    // alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="dequefront_item-stlclr"></a><a name="front_item"></a>deque :: front_item (STL/CLR)

Accède au premier élément.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Notes

La propriété accède au premier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour lire ou écrire le premier élément, lorsque vous savez qu’il existe.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_front_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

    // alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="dequegeneric_container-stlclr"></a><a name="generic_container"></a>deque :: generic_container (STL/CLR)

Type de l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IDeque<generic_value>
    generic_container;
```

### <a name="remarks"></a>Notes

Le type décrit l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_generic_container.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
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

## <a name="dequegeneric_iterator-stlclr"></a><a name="generic_iterator"></a>deque :: generic_iterator (STL/CLR)

Type d’un itérateur à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value> generic_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un itérateur générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_generic_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="dequegeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>deque :: generic_reverse_iterator (STL/CLR)

Type d’un itérateur inverse à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un itérateur inverse générique qui peut être utilisé avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="dequegeneric_value-stlclr"></a><a name="generic_value"></a>deque :: generic_value (STL/CLR)

Type d’un élément à utiliser avec l’interface générique pour le conteneur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type `GValue` qui décrit la valeur de l’élément stocké à utiliser avec l’interface générique pour cette classe de conteneur de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_generic_value.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="dequeinsert-stlclr"></a><a name="insert"></a>deque :: Insert (STL/CLR)

Ajoute des éléments à une position spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre d’éléments à insérer.

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

*Oui*<br/>
Énumération à insérer.

*multiples*<br/>
Valeur de l’élément à insérer.

*where*<br/>
Où insérer dans le conteneur.

### <a name="remarks"></a>Notes

Chacune des fonctions membres insère, avant l’élément vers *lequel* pointe, dans la séquence contrôlée, une séquence spécifiée par les opérandes restants.

La première fonction membre insère un élément avec la valeur *Val* et retourne un itérateur qui désigne l’élément nouvellement inséré. Vous l’utilisez pour insérer un élément unique avant un emplacement désigné par un itérateur.

La deuxième fonction membre insère une répétition des éléments *Count* de la valeur *Val*. Vous l’utilisez pour insérer zéro, un ou plusieurs éléments contigus qui sont toutes des copies de la même valeur.

Si `InIt` est un type entier, la troisième fonction membre se comporte comme `insert(where, (size_type)first, (value_type)last)`. Sinon, elle insère la séquence [ `first` , `last` ). Vous l’utilisez pour insérer zéro, un ou plusieurs éléments contigus copiés à partir d’une autre séquence.

La quatrième fonction membre insère la séquence désignée par la *droite*. Vous l’utilisez pour insérer une séquence décrite par un énumérateur.

Lors de l’insertion d’un seul élément, le nombre de copies d’élément est linéaire dans le nombre d’éléments entre le point d’insertion et l’extrémité plus proche de la séquence. (Lors de l’insertion d’un ou plusieurs éléments à la fin de la séquence, aucune copie d’élément ne se produit.) Si `InIt` est un itérateur d’entrée, la troisième fonction membre effectue effectivement une insertion unique pour chaque élément de la séquence. Dans le cas contraire, lors de l’insertion `N` d’éléments, le nombre de copies d’éléments est linéaire dans `N` plus le nombre d’éléments entre le point d’insertion et l’extrémité plus proche de la séquence.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_insert.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::deque<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::deque<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="dequeiterator-stlclr"></a><a name="iterator"></a>deque :: iterator (STL/CLR)

Type d'un itérateur pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T1` qui peut servir d’itérateur d’accès aléatoire pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

    // alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="dequeoperator-stlclr"></a><a name="op_neq"></a>deque :: Operator ! = (STL/CLR)

Comparaison deque non égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator!=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(left == right)` . Vous l’utilisez pour tester si *Left* n’est pas *ordonné de la même manière que* si les deux classes deque sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_ne.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="dequeoperatorstlclr"></a><a name="operator"></a>deque ::, opérateur (STL/CLR)

Accède à un élément à une position spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Paramètres

*imprim*<br/>
Position de l'élément auquel accéder.

### <a name="remarks"></a>Notes

L’opérateur membre retourne un referene à l’élément à la position *pos*. Vous l’utilisez pour accéder à un élément dont vous connaissez la position.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_sub.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

    // change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="dequepop_back-stlclr"></a><a name="pop_back"></a>deque ::p op_back (STL/CLR)

Supprime le dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_back();
```

### <a name="remarks"></a>Notes

La fonction membre supprime le dernier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour raccourcir le deque d’un élément à l’arrière.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_pop_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="dequepop_front-stlclr"></a><a name="pop_front"></a>deque ::p op_front (STL/CLR)

Supprime le premier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_front();
```

### <a name="remarks"></a>Notes

La fonction membre supprime le premier élément de la séquence contrôlée, qui ne doit pas être vide. Vous l’utilisez pour raccourcir le deque d’un élément à l’avant.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_pop_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="dequepush_back-stlclr"></a><a name="push_back"></a>deque ::p ush_back (STL/CLR)

Ajoute un nouveau dernier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Notes

La fonction membre insère un élément avec une valeur `val` à la fin de la séquence contrôlée. Vous l’utilisez pour ajouter un autre élément au deque.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_push_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequepush_front-stlclr"></a><a name="push_front"></a>deque ::p ush_front (STL/CLR)

Ajoute un nouveau premier élément.

### <a name="syntax"></a>Syntaxe

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Notes

La fonction membre insère un élément avec une valeur `val` au début de la séquence contrôlée. Vous l’utilisez pour ajouter un autre élément au deque.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_push_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="dequerbegin-stlclr"></a><a name="rbegin"></a>deque :: rbegin (STL/CLR)

Désigne le début de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui désigne le dernier élément de la séquence contrôlée, ou juste après le début d’une séquence vide. Par conséquent, il désigne le `beginning` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne le début `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_rbegin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="dequereference-stlclr"></a><a name="reference"></a>deque :: Reference (STL/CLR)

Type d'une référence à un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Notes

Le type décrit une référence à un élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="dequerend-stlclr"></a><a name="rend"></a>deque :: rend (STL/CLR)

Désigne la fin de la séquence contrôlée inverse.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur inverse qui pointe juste après le début de la séquence contrôlée. Par conséquent, il désigne le `end` de la séquence inverse. Vous l'utilisez pour obtenir un itérateur qui désigne la fin `current` de la séquence contrôlée vue dans l'ordre inverse, mais son état peut changer si la longueur de la séquence contrôlée change.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_rend.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="dequeresize-stlclr"></a><a name="resize"></a>deque :: Resize (STL/CLR)

Change le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Paramètres

*new_size*<br/>
Nouvelle taille de la séquence contrôlée.

*multiples*<br/>
Valeur de l’élément de remplissage.

### <a name="remarks"></a>Notes

Les fonctions membres garantissent que [deque :: Size (STL/CLR)](#size) `()` retourne désormais *NEW_SIZE*. Si la séquence contrôlée doit être plus longue, la première fonction membre ajoute des éléments avec `value_type()` la valeur, tandis que la deuxième fonction membre ajoute des éléments avec la valeur *Val*. Pour rendre la séquence contrôlée plus concise, les deux fonctions membres effacent efficacement le dernier élément [deque :: Size (STL/CLR)](#size) `() -` `new_size` . Vous pouvez l’utiliser pour vous assurer que la séquence contrôlée a une taille *NEW_SIZE*, en découpant ou en remplissant la séquence contrôlée actuelle.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_resize.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container and pad with default values
    cliext::deque<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

    // resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="dequereverse_iterator-stlclr"></a><a name="reverse_iterator"></a>deque :: reverse_iterator (STL/CLR)

Type d'un itérateur inverse pour la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet de type non spécifié `T3` qui peut servir d’itérateur inverse pour la séquence contrôlée.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

    // alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="dequesize-stlclr"></a><a name="size"></a>deque :: Size (STL/CLR)

Compte le nombre d'éléments.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence contrôlée. Vous l’utilisez pour déterminer le nombre d’éléments actuellement dans la séquence contrôlée. Si vous vous intéressez uniquement si la séquence a une taille différente de zéro, consultez [deque :: Empty (STL/CLR)](#empty) `()` .

### <a name="example"></a>Exemple

```cpp
// cliext_deque_size.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
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

## <a name="dequesize_type-stlclr"></a><a name="size_type"></a>deque :: size_type (STL/CLR)

Type d’une distance signée entre deux éléments.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Notes

Le type décrit un nombre d’éléments non négatifs.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_size_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="dequeswap-stlclr"></a><a name="swap"></a>deque :: swap (STL/CLR)

Échange le contenu de deux conteneurs.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Conteneur avec lequel échanger le contenu.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre **`*this`** et *Right*. Elle le fait en temps constant et ne lève aucune exception. Vous l’utilisez comme un moyen rapide d’échanger le contenu de deux conteneurs.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_swap.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> c2(5, L'x');
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
x x x x x
x x x x x
a b c
```

## <a name="dequeto_array-stlclr"></a><a name="to_array"></a>deque :: to_array (STL/CLR)

Copie la séquence contrôlée dans un nouveau tableau.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un tableau contenant la séquence contrôlée. Vous l’utilisez pour obtenir une copie de la séquence contrôlée sous forme de tableau.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_to_array.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
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

## <a name="dequevalue_type-stlclr"></a><a name="value_type"></a>deque :: value_type (STL/CLR)

Type d’un élément.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la *valeur*de paramètre de modèle.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_value_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::deque<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operatorlt-deque-stlclr"></a><a name="op_lt"></a>, opérateur &lt; (deque) (STL/CLR)

Deque inférieur à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne true si, pour la position la plus basse `i` pour laquelle `!(right[i] < left[i])` elle est également true `left[i] < right[i]` . Dans le cas contraire, il retourne `left->size() < right->size()` que vous l’utilisez pour vérifier si *right* *Left* est ordonné avant le moment où les deux classes deque sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_lt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="operatorlt-deque-stlclr"></a><a name="op_lteq"></a>opérateur &lt; = (deque) (STL/CLR)

Deque est inférieur ou égal à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(right < left)` . Vous l’utilisez pour tester si *Left* n’est pas trié après *le* moment où les deux classes deque sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_le.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="operator-deque-stlclr"></a><a name="op_as"></a>opérateur = (deque) (STL/CLR)

Remplace la séquence contrôlée.

### <a name="syntax"></a>Syntaxe

```cpp
deque<Value>% operator=(deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Conteneur à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* vers l’objet, puis retourne **`*this`** . Vous l’utilisez pour remplacer la séquence contrôlée par une copie de la séquence contrôlée dans *Right*.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_as.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="operator-deque-stlclr"></a><a name="op_eq"></a>opérateur = = (deque) (STL/CLR)

Comparaison égale à deque.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator==(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction operator retourne true uniquement si les séquences contrôlées par *Left* et *Right* ont la même longueur et, pour chaque position `i` , `left[i] ==` `right[i]` . Vous l’utilisez pour vérifier si *Left* est *ordonné de la même manière que* si les deux classes deque sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_eq.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gt"></a>, opérateur &gt; (deque) (STL/CLR)

Deque supérieur à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `right` `<` `left` . Vous l’utilisez pour tester si *Left* est trié après *Right* lorsque les deux classes deque sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_gt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gteq"></a>opérateur &gt; = (deque) (STL/CLR)

Deque comparaison supérieure ou égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Conteneur de gauche à comparer.

*Oui*<br/>
Conteneur de droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(left` `<` `right)` . Vous l’utilisez pour tester si *Left* n’est pas trié avant *le* moment où les deux classes deque sont comparés élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_deque_operator_ge.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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
