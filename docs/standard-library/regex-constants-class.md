---
description: 'En savoir plus sur : espace de noms regex_constants'
title: regex_constants, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: d33f9d45023453281714e5585ab6ab33ee1f7857
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250515"
---
# <a name="regex_constants-namespace"></a>regex_constants, espace de noms

Espace de noms des indicateurs d'expression régulière.

## <a name="syntax"></a>Syntaxe

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>Notes

L'espace de noms `regex_constants` inclut plusieurs types d'indicateurs et les valeurs qui leur sont associées.

|Nom|Description|
|-|-|
|[error_type](#error_type)|Indicateurs pour signaler les erreurs de syntaxe des expressions régulières.|
|[match_flag_type](#match_flag_type)|Indicateurs des options de correspondance d’expression régulière.|
|[syntax_option_type](#syntax_option_type)|Indicateurs pour la sélection des options de syntaxe.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<regex>

**Espace de noms :** std

## <a name="regex_constantserror_type"></a><a name="error_type"></a> regex_constants :: error_type

Indicateurs pour signaler les erreurs de syntaxe des expressions régulières.

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>Notes

Le type est un type énuméré qui décrit un objet pouvant stocker des indicateurs d’erreur. Les valeurs distinctes des indicateurs sont :

`error_backref` : l’expression contient une référence arrière non valide

`error_badbrace` : l’expression contient un nombre non valide dans une expression { }

`error_badrepeat` : une expression de répétition (« * », « ? », « + », « { » dans la plupart des contextes) n’est pas précédée d’une expression

`error_brace` : l’expression contient une accolade « { » ou « } » sans correspondance

`error_brack` : l’expression contient un crochet « [ » ou « ] » sans correspondance

`error_collate` : l’expression contient un nom d’élément de classement non valide

`error_complexity` : une tentative de mise en correspondance a échoué, car elle était trop complexe

`error_ctype` : l’expression contient un nom de classe de caractères non valide

`error_escape` : l’expression contient une séquence d’échappement non valide

`error_paren` : l’expression contient une parenthèse « ( » ou « ) » sans correspondance

`error_parse` : l’expression n’a pas pu être analysée

`error_range` : l’expression contient un spécificateur de plage de caractères non valide

`error_space` : l’analyse d’une expression régulière a échoué, car il n’y avait pas suffisamment de ressources disponibles

`error_stack` : une tentative de mise en correspondance a échoué, car il n’y avait pas suffisamment de mémoire disponible

`error_syntax` : échec de l’analyse sur une erreur de syntaxe

`error_backref` : l’expression contient une référence arrière non valide

## <a name="regex_constantsmatch_flag_type"></a><a name="match_flag_type"></a> regex_constants :: match_flag_type

Indicateurs des options de correspondance d’expression régulière.

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>Notes

Le type est un type de masque de bits qui décrit les options à utiliser durant la mise en correspondance d’une séquence de texte par rapport à une expression régulière, ainsi que les indicateurs de format à utiliser durant le remplacement de texte. Vous pouvez combiner des options avec `|`.

Options de correspondance :

`match_default`

`match_not_bol` : ne pas considérer la première position dans la séquence cible comme le début d’une ligne

`match_not_eol` : ne pas considérer la position située après la fin dans la séquence cible comme la fin d’une ligne

`match_not_bow` : ne pas considérer la première position dans la séquence cible comme le début d’un mot

`match_not_eow` : ne pas considérer la position située après la fin dans la séquence cible comme la fin d’un mot

`match_any` : si plusieurs correspondances sont possibles, n’importe quelle correspondance est acceptable

`match_not_null` : ne pas considérer une sous-séquence vide comme une correspondance

`match_continuous` : ne pas rechercher de correspondances ailleurs qu’au début de la séquence cible

`match_prev_avail` -- `--first` est un itérateur valide. Ignorer `match_not_bol` et `match_not_bow` s’ils sont définis

Indicateurs de format :

`format_default` : utiliser les règles de format ECMAScript

`format_sed` : utiliser les règles de format sed

`format_no_copy` : ne pas copier le texte qui ne correspond pas à l’expression régulière

`format_first_only` : ne pas rechercher de correspondances après la première

## <a name="regex_constantssyntax_option_type"></a><a name="syntax_option_type"></a> regex_constants :: syntax_option_type

Indicateurs pour la sélection des options de syntaxe.

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>Notes

Le type est un type de masque de bits qui décrit les spécificateurs de langage et les modificateurs de syntaxe à utiliser durant la compilation d’une expression régulière. Vous pouvez combiner des options avec `|`. Vous devez utiliser un seul spécificateur de langage à la fois.

Spécificateurs de langage :

`ECMAScript` : compiler en ECMAScript

`basic` : compiler en BRE

`extended` : compiler en ERE

`awk` : compiler en awk

`grep` : compiler en grep

`egrep` : compiler en egrep

Modificateurs de syntaxe :

`icase` : les correspondances ne respectent pas la casse

`nosubs` : l’implémentation n’a pas besoin d’assurer le suivi du contenu des groupes de capture

`optimize` : l’implémentation doit privilégier la vitesse de mise en correspondance plutôt que la vitesse de compilation des expressions régulières

`collate` : les correspondances varient selon les paramètres régionaux

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[Classe regex_error](../standard-library/regex-error-class.md)\
[\<regex> Mission](../standard-library/regex-functions.md)\
[Classe regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex> Operator](../standard-library/regex-operators.md)\
[Classe regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Classe regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
