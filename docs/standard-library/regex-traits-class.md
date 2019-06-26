---
title: Classe regex_traits
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 47e0a1e51809efad2924a2051d1627fe2e9ff95f
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400675"
---
# <a name="regextraits-class"></a>Classe regex_traits

Décrit les caractéristiques des éléments pour la mise en correspondance.

## <a name="syntax"></a>Syntaxe

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Paramètres

*Elem*<br/>
Type d’élément caractère à décrire.

## <a name="remarks"></a>Notes

La classe de modèle décrit différentes caractéristiques d’expression régulière pour le type *Elem*. La classe de modèle [basic_regex, classe](../standard-library/basic-regex-class.md) utilise ces informations pour manipuler les éléments de type *Elem*.

Chaque objet `regex_traits` a un objet de type `regex_traits::locale` qui est utilisé par certaines de ses fonctions membres. Les paramètres régionaux par défaut sont une copie de `regex_traits::locale()`. La fonction membre `imbue` remplace l’objet de paramètres régionaux , et la fonction membre `getloc` retourne une copie de l’objet de paramètres régionaux.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[regex_traits](#regex_traits)|Construit l’objet.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_class_type](#char_class_type)|Type des désignateurs de classes de caractères.|
|[char_type](#char_type)|Type d’un élément.|
|[locale_type](#locale_type)|Type de l’objet de paramètres régionaux stocké.|
|[size_type](#size_type)|Type d'une longueur de séquence.|
|[string_type](#string_type)|Type d'une chaîne d'éléments.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[getloc](#getloc)|Retourne l’objet des paramètres régionaux stockés.|
|[imbue](#imbue)|Modifie l’objet des paramètres régionaux stocké.|
|[isctype](#isctype)|Teste l’appartenance à la classe.|
|[length](#length)|Retourne la longueur d’une séquence se terminant par null.|
|[lookup_classname](#lookup_classname)|Mappe une séquence à une classe de caractères.|
|[lookup_collatename](#lookup_collatename)|Mappe une séquence à un élément de classement.|
|[transform](#transform)|Convertit en séquence ordonnée équivalente.|
|[transform_primary](#transform_primary)|Convertit en séquence ordonnée équivalente ne respectant pas la casse.|
|[translate](#translate)|Convertit en un élément correspondant équivalent.|
|[translate_nocase](#translate_nocase)|Convertit en un élément correspondant équivalent ne respectant pas la casse.|
|[value](#value)|Convertit un élément en valeur numérique.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="example"></a>Exemple

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="char_class_type"></a>  regex_traits::char_class_type

Type des désignateurs de classes de caractères.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour un type non spécifique qui désigne les classes de caractères. Vous pouvez combiner les valeurs de ce type à l’aide de l’opérateur `|` pour désigner les classes de caractères qui représentent l’union des classes désignées par les opérandes.

## <a name="char_type"></a>  regex_traits::char_type

Type d’un élément.

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de l'argument de modèle `Elem`.

## <a name="getloc"></a>  regex_traits::getloc

Retourne l’objet des paramètres régionaux stockés.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne l’objet `locale` stocké.

## <a name="imbue"></a>  regex_traits::imbue

Modifie l’objet des paramètres régionaux stocké.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Paramètres

*loc*<br/>
Objet de paramètres régionaux à stocker.

### <a name="remarks"></a>Notes

La fonction membre copie *loc* à stocké `locale` de l’objet et retourne une copie de la valeur précédente de stocké `locale` objet.

## <a name="isctype"></a>  regex_traits::isctype

Teste l’appartenance à la classe.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Paramètres

*ch*<br/>
Élément à tester.

*cls*<br/>
Classes à tester.

### <a name="remarks"></a>Notes

La fonction membre retourne true uniquement si le caractère *ch* est dans la classe de caractères désignée par *cls*.

## <a name="length"></a>  regex_traits::length

Retourne la longueur d’une séquence se terminant par null.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
La séquence se terminant par null.

### <a name="remarks"></a>Notes

La fonction membre statique retourne `std::char_traits<char_type>::length(str)`.

## <a name="locale_type"></a>  regex_traits::locale_type

Type de l’objet de paramètres régionaux stocké.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme d’un type qui encapsule les paramètres régionaux. Dans les spécialisations `regex_traits<char>` et `regex_traits<wchar_t>`, il s'agit d'un synonyme de `std::locale`.

## <a name="lookup_classname"></a>  regex_traits::lookup_classname

Mappe une séquence à une classe de caractères.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la séquence à rechercher.

*last*<br/>
Fin de la séquence à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne une valeur qui désigne la classe de caractères nommée par la séquence de caractères vers laquelle pointent ses arguments. La valeur ne dépend pas de la casse des caractères dans la séquence.

La spécialisation `regex_traits<char>` reconnaît les noms `"d"`, `"s"`, `"w"`, `"alnum"`, `"alpha"`, `"blank"`, `"cntrl"`, `"digit"`, `"graph"`, `"lower"`, `"print"`, `"punct"`, `"space"`, `"upper"` et `"xdigit"`, tous sans respect de la casse.

La spécialisation `regex_traits<wchar_t>` reconnaît les noms `L"d"`, `L"s"`, `L"w"`, `L"alnum"`, `L"alpha"`, `L"blank"`, `L"cntrl"`, `L"digit"`, `L"graph"`, `L"lower"`, `L"print"`, `L"punct"`, `L"space"`, `L"upper"` et `L"xdigit"`, tous sans respect de la casse.

## <a name="lookup_collatename"></a>  regex_traits::lookup_collatename

Mappe une séquence à un élément de classement.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la séquence à rechercher.

*last*<br/>
Fin de la séquence à rechercher.

### <a name="remarks"></a>Notes

La fonction membre retourne un objet string contenant l’élément de classement correspondant à la séquence `[first, last)`, ou une chaîne vide si la séquence n’est pas un élément de classement valide.

## <a name="regex_traits"></a>  regex_traits::regex_traits

Construit l’objet.

```cpp
regex_traits();
```

### <a name="remarks"></a>Notes

Le constructeur construit un objet dont l'objet `locale` stocké est initialisé avec les paramètres régionaux par défaut.

## <a name="size_type"></a>  regex_traits::size_type

Type d'une longueur de séquence.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme d'un type intégral non signé. Dans les spécialisations `regex_traits<char>` et `regex_traits<wchar_t>`, il s'agit d'un synonyme de `std::size_t`.

Le typedef est un synonyme de `std::size_t`.

## <a name="string_type"></a>  regex_traits::string_type

Type d'une chaîne d'éléments.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de `basic_string<Elem>`.

## <a name="transform"></a>  regex_traits::transform

Convertit en séquence ordonnée équivalente.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la séquence à transformer.

*last*<br/>
Fin de la séquence à transformer.

### <a name="remarks"></a>Notes

La fonction membre retourne une chaîne qu’elle génère à l’aide d’une règle de transformation qui dépend de l’objet `locale` stocké. Pour deux séquences de caractères désignées par les plages d’itérateurs `[first1, last1)` et `[first2, last2)`, `transform(first1, last1) < transform(first2, last2)` si la séquence de caractères désignée par la plage d’itérateurs `[first1, last1)` est triée avant la séquence de caractères désignée par la plage d’itérateurs `[first2, last2)`.

## <a name="transform_primary"></a>  regex_traits::transform_primary

Convertit en séquence ordonnée équivalente ne respectant pas la casse.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Paramètres

*first*<br/>
Début de la séquence à transformer.

*last*<br/>
Fin de la séquence à transformer.

### <a name="remarks"></a>Notes

La fonction membre retourne une chaîne qu’elle génère à l’aide d’une règle de transformation qui dépend de l’objet `locale` stocké. Pour deux séquences de caractères désignées par les plages d’itérateurs `[first1, last1)` et `[first2, last2)`, `transform_primary(first1, last1) < transform_primary(first2, last2)` si la séquence de caractères désignée par la plage d’itérateurs `[first1, last1)` est triée avant la séquence de caractères désignée par la plage d’itérateurs `[first2, last2)` indépendamment de la casse ou des accents.

## <a name="translate"></a>  regex_traits::translate

Convertit en un élément correspondant équivalent.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Paramètres

*ch*<br/>
Élément à convertir.

### <a name="remarks"></a>Notes

La fonction membre retourne un caractère qu’elle génère à l’aide d’une règle de transformation qui dépend de l’objet `locale` stocké. Pour deux objets `char_type` `ch1` et `ch2`, `translate(ch1) == translate(ch2)` seulement si `ch1` et `ch2` doivent correspondre quand un des objets est présent dans la définition de l’expression régulière et que l’autre se trouve à la position correspondante dans la séquence cible pour une correspondance respectant les paramètres régionaux.

## <a name="translate_nocase"></a>  regex_traits::translate_nocase

Convertit en un élément correspondant équivalent ne respectant pas la casse.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Paramètres

*ch*<br/>
Élément à convertir.

### <a name="remarks"></a>Notes

La fonction membre retourne un caractère qu’elle génère à l’aide d’une règle de transformation qui dépend de l’objet `locale` stocké. Pour deux objets `char_type` `ch1` et `ch2`, `translate_nocase(ch1) == translate_nocase(ch2)` seulement si `ch1` et `ch2` doivent correspondre quand un des objets est présent dans la définition de l’expression régulière et que l’autre se trouve à la position correspondante dans la séquence cible pour une correspondance ne respectant pas la casse.

## <a name="value"></a>  regex_traits::value

Convertit un élément en valeur numérique.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Paramètres

*ch*<br/>
Élément à convertir.

*radix*<br/>
Base arithmétique à utiliser.

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur représentée par le caractère *ch* dans la base de *radix*, ou -1 si *ch* n’est pas un chiffre valide dans la base de *radix*. La fonction sera uniquement appelée avec un *radix* argument 8, 10 ou 16.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, classe](../standard-library/regex-constants-class.md)<br/>
[regex_error, classe](../standard-library/regex-error-class.md)<br/>
[\<regex>, fonctions](../standard-library/regex-functions.md)<br/>
[regex_iterator, classe](../standard-library/regex-iterator-class.md)<br/>
[\<regex>, opérateurs](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, classe](../standard-library/regex-token-iterator-class.md)<br/>
[\<regex>, typedefs](../standard-library/regex-typedefs.md)<br/>
[regex_traits\<char > classe](../standard-library/regex-traits-char-class.md)<br/>
[regex_traits\<wchar_t>, classe](../standard-library/regex-traits-wchar-t-class.md)<br/>
