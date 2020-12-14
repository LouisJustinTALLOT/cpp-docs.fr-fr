---
description: 'En savoir plus sur : classe regex_token_iterator'
title: regex_token_iterator, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 752ff44864b435100bacb83250a5c6a792cab502
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243885"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator, classe

Classe d’itérateur pour les sous-correspondances.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Paramètres

*BidIt*\
Type d'itérateur pour les sous-correspondances.

*Elem*\
Type des éléments à faire correspondre.

*RXtraits*\
Classe Traits des éléments.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet itérateur Forward constant. D’un point de vue conceptuel, elle contient un objet `regex_iterator` utilisé pour la recherche d’expressions régulières dans une séquence de caractères. Elle extrait des objets de type `sub_match<BidIt>` représentant les sous-correspondances identifiées par les valeurs d’index dans le vecteur stocké `subs` pour chaque correspondance d’expression régulière.

La valeur d’index -1 désigne la séquence de caractères qui commence immédiatement après la fin de la correspondance d’expression régulière précédente, ou le début de la séquence de caractères en l’absence de correspondance d’expression régulière précédente. Par ailleurs, la séquence s’étend jusqu’au premier caractère (sans l’inclure) de la correspondance d’expression régulière actuelle, ou jusqu’à la fin de la séquence de caractères en l’absence de correspondance actuelle. Toute autre valeur d’index `idx` désigne le contenu du groupe de capture situé dans `it.match[idx]`.

### <a name="members"></a>Membres

|Membre|Valeur par défaut|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|Construit l’itérateur.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[difference_type](#difference_type)|Type d’une différence d’itérateur.|
|[iterator_category](#iterator_category)|Type de la catégorie d'itérateur.|
|[dirigé](#pointer)|Type d'un pointeur vers une correspondance.|
|[reference](#reference)|Type d’une référence à une sous-correspondance.|
|[regex_type](#regex_type)|Type de l’expression régulière à mettre en correspondance.|
|[value_type](#value_type)|Type d’une sous-correspondance.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! =](#op_neq)|Compare l’inégalité d’itérateurs.|
|[and](#op_star)|Accède à la sous-correspondance désignée.|
|[opérateur + +](#op_add_add)|Incrémente l'itérateur.|
|[opérateur = =](#op_eq_eq)|Compare des itérateurs pour déterminer s’ils sont égaux.|
|[>Operator ](#op_arrow)|Accède à la sous-correspondance désignée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<regex>

**Espace de noms :** std

## <a name="example"></a>Exemple

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a> regex_token_iterator ::d ifference_type

Type d’une différence d’itérateur.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `std::ptrdiff_t`.

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a> regex_token_iterator :: iterator_category

Type de la catégorie d'itérateur.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `std::forward_iterator_tag`.

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a> regex_token_iterator :: Operator ! =

Compare l’inégalité d’itérateurs.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur auquel comparer.

### <a name="remarks"></a>Notes

La fonction membre retourne `!(*this == right)`.

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a> regex_token_iterator :: Operator *

Accède à la sous-correspondance désignée.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un objet `sub_match<BidIt>` représentant le groupe de capture identifié par la valeur d’index `subs[pos]`.

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a> regex_token_iterator :: Operator + +

Incrémente l'itérateur.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Notes

Si l'itérateur stocké `it` est un itérateur de fin de séquence, le premier opérateur définit la valeur stockée `pos` à la valeur de `subs.size()` (ce qui crée un itérateur de fin de séquence). Sinon, l'opérateur incrémente la valeur stockée `pos` ; si le résultat est égal à la valeur `subs.size()`, il définit la valeur stockée `pos` à zéro et incrémente l'itérateur stocké `it`. Si, suite à son incrémentation, l'itérateur est inégal à un itérateur de fin de séquence, l'opérateur ne fait rien de plus. Sinon, si la fin de la correspondance précédente était à la fin de la séquence de caractères, l'opérateur définit la valeur stockée de `pos` à `subs.size()`. Sinon, l'opérateur incrémente de manière répétée la valeur stockée `pos` jusqu'à `pos == subs.size()` ou `subs[pos] == -1` (garantissant ainsi que le déréférencement suivant de l'itérateur retournera la fin de la séquence de caractères si l'une des valeurs d'index est -1). Dans tous les cas, l'opérateur retourne l'objet.

Le deuxième opérateur effectue une copie de l'objet, incrémente l'objet, puis retourne la copie.

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a> regex_token_iterator :: Operator = =

Compare des itérateurs pour déterminer s’ils sont égaux.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur auquel comparer.

### <a name="remarks"></a>Notes

La fonction membre retourne `it == right.it && subs == right.subs && pos == right.pos`.

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a> regex_token_iterator :: Operator-&gt;

Accède à la sous-correspondance désignée.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Notes

La fonction membre retourne un pointeur vers un objet `sub_match<BidIt>` représentant le groupe de capture identifié par la valeur d’index `subs[pos]`.

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a> regex_token_iterator ::p ointer

Type d'un pointeur vers une correspondance.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `sub_match<BidIt>*`, où `BidIt` est le paramètre de modèle.

## <a name="regex_token_iteratorreference"></a><a name="reference"></a> regex_token_iterator :: référence

Type d’une référence à une sous-correspondance.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `sub_match<BidIt>&`, où `BidIt` est le paramètre de modèle.

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a> regex_token_iterator :: regex_token_iterator

Construit l’itérateur.

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Paramètres

*premier*\
Début de la séquence à mettre en correspondance.

*famille*\
Fin de la séquence à mettre en correspondance.

*rouvert*\
Expression régulière pour les correspondances.

*FA*\
Indicateurs pour les correspondances.

### <a name="remarks"></a>Notes

Le premier constructeur construit un itérateur de fin de séquence.

Le second constructeur construit un objet dont l’itérateur stocké `it` est initialisé à `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, dont le vecteur stocké `subs` contient seulement un entier, ayant la valeur `submatch`, et dont la valeur stockée `pos` est égale à zéro. Remarque : l’objet résultant extrait la sous-correspondance identifiée par la valeur d’index `submatch` pour chaque correspondance d’expression régulière réussie.

Le troisième constructeur construit un objet dont l’itérateur stocké `it` est initialisé à `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, dont le vecteur stocké `subs` contient une copie de l’argument de constructeur `submatches`, et dont la valeur stockée `pos` est égale à zéro.

Le quatrième constructeur construit un objet dont l’itérateur stocké `it` est initialisé à `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, dont le vecteur stocké `subs` contient les valeurs `N` vers lesquelles pointe l’argument de constructeur `submatches`, et dont la valeur stockée `pos` est égale à zéro.

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a> regex_token_iterator :: regex_type

Type de l’expression régulière à mettre en correspondance.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de `basic_regex<Elem, RXtraits>`.

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a> regex_token_iterator :: value_type

Type d’une sous-correspondance.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `sub_match<BidIt>`, où `BidIt` est le paramètre de modèle.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[Classe regex_constants](../standard-library/regex-constants-class.md)\
[Classe regex_error](../standard-library/regex-error-class.md)\
[\<regex> Mission](../standard-library/regex-functions.md)\
[Classe regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex> Operator](../standard-library/regex-operators.md)\
[Classe regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
