---
description: 'En savoir plus sur : classe regex_iterator'
title: regex_iterator, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: 50595a863a6c56ddacffef2de68d04fd91fdd837
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240466"
---
# <a name="regex_iterator-class"></a>regex_iterator, classe

Classe d’itérateur pour les correspondances.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Paramètres

*BidIt*\
Type d'itérateur pour les sous-correspondances.

*Elem*\
Type des éléments à faire correspondre.

*RXtraits*\
Classe Traits des éléments.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet itérateur Forward constant. Elle extrait les objets de type `match_results<BidIt>` en appliquant à plusieurs reprises son objet d’expression régulière `*pregex` à la séquence de caractères définie par la plage d’itérateurs `[begin, end)`.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[regex_iterator](#regex_iterator)|Construit l’itérateur.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[difference_type](#difference_type)|Type d’une différence d’itérateur.|
|[iterator_category](#iterator_category)|Type de la catégorie d'itérateur.|
|[dirigé](#pointer)|Type d'un pointeur vers une correspondance.|
|[reference](#reference)|Type d’une référence à une correspondance.|
|[regex_type](#regex_type)|Type de l’expression régulière à mettre en correspondance.|
|[value_type](#value_type)|Type d'une correspondance.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! =](#op_neq)|Compare l’inégalité d’itérateurs.|
|[and](#op_star)|Accède à la correspondance désignée.|
|[opérateur + +](#op_add_add)|Incrémente l'itérateur.|
|[opérateur =](#op_eq)|Compare des itérateurs pour déterminer s’ils sont égaux.|
|[>Operator ](#op_arrow)|Accède à la correspondance désignée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<regex>

**Espace de noms :** std

## <a name="examples"></a>Exemples

Consultez les rubriques suivantes pour obtenir des exemples d’expressions régulières :

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

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
match == a
match == a
match == a
```

## <a name="regex_iteratordifference_type"></a><a name="difference_type"></a> regex_iterator ::d ifference_type

Type d’une différence d’itérateur.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `std::ptrdiff_t`.

## <a name="regex_iteratoriterator_category"></a><a name="iterator_category"></a> regex_iterator :: iterator_category

Type de la catégorie d'itérateur.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `std::forward_iterator_tag`.

## <a name="regex_iteratoroperator"></a><a name="op_neq"></a> regex_iterator :: Operator ! =

Compare l’inégalité d’itérateurs.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur auquel comparer.

### <a name="remarks"></a>Notes

La fonction membre retourne `!(*this == right)`.

## <a name="regex_iteratoroperator"></a><a name="op_star"></a> regex_iterator :: Operator *

Accède à la correspondance désignée.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur stockée `match`.

## <a name="regex_iteratoroperator"></a><a name="op_add_add"></a> regex_iterator :: Operator + +

Incrémente l'itérateur.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Notes

Si la correspondance actuelle ne comporte aucun caractère, le premier opérateur appelle `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`. Sinon, il avance la valeur stockée `begin` pour pointer vers le premier caractère situé après la correspondance actuelle, puis appelle `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. Dans chaque cas, si la recherche n’aboutit pas, l’opérateur assigne à l’objet un itérateur de fin de séquence. L’opérateur retourne l’objet.

Le deuxième opérateur effectue une copie de l'objet, incrémente l'objet, puis retourne la copie.

## <a name="regex_iteratoroperator"></a><a name="op_eq"></a> regex_iterator :: Operator =

Compare des itérateurs pour déterminer s’ils sont égaux.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur auquel comparer.

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur true si **`*this`** et *Right* sont des itérateurs de fin de séquence ou si aucun des deux n’est un itérateur de fin de séquence et `begin == right.begin` ,, `end == right.end` `pregex == right.pregex` et `flags == right.flags` . Sinon, elle retourne false.

## <a name="regex_iteratoroperator-gt"></a><a name="op_arrow"></a> regex_iterator :: Operator-&gt;

Accède à la correspondance désignée.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Notes

La fonction membre retourne l’adresse de la valeur stockée `match`.

## <a name="regex_iteratorpointer"></a><a name="pointer"></a> regex_iterator ::p ointer

Type d'un pointeur vers une correspondance.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `match_results<BidIt>*`, où `BidIt` est le paramètre de modèle.

## <a name="regex_iteratorreference"></a><a name="reference"></a> regex_iterator :: référence

Type d’une référence à une correspondance.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `match_results<BidIt>&`, où `BidIt` est le paramètre de modèle.

## <a name="regex_iteratorregex_iterator"></a><a name="regex_iterator"></a> regex_iterator :: regex_iterator

Construit l’itérateur.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
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

Le premier constructeur construit un itérateur de fin de séquence. Le deuxième constructeur initialise la valeur stockée `begin` avec *First*, la valeur stockée `end` avec *Last*, la valeur stockée `pregex` avec `&re` , et la valeur stockée `flags` avec *f*. Il appelle ensuite `regex_search(begin, end, match, *pregex, flags)`. En cas d’échec de la recherche, le constructeur assigne à l’objet un itérateur de fin de séquence.

## <a name="regex_iteratorregex_type"></a><a name="regex_type"></a> regex_iterator :: regex_type

Type de l’expression régulière à mettre en correspondance.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de `basic_regex<Elem, RXtraits>`.

## <a name="regex_iteratorvalue_type"></a><a name="value_type"></a> regex_iterator :: value_type

Type d'une correspondance.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `match_results<BidIt>`, où `BidIt` est le paramètre de modèle.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[Classe regex_constants](../standard-library/regex-constants-class.md)\
[Classe regex_error](../standard-library/regex-error-class.md)\
[\<regex> Mission](../standard-library/regex-functions.md)\
[Classe regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex> Operator](../standard-library/regex-operators.md)\
[Classe regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Classe regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
