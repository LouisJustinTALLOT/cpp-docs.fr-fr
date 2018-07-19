---
title: basic_regex, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::basic_regex
dev_langs:
- C++
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f13dfb45073a1a21e8d6a7b4585f0dfc5c71b8e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959746"
---
# <a name="basicregex-class"></a>basic_regex, classe

Encapsule une expression régulière.

## <a name="syntax"></a>Syntaxe

```cpp
class basic_regex {
   public:
   basic_regex();
   explicit basic_regex(const Elem *ptr,
   flag_type flags = ECMAScript);
   basic_regex(const Elem *ptr, size_type len,
   flag_type flags = ECMAScript);
   basic_regex(const basic_regex& right);
   template <class STtraits, class STalloc>
   explicit basic_regex(const basic_string<Elem, STtraits, STalloc>& str,
   flag_type flags = ECMAScript);
   template <class InIt>
   explicit basic_regex(InIt first, InIt last,
   flag_type flags = ECMAScript);
   basic_regex& operator=(const basic_regex& right);
   basic_regex& operator=(const Elem *ptr);
   template <class STtraits, class STalloc>
   basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
   basic_regex& assign(const basic_regex& right);
   basic_regex& assign(const Elem *ptr,
   flag_type flags = ECMAScript);
   basic_regex& assign(const Elem *ptr, size_type len,
   flag_type flags = ECMAScript);
   template <class STtraits, class STalloc>
   basic_regex& assign(const basic_string<Elem, STtraits, STalloc>& str,
   flag_type flags = ECMAScript);
   template <class InIt>
   basic_regex& assign(InIt first, InIt last,
   flag_type flags = ECMAScript);
   locale_type imbue(locale_type loc);
   locale_type getloc() const;
   void swap(basic_regex& other) throw();
   unsigned mark_count() const;
   flag_type flags() const;
   typedef Elem value_type;
   typedef regex_constants::syntax_option_type flag_type;
   typedef typename RXtraits::locale_type locale_type;
   static const flag_type icase = regex_constants::icase;
   static const flag_type nosubs = regex_constants::nosubs;
   static const flag_type optimize = regex_constants::optimize;
   static const flag_type collate = regex_constants::collate;
   static const flag_type ECMAScript = regex_constants::ECMAScript;
   static const flag_type basic = regex_constants::basic;
   static const flag_type extended = regex_constants::extended;
   static const flag_type awk = regex_constants::awk;
   static const flag_type grep = regex_constants::grep;
   static const flag_type egrep = regex_constants::egrep;
   private:
   RXtraits traits;    // exposition only
   };
   ```

### <a name="parameters"></a>Paramètres

*Elem* le type des éléments à faire correspondre.

