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
ms.openlocfilehash: faf7f607f9433fa3e4813957b24220a5e66e1e49
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008609"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Incluez l’en-tête STL/CLR `<cliext/utility>` pour définir la classe de modèle `pair` et plusieurs fonctions de modèle de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>
```

## <a name="requirements"></a>Configuration requise

**En-tête :**\<cliext/utility>

**Espace de noms :** cliext

## <a name="declarations"></a>Déclarations

|Classe|Description|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Encapsuler une paire d’éléments.|

|Opérateur|Description|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Comparaison d’égalité des paires.|
|[Operator ! = (paire) (STL/CLR)](#op_neq)|Comparaison non équivalente.|
|[< d’opérateur (paire) (STL/CLR)](#op_lt)|Couple inférieur à la comparaison.|
|[Operator \< = (paire) (STL/CLR)](#op_lteq)|Comparaison de paires inférieure ou égale à.|
|[> d’opérateur (paire) (STL/CLR)](#op_gt)|Paire supérieure à la comparaison.|
|[opérateur>= (paire) (STL/CLR)](#op_gteq)|Comparaison de paires supérieur ou égal à.|

|Fonction|Description|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Créer une paire à partir d’une paire de valeurs.|

## <a name="pair-stlclr"></a><a name="pair"></a> paire (STL/CLR)

La classe de modèle décrit un objet qui encapsule une paire de valeurs.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Paramètres

*Value*<br/>
Type de première valeur encapsulée.

*Value2*<br/>
Type de la deuxième valeur encapsulée.

## <a name="members"></a>Membres

|Définition de type|Description|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Type de la première valeur encapsulée.|
|[pair::second_type (STL/CLR)](#second_type)|Type de la deuxième valeur encapsulée.|

|Member, objet|Description|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|Première valeur stockée.|
|[pair::second (STL/CLR)](#second)|Deuxième valeur stockée.|

|Fonction membre|Description|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Construit un objet pair.|
|[pair::swap (STL/CLR)](#swap)|Échange le contenu de deux paires.|

|Opérateur|Description|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Remplace la paire de valeurs stockée.|

## <a name="remarks"></a>Notes

L’objet stocke une paire de valeurs. Vous utilisez cette classe de modèle pour combiner deux valeurs en un seul objet. En outre, l’objet `cliext::pair` (décrit ici) stocke uniquement les types managés ; pour stocker une paire de types non managés `std::pair` , utilisez, déclaré dans `<utility>` .

## <a name="pairfirst-stlclr"></a><a name="first"></a> pair :: First (STL/CLR)

Première valeur encapsulée.

### <a name="syntax"></a>Syntaxe

```cpp
Value1 first;
```

### <a name="remarks"></a>Notes

L’objet stocke la première valeur encapsulée.

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a> paire :: first_type (STL/CLR)

Type de la première valeur encapsulée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *value1*.

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a> pair :: Operator = (STL/CLR)

Remplace la paire de valeurs stockée.

### <a name="syntax"></a>Syntaxe

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Paire à copier.

### <a name="remarks"></a>Notes

L’opérateur membre copie *directement* vers l’objet, puis retourne **`*this`** . Vous l’utilisez pour remplacer la paire de valeurs stockée par une copie de la paire de valeurs stockée dans *Right*.

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a> paire ::p air (STL/CLR)

Construit un objet pair.

### <a name="syntax"></a>Syntaxe

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Couple à stocker.

*val1*<br/>
Première valeur à stocker.

*val2*<br/>
Deuxième valeur à stocker.

### <a name="remarks"></a>Notes

Le constructeur :

`pair();`

Initialise la paire stockée avec les valeurs construites par défaut.

Le constructeur :

`pair(pair<Value1, Value2>% right);`

Initialise la paire stockée avec la paire `right.` [:: First (STL/CLR)](#first) et la `right.` [paire :: second (STL/CLR)](#second).

`pair(pair<Value1, Value2>^ right);`

Initialise la paire stockée avec la paire `right->` [:: First (STL/CLR)](#first) et la `right>` [paire :: second (STL/CLR)](#second).

Le constructeur :

`pair(Value1 val1, Value2 val2);`

Initialise la paire stockée avec *val1* et *val2*.

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

## <a name="pairsecond-stlclr"></a><a name="second"></a> paire :: second (STL/CLR)

Deuxième valeur encapsulée.

### <a name="syntax"></a>Syntaxe

```cpp
Value2 second;
```

### <a name="remarks"></a>Notes

L’objet stocke la deuxième valeur encapsulée.

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a> paire :: second_type (STL/CLR)

Type de la deuxième valeur encapsulée.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *value2*.

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

## <a name="pairswap-stlclr"></a><a name="swap"></a> paire :: swap (STL/CLR)

Échange le contenu de deux paires.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*Oui*<br/>
Coupler pour échanger le contenu avec.

### <a name="remarks"></a>Notes

La fonction membre permute la paire de valeurs stockée entre **`*this`** et *Right*.

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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a> make_pair (STL/CLR)

Créer un `pair` à partir d’une paire de valeurs.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Paramètres

*Value*<br/>
Type de la première valeur encapsulée.

*Value2*<br/>
Type de la deuxième valeur encapsulée.

*first*<br/>
Première valeur à inclure dans un wrapper.

*second*<br/>
Deuxième valeur à inclure dans un wrapper.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `pair<Value1, Value2>(first, second)`. Vous l’utilisez pour construire un `pair<Value1, Value2>` objet à partir d’une paire de valeurs.

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a> Operator ! = (paire) (STL/CLR)

Comparaison non équivalente.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Paire à droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(left == right)` . Vous l’utilisez pour tester si *Left* n’est pas *ordonné de la même manière que* si les deux paires sont comparées élément par élément.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a> opérateur &lt; (paire) (STL/CLR)

Couple inférieur à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Paire à droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second` . Vous l’utilisez pour vérifier si *Left* est *ordonné avant le moment où* les deux paires sont comparées élément par élément.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a> Operator &lt; = (paire) (STL/CLR)

Comparaison de paires inférieure ou égale à.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Paire à droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(right < left)` . Vous l’utilisez pour tester si *Left* n’est pas trié après *le* moment où les deux paires sont comparées élément par élément.

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a> opérateur = = (paire) (STL/CLR)

Comparaison d’égalité des paires.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Paire à droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `left.first ==` `right.first &&` `left.second ==` `right.second` . Vous l’utilisez pour vérifier si *Left* est *ordonné de la même manière que* si les deux paires sont comparées élément par élément.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a> opérateur &gt; (paire) (STL/CLR)

Paire supérieure à la comparaison.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Paire à droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `right` `<` `left` . Vous l’utilisez pour vérifier si *Left* est ordonné après *le* moment où les deux paires sont comparées élément par élément.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a> Operator &gt; = (paire) (STL/CLR)

Comparaison de paires supérieur ou égal à.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Paramètres

*gauche*<br/>
Paire gauche à comparer.

*Oui*<br/>
Paire à droite à comparer.

### <a name="remarks"></a>Notes

La fonction opérateur retourne `!(left < right)` . Vous l’utilisez pour tester si *Left* n’est pas trié *avant le moment où* les deux paires sont comparées élément par élément.

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
