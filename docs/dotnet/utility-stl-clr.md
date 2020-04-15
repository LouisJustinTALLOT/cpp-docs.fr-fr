---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320286"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Inclure l’en-tête `<cliext/utility>` STL/CLR `pair` pour définir la classe de modèle et plusieurs fonctions de modèle de support.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>
```

## <a name="requirements"></a>Spécifications

**En-tête:** \<cliext/utility>

**Espace nom:** cliext

## <a name="declarations"></a>Déclarations

|Classe|Description|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Envelopper une paire d’éléments.|

|Opérateur|Description|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Paire comparaison égale.|
|[opérateur! (paire) (STL/CLR)](#op_neq)|Paire pas comparaison égale.|
|[< (paire) (STL/CLR)](#op_lt)|Paire moins que la comparaison.|
|[opérateur\<(paire) (STL/CLR)](#op_lteq)|Paire moins ou comparaison égale.|
|[> (paire) (STL/CLR)](#op_gt)|Paire plus grande que la comparaison.|
|[opérateur>(paire) (STL/CLR)](#op_gteq)|Paire plus grande que ou égale comparaison.|

|Fonction|Description|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Faites une paire à partir d’une paire de valeurs.|

## <a name="members"></a>Membres

## <a name="pair-stlclr"></a><a name="pair"></a>paire (STL/CLR)

La classe de modèle décrit un objet qui enveloppe une paire de valeurs.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Paramètres

*Valeur1*<br/>
Le type de première valeur enveloppée.

*Valeur2*<br/>
Le type de deuxième valeur enveloppée.

## <a name="members"></a>Membres

|Définition de types|Description|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Le type de la première valeur enveloppée.|
|[pair::second_type (STL/CLR)](#second_type)|Le type de la deuxième valeur enveloppée.|

|Objet membre|Description|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|La première valeur stockée.|
|[pair::second (STL/CLR)](#second)|La deuxième valeur stockée.|

|Fonction membre|Description|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Construit un objet de paire.|
|[pair::swap (STL/CLR)](#swap)|Échange le contenu de deux paires.|

|Opérateur|Description|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Remplace la paire de valeurs stockées.|

## <a name="remarks"></a>Notes

L’objet stocke une paire de valeurs. Vous utilisez cette classe de modèle pour combiner deux valeurs en un seul objet. En outre, `cliext::pair` l’objet (décrit ici) ne stocke que les types gérés; pour stocker une paire de types `std::pair`non `<utility>`gérants utiliser , déclaré dans .

## <a name="pairfirst-stlclr"></a><a name="first"></a>paire::premier (STL/CLR)

La première valeur enveloppée.

### <a name="syntax"></a>Syntaxe

```cpp
Value1 first;
```

### <a name="remarks"></a>Notes

L’objet stocke la première valeur enveloppée.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>paire:first_type (STL/CLR)

Le type de la première valeur enveloppée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Notes

Le type est synonyme du paramètre du modèle *Value1*.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>paire::opérateur (STL/CLR)

Remplace la paire de valeurs stockées.

### <a name="syntax"></a>Syntaxe

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Paire à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* l’objet, puis renvoie `*this`. Vous l’utilisez pour remplacer la paire de valeurs stockées par une copie de la paire de valeurs stockées à *droite.*

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>paire::pair (STL/CLR)

Construit un objet de paire.

### <a name="syntax"></a>Syntaxe

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Paire à stocker.

*val1*<br/>
Première valeur à stocker.

*val2*<br/>
Deuxième valeur à stocker.

### <a name="remarks"></a>Notes

Le constructeur:

`pair();`

initialise la paire stockée avec des valeurs construites par défaut.

Le constructeur:

`pair(pair<Value1, Value2>% right);`

initialise la paire `right.`stockée avec [paire::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) et `right.` [paire::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

initialise la paire `right->`stockée avec [paire::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) et `right>` [paire::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

Le constructeur:

`pair(Value1 val1, Value2 val2);`

initialise la paire stockée avec *val1* et *val2*.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a>paire:deuxième (STL/CLR)

La deuxième valeur enveloppée.

### <a name="syntax"></a>Syntaxe

```cpp
Value2 second;
```

### <a name="remarks"></a>Notes

L’objet stocke la deuxième valeur enveloppée.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>paire:second_type (STL/CLR)

Le type de la deuxième valeur enveloppée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Notes

Le type est synonyme du paramètre du modèle *Value2*.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a>paire::swap (STL/CLR)

Échange le contenu de deux paires.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Paire pour échanger le contenu avec.

### <a name="remarks"></a>Notes

La fonction membre échange la paire `*this` de valeurs stockée entre et *à droite*.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair (STL/CLR)

Faites `pair` un à partir d’une paire de valeurs.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Paramètres

*Valeur1*<br/>
Le type de la première valeur enveloppée.

*Valeur2*<br/>
Le type de la deuxième valeur enveloppée.

*Première*<br/>
Première valeur à envelopper.

*Deuxième*<br/>
Deuxième valeur à envelopper.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `pair<Value1, Value2>(first, second)`. Vous l’utilisez `pair<Value1, Value2>` pour construire un objet à partir d’une paire de valeurs.

### <a name="example"></a>Exemple

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>opérateur! (paire) (STL/CLR)

Paire pas comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Bonne paire à comparer.

### <a name="remarks"></a>Notes

La fonction `!(left == right)`opérateur revient . Vous l’utilisez pour tester si *la gauche* n’est pas commandée de la même façon que *droite* lorsque les deux paires sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>opérateur&lt; (paire) (STL/CLR)

Paire moins que la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Bonne paire à comparer.

### <a name="remarks"></a>Notes

La fonction `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`opérateur revient . Vous l’utilisez pour tester si *la gauche* est commandée avant *droite* lorsque les deux paires sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>opérateur&lt;(paire) (STL/CLR)

Paire moins ou comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Bonne paire à comparer.

### <a name="remarks"></a>Notes

La fonction `!(right < left)`opérateur revient . Vous l’utilisez pour tester si *la gauche* n’est pas commandée après *le droit* lorsque les deux paires sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>(paire) (STL/CLR)

Paire comparaison égale.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Bonne paire à comparer.

### <a name="remarks"></a>Notes

La fonction `left.first ==` `right.first &&` `left.second ==` `right.second`opérateur revient . Vous l’utilisez pour tester si *la gauche* est commandée de la même façon que *droite* lorsque les deux paires sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>opérateur&gt; (paire) (STL/CLR)

Paire plus grande que la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Bonne paire à comparer.

### <a name="remarks"></a>Notes

La fonction `right` `<` `left`opérateur revient . Vous l’utilisez pour tester si *la gauche* est commandée après *droite* lorsque les deux paires sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>opérateur&gt;(paire) (STL/CLR)

Paire plus grande que ou égale comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Bonne paire à comparer.

### <a name="remarks"></a>Notes

La fonction `!(left < right)`opérateur revient . Vous l’utilisez pour tester si *la gauche* n’est pas commandée avant *à droite* lorsque les deux paires sont comparées élément par élément.

### <a name="example"></a>Exemple

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
