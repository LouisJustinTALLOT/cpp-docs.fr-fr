---
title: '&lt;regex&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 06/19/2018
ms.topic: reference
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
dev_langs:
- C++
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: 9a417cc9738aec739bdeaec58cc5d50476c9c753
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107494"
---
# <a name="ltregexgt-functions"></a>&lt;regex&gt;, fonctions

|||
|-|-|
|[regex_match](#regex_match)|Teste si une expression régulière correspond à l'intégralité de la chaîne cible.|
|[regex_replace](#regex_replace)|Remplace des expressions régulières mises en correspondance.|
|[regex_search](#regex_search)|Recherche une correspondance d'expression régulière.|
|[swap](#swap)|Échange deux `basic_regex` ou `match_results` objets.|

## <a name="regex_match"></a>  regex_match

Teste si une expression régulière correspond à l'intégralité de la chaîne cible.

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);


// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);


// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);


// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);


// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Paramètres

*BidIt*<br/> Type d'itérateur pour les sous-correspondances. Pour les cas courants de `string::const_iterator`, `wstring::const_iterator`, `const char*` ou `const wchar_t*`.

*Alloc*<br/>
Classe d'allocateur des résultats de correspondances.

*Elem*<br/>
Type des éléments à faire correspondre. Pour les cas courants, il est `string`, `wstring`, `char*` ou `wchar_t*`.

*RXtraits*<br/>
Classe Traits des éléments.

*Alloc2*<br/>
Classe d'allocateur d'expressions régulières.

*IOtraits*<br/>
Classe de caractéristiques des chaînes.

*IOalloc*<br/>
Classe d'allocateur de chaînes.

*flags*<br/>
Indicateurs pour les correspondances.

*first*<br/>
Début de la séquence à mettre en correspondance.

*last*<br/>
Fin de la séquence à mettre en correspondance.

*match*<br/>
Résultats de correspondances. Correspond au type Elem : [smatch](../standard-library/regex-typedefs.md#smatch) pour `string`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) pour `wstring`, [cmatch](../standard-library/regex-typedefs.md#cmatch) pour `char*` ou [wcmatch](../standard-library/regex-typedefs.md#wcmatch) pour `wchar_t*`.

*ptr*<br/>
Pointeur vers le début de la séquence à mettre en correspondance. Si *ptr* est `char*`, puis utilisez `cmatch` et `regex`. Si *ptr* est `wchar_t*` ensuite utiliser `wcmatch` et `wregex`.

*RE*<br/>
Expression régulière à mettre en correspondance. Type `regex` pour `string` et `char*`, ou `wregex` pour `wstring` et `wchar_t*`.

*str*<br/>
Chaîne à mettre en correspondance. Correspond au type de *Elem*.

### <a name="remarks"></a>Notes

Chaque fonction de modèle retourne true uniquement si la séquence de l’intégralité de l’opérande *str* correspond exactement à l’argument d’expression régulière *re*. Utilisez [regex_search](../standard-library/regex-functions.md#regex_search) à mettre en correspondance une sous-chaîne au sein d’une séquence cible et `regex_iterator` pour rechercher plusieurs correspondances. Les fonctions qui acceptent un objet `match_results` définissent ses membres pour refléter si la correspondance a abouti et, si tel est le cas, ce que les différents groupes de capture dans l'expression régulière ont capturé.

Les fonctions qui acceptent un objet `match_results` définissent ses membres pour refléter si la correspondance a abouti et, si tel est le cas, ce que les différents groupes de capture dans l'expression régulière ont capturé.

### <a name="example"></a>Exemple

```cpp
#include "stdafx.h"
#include <regex>
#include <iostream>

using namespace std;

int _tmain(int argc, _TCHAR* argv[])
{

    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);

    // (1) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (2) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal
    found = regex_match(target2.cbegin(), target2.cend(), rx2);

    // (3) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

## <a name="regex_replace"></a>  regex_replace

Remplace des expressions régulières mises en correspondance.

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Paramètres

*Outlt*<br/>
Type d’itérateur pour les remplacements.

*BidIt*<br/>
Type d'itérateur pour les sous-correspondances.

*RXtraits*<br/>
Classe Traits des éléments.

*Alloc*<br/>
Classe d'allocateur d'expressions régulières.

*Elem*<br/>
Type des éléments à faire correspondre.

*flags*<br/>
Indicateurs pour les correspondances.

*first*<br/>
Début de la séquence à mettre en correspondance.

*FMT*<br/>
Format des remplacements.

*last*<br/>
Fin de la séquence à mettre en correspondance.

*out*<br/>
Itérateur de sortie.

*RE*<br/>
Expression régulière à mettre en correspondance.

*str*<br/>
Chaîne à mettre en correspondance.

### <a name="remarks"></a>Notes

La première fonction construit un [regex_iterator, classe](../standard-library/regex-iterator-class.md) objet `iter(first, last, re, flags)` et l’utilise pour fractionner la plage d’entrée `[first, last)` en une série de sous-séquences `T0 M0 T1 M1...TN-1 MN-1 TN`, où `Mn` est la correspondance nième détectée par le itérateur. Si aucune correspondance n’est trouvée, `T0` correspond à la plage d’entrée entière et `N` est égal à zéro. Si `(flags & format_first_only) != 0`, seule la première correspondance est utilisée, `T1` correspond à tout le texte entré qui suit la correspondance et `N` a la valeur 1. Pour chaque `i` dans la plage `[0, N)`si `(flags & format_no_copy) == 0` elle copie le texte dans la plage `Ti` à l’itérateur *out*. Elle appelle ensuite `m.format(out, fmt, flags)`, où `m` est l’objet `match_results` retourné par l’objet itérateur `iter` pour la sous-séquence `Mi`. Enfin, si `(flags & format_no_copy) == 0` elle copie le texte dans la plage `TN` à l’itérateur *out*. La fonction retourne *out*.

La deuxième fonction construit une variable locale `result` de type `basic_string<charT>`, puis appelle `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`. Elle retourne `result`.

### <a name="example"></a>Exemple

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a>  regex_search

Recherche une correspondance d'expression régulière.

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Paramètres

*BidIt*<br/>
Type d'itérateur pour les sous-correspondances.

*Alloc*<br/>
Classe d'allocateur des résultats de correspondances.

*Elem*<br/>
Type des éléments à faire correspondre.

*RXtraits*<br/>
Classe Traits des éléments.

*Alloc2*<br/>
Classe d'allocateur d'expressions régulières.

*IOtraits*<br/>
Classe de caractéristiques des chaînes.

*IOalloc*<br/>
Classe d'allocateur de chaînes.

*flags*<br/>
Indicateurs pour les correspondances.

*first*<br/>
Début de la séquence à mettre en correspondance.

*last*<br/>
Fin de la séquence à mettre en correspondance.

*match*<br/>
Résultats de correspondances.

*ptr*<br/>
Pointeur vers le début de la séquence à mettre en correspondance.

*RE*<br/>
Expression régulière à mettre en correspondance.

*str*<br/>
Chaîne à mettre en correspondance.

### <a name="remarks"></a>Notes

Chaque fonction de modèle retourne true uniquement si une recherche de son argument d’expression régulière *re* dans son opérande séquence réussit. Les fonctions qui acceptent un objet `match_results` définissent ses membres pour indiquer si la recherche a réussi et, le cas échéant, ce que les différents groupes de capture dans l’expression régulière ont capturé.

### <a name="example"></a>Exemple

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a>  swap

Échange deux `basic_regex` ou `match_results` objets.

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Elem*<br/>
Type des éléments à faire correspondre.

*RXtraits*<br/>
Classe Traits des éléments.

### <a name="remarks"></a>Notes

Les fonctions de modèle échangent le contenu de leurs arguments respectifs en temps constant et ne lèvent pas d’exceptions.

### <a name="example"></a>Exemple

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, classe](../standard-library/regex-constants-class.md)<br/>
[regex_error, classe](../standard-library/regex-error-class.md)<br/>
[regex_iterator, classe](../standard-library/regex-iterator-class.md)<br/>
[\<regex>, opérateurs](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, classe](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, classe](../standard-library/regex-traits-class.md)<br/>
[\<regex>, typedefs](../standard-library/regex-typedefs.md)<br/>
