---
title: basic_regex, classe
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 8df9e927c430f3b94f5857bf18f575e79d6b922a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453435"
---
# <a name="basicregex-class"></a>basic_regex, classe

Encapsule une expression régulière.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Paramètres

*Elem*\
Type des éléments à faire correspondre.

*RXtraits*\
Classe Traits des éléments.

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet qui contient une expression régulière. Les objets de cette classe de modèle peuvent être passés aux fonctions de modèle [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)et [regex_replace](../standard-library/regex-functions.md#regex_replace), ainsi que des arguments de chaîne de texte appropriés, afin de rechercher le texte correspondant à l’expression régulière. Il existe deux spécialisations de cette classe de modèle, avec les définitions de type [Regex](../standard-library/regex-typedefs.md#regex) pour les éléments de type **char**et [wregex](../standard-library/regex-typedefs.md#wregex) pour les éléments de type **wchar_t**.

L’argument de modèle *RXtraits* décrit diverses propriétés importantes de la syntaxe des expressions régulières prises en charge par la classe de modèle. Une classe qui spécifie ces caractéristiques d’expression régulière doit avoir la même interface externe qu’un objet de la classe de modèle [regex_traits](../standard-library/regex-traits-class.md).

Certaines fonctions acceptent une séquence d’opérande qui définit une expression régulière. Vous pouvez spécifier cette séquence d'opérande de plusieurs façons :

`ptr`--une séquence se terminant par un **caractère**null (telle qu’une chaîne C, pour *elem* de type char `ptr` ) à partir de (qui ne doit pas être un pointeur null), où l’élément `value_type()` de fin est la valeur et ne fait pas partie de la séquence d’opérande

`ptr`, `count` -- une séquence d'éléments `count` commençant à `ptr` (qui ne doit pas être un pointeur null).

`str` -- la séquence spécifiée par l'objet `basic_string` `str`.

`first`, `last` -- une séquence d'éléments délimités par les itérateurs `first` et `last`, dans la plage `[first, last)`.

`right` -- l'objet `basic_regex` `right`.

Ces fonctions membres acceptent également un argument `flags` qui spécifie différentes options pour l’interprétation de l’expression régulière, en plus de celles décrites par le type *RXtraits* .

### <a name="members"></a>Membres

|Membre|Valeur par défaut|
|-|-|
|public static const flag_type iCase|regex_constants::icase|
|public static const flag_type NoSubs|regex_constants::nosubs|
|public static const flag_type optimiser|regex_constants:: Optimize|
|COLLATE static static const flag_type COLLATE|regex_constants::collate|
|public static const flag_type ECMAScript|regex_constants:: ECMAScript|
|public static const flag_type de base|regex_constants:: Basic|
|public static const flag_type étendu|regex_constants:: Extended|
|public static const flag_type awk|regex_constants::awk|
|static static const flag_type grep|regex_constants::grep|
|public static const flag_type egrep|regex_constants::egrep|
|caractéristiques RXtraits privées||

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_regex](#basic_regex)|Construit l'objet d'expression régulière.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[flag_type](#flag_type)|Type des indicateurs d’option de syntaxe.|
|[locale_type](#locale_type)|Type de l’objet de paramètres régionaux stocké.|
|[value_type](#value_type)|Type de l’élément.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[assign](#assign)|Assigne une valeur à l’objet d’expression régulière.|
|[flags](#flags)|Retourne des indicateurs d’option de syntaxe.|
|[getloc](#getloc)|Retourne l’objet des paramètres régionaux stockés.|
|[imbue](#imbue)|Modifie l’objet des paramètres régionaux stocké.|
|[mark_count](#mark_count)|Retourne le nombre de sous-expressions en correspondance.|
|[swap](#swap)|Échange deux objets d’expression régulière.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Assigne une valeur à l’objet d’expression régulière.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="assign"></a>  basic_regex::assign

Assigne une valeur à l’objet d’expression régulière.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>Paramètres

*STtraits*\
Classe de caractéristiques pour une source de chaîne.

*STalloc*\
Classe d'allocateurs pour une source de chaîne.

*Rein*\
Type d'itérateur d'entrée pour une source de plage.

*Oui*\
Regex source à copier.

*effectués*\
Pointeur vers le début de la séquence à copier.

*père*\
Indicateurs d'option de syntaxe à ajouter lors de la copie.

*Len/TD >* \
Longueur de la séquence à copier.

*Str*\
Chaîne à copier.

*premier*\
Début de la séquence à copier.

*famille*\
Fin de la séquence à copier.

*IList*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Les fonctions membres remplacent chacune l'expression régulière détenue par `*this` par l'expression régulière décrite par la séquence d'opérande, puis retournent `*this`.

## <a name="basic_regex"></a>  basic_regex::basic_regex

Construit l'objet d'expression régulière.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>Paramètres

*STtraits*\
Classe de caractéristiques pour une source de chaîne.

*STalloc*\
Classe d'allocateurs pour une source de chaîne.

*Rein*\
Type d'itérateur d'entrée pour une source de plage.

*Oui*\
Regex source à copier.

*effectués*\
Pointeur vers le début de la séquence à copier.

*père*\
Indicateurs d'option de syntaxe à ajouter lors de la copie.

*Len/TD >* \
Longueur de la séquence à copier.

*Str*\
Chaîne à copier.

*premier*\
Début de la séquence à copier.

*famille*\
Fin de la séquence à copier.

*IList*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet construit par défaut de type `RXtraits`.

Le premier constructeur construit un objet `basic_regex` vide. Les autres constructeurs construisent un objet `basic_regex` qui contient l'expression régulière décrite par la séquence d'opérande.

Un objet `basic_regex` vide ne correspond à aucune séquence de caractères lorsqu’il est passé à [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)ou [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="flag_type"></a>  basic_regex::flag_type

Type des indicateurs d’option de syntaxe.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="flags"></a>  basic_regex::flags

Retourne des indicateurs d’option de syntaxe.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur de l’argument `flag_type` passé à l’appel le plus récent des fonctions membres [basic_regex::assign](#assign) ou, si aucun appel n’a été effectué, la valeur passée au constructeur.

## <a name="getloc"></a>  basic_regex::getloc

Retourne l’objet des paramètres régionaux stockés.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="imbue"></a>  basic_regex::imbue

Modifie l’objet des paramètres régionaux stocké.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Paramètres

*Loc*\
Objet de paramètres régionaux à stocker.

### <a name="remarks"></a>Notes

La fonction membre vide `*this` et retourne `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="locale_type"></a>  basic_regex::locale_type

Type de l’objet de paramètres régionaux stocké.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="mark_count"></a>  basic_regex::mark_count

Retourne le nombre de sous-expressions en correspondance.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre de groupes de capture dans l’expression régulière.

## <a name="op_eq"></a>  basic_regex::operator=

Assigne une valeur à l’objet d’expression régulière.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Paramètres

*STtraits*\
Classe de caractéristiques pour une source de chaîne.

*STalloc*\
Classe d'allocateurs pour une source de chaîne.

*Oui*\
Regex source à copier.

*Str*\
Chaîne à copier.

### <a name="remarks"></a>Notes

Les opérateurs remplacent chacun l’expression régulière détenue par `*this` par l’expression régulière décrite par la séquence d’opérande, puis retournent `*this`.

## <a name="swap"></a>  basic_regex::swap

Échange deux objets d’expression régulière.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet d’expression régulière à échanger.

### <a name="remarks"></a>Notes

La fonction membre échange les expressions régulières entre `*this` et *Right*. Elle le fait dans un cadre de temps fixe, et ne lève aucune exception.

## <a name="value_type"></a>  basic_regex::value_type

Type de l’élément.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *elem*.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits, classe](../standard-library/regex-traits-class.md)
