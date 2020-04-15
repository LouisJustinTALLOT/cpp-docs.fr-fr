---
title: basic_regex, classe
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 74a8684c619e2cfbd5417950aa6108ad93511bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376748"
---
# <a name="basic_regex-class"></a>basic_regex, classe

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

Le modèle de classe décrit un objet qui tient une expression régulière. Les objets de ce modèle de classe peuvent être transmis aux fonctions de modèle [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search), et [regex_replace](../standard-library/regex-functions.md#regex_replace), avec des arguments appropriés de chaîne de texte, à la recherche de texte qui correspond à l’expression régulière. Il ya deux spécialisations de ce modèle de classe, avec les définitions de type [regex](../standard-library/regex-typedefs.md#regex) pour les éléments de type **char**, et [wregex](../standard-library/regex-typedefs.md#wregex) pour les éléments de type **wchar_t**.

L’argument du modèle *RXtraits* décrit diverses propriétés importantes de la syntaxe des expressions régulières que le modèle de classe prend en charge. Une classe qui spécifie ces traits d’expression réguliers doit avoir la même interface externe qu’un objet de type [regex_traits Classe](../standard-library/regex-traits-class.md).

Certaines fonctions acceptent une séquence d’opérande qui définit une expression régulière. Vous pouvez spécifier cette séquence d'opérande de plusieurs façons :

`ptr`-- une séquence désilisable (comme une chaîne **char**C, pour `ptr` *Elem* de type char ) commençant à (qui `value_type()` ne doit pas être un pointeur nul), où l’élément de terminaison est la valeur et ne fait pas partie de la séquence d’opéra

`ptr`, `count` -- une séquence d'éléments `count` commençant à `ptr` (qui ne doit pas être un pointeur null).

`str` -- la séquence spécifiée par l'objet `basic_string``str`.

`first`, `last` -- une séquence d'éléments délimités par les itérateurs `first` et `last`, dans la plage `[first, last)`.

`right` -- l'objet `basic_regex``right`.

Ces fonctions de membre `flags` prennent également un argument qui spécifie diverses options pour l’interprétation de l’expression régulière en plus de celles décrites par le type *RXtraits.*

### <a name="members"></a>Membres

|Membre|Valeur par défaut|
|-|-|
|const statique public flag_type icase|regex_constants::icase|
|const statique public flag_type nosubs|regex_constants::nosubs|
|const statique public flag_type optimiser|regex_constants::optimiser|
|const statique public flag_type collate|regex_constants::collate|
|cône statique public flag_type ECMAScript|regex_constants::ECMAScript|
|const statique public flag_type de base|regex_constants::basique|
|const statique public flag_type étendu|regex_constants::étendu|
|const statique public flag_type awk|regex_constants::awk|
|const statique public flag_type grep|regex_constants::grep|
|const statique public flag_type egrep|regex_constants::egrep|
|traits privés RXtraits||

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_regex](#basic_regex)|Construit l'objet d'expression régulière.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[flag_type](#flag_type)|Type des indicateurs d’option de syntaxe.|
|[locale_type](#locale_type)|Type de l’objet de paramètres régionaux stocké.|
|[value_type](#value_type)|Type de l’élément.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Attribuer](#assign)|Assigne une valeur à l’objet d’expression régulière.|
|[Drapeaux](#flags)|Retourne des indicateurs d’option de syntaxe.|
|[getloc getloc](#getloc)|Retourne l’objet des paramètres régionaux stockés.|
|[imbue](#imbue)|Modifie l’objet des paramètres régionaux stocké.|
|[mark_count](#mark_count)|Retourne le nombre de sous-expressions en correspondance.|
|[swap](#swap)|Échange deux objets d’expression régulière.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur](#op_eq)|Assigne une valeur à l’objet d’expression régulière.|

## <a name="requirements"></a>Spécifications

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

## <a name="basic_regexassign"></a><a name="assign"></a>basic_regex::assigner

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

*STtraits (STtraits)*\
Classe de caractéristiques pour une source de chaîne.

*STalloc (STalloc)*\
Classe d'allocateurs pour une source de chaîne.

*Init*\
Type d'itérateur d'entrée pour une source de plage.

*Oui*\
Regex source à copier.

*Ptr*\
Pointeur vers le début de la séquence à copier.

*Drapeaux*\
Indicateurs d'option de syntaxe à ajouter lors de la copie.

*len/TD>*\
Longueur de la séquence à copier.

*Str*\
Chaîne à copier.

*Première*\
Début de la séquence à copier.

*Dernière*\
Fin de la séquence à copier.

*Ilist*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Les fonctions membres remplacent chacune l'expression régulière détenue par `*this` par l'expression régulière décrite par la séquence d'opérande, puis retournent `*this`.

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a>basic_regex::basic_regex

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

*STtraits (STtraits)*\
Classe de caractéristiques pour une source de chaîne.

*STalloc (STalloc)*\
Classe d'allocateurs pour une source de chaîne.

*Init*\
Type d'itérateur d'entrée pour une source de plage.

*Oui*\
Regex source à copier.

*Ptr*\
Pointeur vers le début de la séquence à copier.

*Drapeaux*\
Indicateurs d'option de syntaxe à ajouter lors de la copie.

*len/TD>*\
Longueur de la séquence à copier.

*Str*\
Chaîne à copier.

*Première*\
Début de la séquence à copier.

*Dernière*\
Fin de la séquence à copier.

*Ilist*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet construit par défaut de type `RXtraits`.

Le premier constructeur construit un objet `basic_regex` vide. Les autres constructeurs construisent un objet `basic_regex` qui contient l'expression régulière décrite par la séquence d'opérande.

Un `basic_regex` objet vide ne correspond à aucune séquence de caractère lorsqu’il est passé à [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search), ou [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="basic_regexflag_type"></a><a name="flag_type"></a>basic_regex::flag_type

Type des indicateurs d’option de syntaxe.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="basic_regexflags"></a><a name="flags"></a>basic_regex::drapeaux

Retourne des indicateurs d’option de syntaxe.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur de l’argument `flag_type` passé à l’appel le plus récent des fonctions membres [basic_regex::assign](#assign) ou, si aucun appel n’a été effectué, la valeur passée au constructeur.

## <a name="basic_regexgetloc"></a><a name="getloc"></a>basic_regex::getloc

Retourne l’objet des paramètres régionaux stockés.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Notes

La fonction `traits.`membre revient [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="basic_regeximbue"></a><a name="imbue"></a>basic_regex::imbue

Modifie l’objet des paramètres régionaux stocké.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Paramètres

*Loc*\
Objet de paramètres régionaux à stocker.

### <a name="remarks"></a>Notes

La fonction membre `*this` se `traits.`vide et renvoie [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a>basic_regex::locale_type

Type de l’objet de paramètres régionaux stocké.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="basic_regexmark_count"></a><a name="mark_count"></a>basic_regex::mark_count

Retourne le nombre de sous-expressions en correspondance.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre de groupes de capture dans l’expression régulière.

## <a name="basic_regexoperator"></a><a name="op_eq"></a>basic_regex::opérateur

Assigne une valeur à l’objet d’expression régulière.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Paramètres

*STtraits (STtraits)*\
Classe de caractéristiques pour une source de chaîne.

*STalloc (STalloc)*\
Classe d'allocateurs pour une source de chaîne.

*Oui*\
Regex source à copier.

*Str*\
Chaîne à copier.

### <a name="remarks"></a>Notes

Les opérateurs remplacent chacun l’expression régulière détenue par `*this` par l’expression régulière décrite par la séquence d’opérande, puis retournent `*this`.

## <a name="basic_regexswap"></a><a name="swap"></a>basic_regex::swap

Échange deux objets d’expression régulière.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet d’expression régulière à échanger.

### <a name="remarks"></a>Notes

La fonction membre échange les `*this` expressions régulières entre et *à droite*. Elle le fait dans un cadre de temps fixe, et ne lève aucune exception.

## <a name="basic_regexvalue_type"></a><a name="value_type"></a>basic_regex::value_type

Type de l’élément.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Notes

Le type est synonyme du paramètre *elem*.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[Regex](../standard-library/regex-typedefs.md#regex)\
[wregex wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits, classe](../standard-library/regex-traits-class.md)