*RXtraits* classe Traits des éléments.

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet qui contient une expression régulière. Objets de cette classe de modèle peuvent être passés aux fonctions de modèle [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search), et [regex_replace](../standard-library/regex-functions.md#regex_replace), avec les arguments de chaîne de texte appropriés, Pour rechercher du texte qui correspond à l’expression régulière. Il existe deux spécialisations de cette classe de modèle, avec les définitions de type [regex](../standard-library/regex-typedefs.md#regex) pour les éléments de type **char**, et [wregex](../standard-library/regex-typedefs.md#wregex) pour les éléments de type  **wchar_t**.

L’argument de modèle *RXtraits* décrit plusieurs propriétés importantes de la syntaxe des expressions régulières qui prend en charge de la classe de modèle. Une classe qui spécifie ces caractéristiques d’expression régulière doit avoir la même interface externe qu’un objet de la classe de modèle [regex_traits](../standard-library/regex-traits-class.md).

Certaines fonctions acceptent une séquence d’opérande qui définit une expression régulière. Vous pouvez spécifier cette séquence d'opérande de plusieurs façons :

`ptr` --une séquence se terminant par null (comme une chaîne C, pour *Elem* de type **char**) commençant à `ptr` (qui doit être pas un pointeur null), où l’élément de fin est la valeur `value_type()` et ne fait pas partie de la séquence d’opérande

`ptr`, `count` -- une séquence d'éléments `count` commençant à `ptr` (qui ne doit pas être un pointeur null).

`str` -- la séquence spécifiée par l'objet `basic_string` `str`.

`first`, `last` -- une séquence d'éléments délimités par les itérateurs `first` et `last`, dans la plage `[first, last)`.

`right` -- l'objet `basic_regex` `right`.

Ces fonctions membres acceptent également un argument `flags` qui spécifie différentes options pour l’interprétation de l’expression régulière en plus de celles décrites par le *RXtraits* type.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="assign"></a>  basic_regex::assign

Assigne une valeur à l'objet d'expression régulière.

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

*STtraits* classe de Traits pour une source de chaîne.

*STalloc* classe Allocator pour une source de chaîne.

*InIt* type d’itérateur pour une source de la plage d’entrée.

*droit* Regex source à copier.

*PTR* pointeur au début de la séquence à copier.

*indicateurs* indicateurs d’option de syntaxe à ajouter lors de la copie.

*Len/TD >* longueur de la séquence à copier.

*Str* chaîne à copier.

*première* début de la séquence à copier.

*dernière* fin de séquence à copier.

*IList* initializer_list à copier.

### <a name="remarks"></a>Notes

Les fonctions membres remplacent chacune l'expression régulière détenue par `*this` par l'expression régulière décrite par la séquence d'opérande, puis retournent `*this`.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_assign.cpp
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
match("abc", "") == falsematch("abc", "abcd") == falsematch("abc", "abc") == truematch("abc", "abc") == truematch(string("abcd"), "abc") == falsematch(string("abc"), "abc") == true"abc" mark_count == 0"(abc)" mark_count == 1getloc == imbued == truematch("abc") == true
```

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

*STtraits* classe de Traits pour une source de chaîne.

*STalloc* classe Allocator pour une source de chaîne.

*InIt* type d’itérateur pour une source de la plage d’entrée.

*droit* Regex source à copier.

*PTR* pointeur au début de la séquence à copier.

*indicateurs* indicateurs d’option de syntaxe à ajouter lors de la copie.

*Len/TD >* longueur de la séquence à copier.

*Str* chaîne à copier.

*première* début de la séquence à copier.

*dernière* fin de séquence à copier.

*IList* initializer_list à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet construit par défaut de type `RXtraits`.

Le premier constructeur construit un objet `basic_regex` vide. Les autres constructeurs construisent un objet `basic_regex` qui contient l'expression régulière décrite par la séquence d'opérande.

Vide `basic_regex` objet ne correspond pas à n’importe quelle séquence de caractères quand il est passé à [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search), ou [regex_replace](../standard-library/regex-functions.md#regex_replace).

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_construct.cpp
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
    regex rx6{ { 'a', 'b', 'c' } };
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}

```

```Output
match("abc", "") == falsematch("abc", "abcd") == falsematch("abc", "abc") == truematch("abc", "abc") == truematch(string("abcd"), "abc") == falsematch(string("abc"), "abc") == true"abc" mark_count == 0"(abc)" mark_count == 1getloc == imbued == truematch("abc", "abc") == true
```

## <a name="flag_type"></a>  basic_regex::flag_type

Type des indicateurs d’option de syntaxe.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_flag_type.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="flags"></a>  basic_regex::flags

Retourne des indicateurs d’option de syntaxe.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur de l’argument `flag_type` passé à l’appel le plus récent des fonctions membres [basic_regex::assign](#assign) ou, si aucun appel n’a été effectué, la valeur passée au constructeur.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_flags.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="getloc"></a>  basic_regex::getloc

Retourne l’objet des paramètres régionaux stockés.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_getloc.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="imbue"></a>  basic_regex::imbue

Modifie l’objet des paramètres régionaux stocké.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Paramètres

*loc* l’objet de paramètres régionaux à stocker.

### <a name="remarks"></a>Notes

La fonction membre vide `*this` et retourne `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_imbue.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="locale_type"></a>  basic_regex::locale_type

Type de l’objet de paramètres régionaux stocké.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_locale_type.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="mark_count"></a>  basic_regex::mark_count

Retourne le nombre de sous-expressions en correspondance.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre de groupes de capture dans l’expression régulière.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_mark_count.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="op_eq"></a>  basic_regex::operator=

Assigne une valeur à l’objet d’expression régulière.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Paramètres

*STtraits* classe de Traits pour une source de chaîne.

*STalloc* classe Allocator pour une source de chaîne.

*droit* Regex source à copier.

*Str* chaîne à copier.

### <a name="remarks"></a>Notes

Les opérateurs remplacent chacun l’expression régulière détenue par `*this` par l’expression régulière décrite par la séquence d’opérande, puis retournent `*this`.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_operator_as.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="swap"></a>  basic_regex::swap

Échange deux objets d’expression régulière.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Paramètres

*droit* l’objet d’expression régulière à échanger.

### <a name="remarks"></a>Notes

La fonction membre échange les expressions régulières entre `*this` et *droit*. Elle le fait dans un cadre de temps fixe, et ne lève aucune exception.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="value_type"></a>  basic_regex::value_type

Type de l’élément.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *Elem*.

### <a name="example"></a>Exemple

```cpp
// std__regex__basic_regex_value_type.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
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
```

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)<br/>
[regex_match](../standard-library/regex-functions.md#regex_match)<br/>
[regex_search](../standard-library/regex-functions.md#regex_search)<br/>
[regex_replace](../standard-library/regex-functions.md#regex_replace)<br/>
[regex](../standard-library/regex-typedefs.md#regex)<br/>
[wregex](../standard-library/regex-typedefs.md#wregex)<br/>
[regex_traits, classe](../standard-library/regex-traits-class.md)<br/>
