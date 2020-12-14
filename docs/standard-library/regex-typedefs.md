---
description: 'En savoir plus sur : les &lt; &gt; typedefs Regex'
title: '&lt;regex&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 7814bd32e167d66c63c5ebf67221f461bc438c1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243794"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt;, typedefs

[cmatch](#cmatch)\
[cregex_iterator](#cregex_iterator)\
[cregex_token_iterator](#cregex_token_iterator)\
[csub_match](#csub_match)\
[Regex](#regex)\
[Smatch](#smatch)\
[sregex_iterator](#sregex_iterator)\
[sregex_token_iterator](#sregex_token_iterator)\
[ssub_match](#ssub_match)\
[wcmatch](#wcmatch)\
[wcregex_iterator](#wcregex_iterator)\
[wcregex_token_iterator](#wcregex_token_iterator)\
[wcsub_match](#wcsub_match)\
[wregex](#wregex)\
[wsmatch](#wsmatch)\
[wsregex_iterator](#wsregex_iterator)\
[wsregex_token_iterator](#wsregex_token_iterator)\
[wssub_match](#wssub_match)

## <a name="cmatch-typedef"></a><a name="cmatch"></a> cmatch (typedef)

Définition de type pour char match_results.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Match_results classe](../standard-library/match-results-class.md) pour les itérateurs de type `const char*` .

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a> cregex_iterator typedef

Définition de type pour char regex_iterator.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_iterator classe](../standard-library/regex-iterator-class.md) pour les itérateurs de type `const char*` .

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a> cregex_token_iterator typedef

Définition de type pour char regex_token_iterator

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_token_iterator classe](../standard-library/regex-token-iterator-class.md) pour les itérateurs de type `const char*` .

## <a name="csub_match-typedef"></a><a name="csub_match"></a> csub_match typedef

Définition de type pour char sub_match.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Sub_match classe](../standard-library/sub-match-class.md) pour les itérateurs de type `const char*` .

## <a name="regex-typedef"></a><a name="regex"></a> Regex (typedef)

Définition de type pour char basic_regex.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Basic_regex classe](../standard-library/basic-regex-class.md) pour les éléments de type **`char`** .

> [!NOTE]
> L’utilisation de caractères étendus a des résultats imprévisibles avec `regex`. Les valeurs en dehors de la plage 0 à 127 peuvent entraîner un comportement non défini.

## <a name="smatch-typedef"></a><a name="smatch"></a> Smatch (typedef)

Définition de type pour string match_results.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Match_results classe](../standard-library/match-results-class.md) pour les itérateurs de type `string::const_iterator` .

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a> sregex_iterator typedef

Définition du type pour string regex_iterator.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_iterator classe](../standard-library/regex-iterator-class.md) pour les itérateurs de type `string::const_iterator` .

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a> sregex_token_iterator typedef

Définition de type pour string regex_token_iterator.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_token_iterator classe](../standard-library/regex-token-iterator-class.md) pour les itérateurs de type `string::const_iterator` .

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a> ssub_match typedef

Définition de type pour string sub_match.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Sub_match classe](../standard-library/sub-match-class.md) pour les itérateurs de type `string::const_iterator` .

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a> wcmatch (typedef)

Définition de type pour wchar_t match_results.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Match_results classe](../standard-library/match-results-class.md) pour les itérateurs de type `const wchar_t*` .

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a> wcregex_iterator typedef

Définition de type pour wchar_t regex_iterator.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_iterator classe](../standard-library/regex-iterator-class.md) pour les itérateurs de type `const wchar_t*` .

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a> wcregex_token_iterator typedef

Définition de type pour wchar_t regex_token_iterator.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_token_iterator classe](../standard-library/regex-token-iterator-class.md) pour les itérateurs de type `const wchar_t*` .

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a> wcsub_match typedef

Définition de type pour wchar_t sub_match.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Sub_match classe](../standard-library/sub-match-class.md) pour les itérateurs de type `const wchar_t*` .

## <a name="wregex-typedef"></a><a name="wregex"></a> wregex (typedef)

Définition de type pour wchar_t basic_regex.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Basic_regex classe](../standard-library/basic-regex-class.md) pour les éléments de type **`wchar_t`** .

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a> wsmatch (typedef)

Définition de type pour wstring match_results.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Match_results classe](../standard-library/match-results-class.md) pour les itérateurs de type `wstring::const_iterator` .

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a> wsregex_iterator typedef

Définition de type pour wstring regex_iterator.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_iterator classe](../standard-library/regex-iterator-class.md) pour les itérateurs de type `wstring::const_iterator` .

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a> wsregex_token_iterator typedef

Définition de type pour wstring regex_token_iterator.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Regex_token_iterator classe](../standard-library/regex-token-iterator-class.md) pour les itérateurs de type `wstring::const_iterator` .

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a> wssub_match typedef

Définition de type pour wstring sub_match.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [Sub_match classe](../standard-library/sub-match-class.md) pour les itérateurs de type `wstring::const_iterator` .

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[Classe regex_constants](../standard-library/regex-constants-class.md)\
[Classe regex_error](../standard-library/regex-error-class.md)\
[\<regex> Mission](../standard-library/regex-functions.md)\
[Classe regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex> Operator](../standard-library/regex-operators.md)\
[Classe regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Classe regex_traits](../standard-library/regex-traits-class.md)
