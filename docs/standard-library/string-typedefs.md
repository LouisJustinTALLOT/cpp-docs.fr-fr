---
title: '&lt;string&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 950ca5ae34b6469c3d79b7297d4fe7b7644d2fcf
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419496"
---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt;, typedefs

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>  string

Type qui décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md) avec des éléments de type **char**.

Les autres typedefs spécialisés pour `basic_string` sont [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string) et [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Notes

Les lignes de code suivantes sont des déclarations équivalentes :

```cpp
string str("");

basic_string<char> str("");
```

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a>  u16string

Type qui décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md) avec des éléments de type `char16_t`.

Les autres typedefs spécialisés pour `basic_string` sont [wstring](../standard-library/string-typedefs.md#wstring), [string](../standard-library/string-typedefs.md#string) et [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Notes

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>  u32string

Type qui décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md) avec des éléments de type `char32_t`.

Les autres typedefs spécialisés pour `basic_string` sont [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) et [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Notes

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>  wstring

Type qui décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md) avec des éléments de type **wchar_t**.

Les autres typedefs spécialisés pour `basic_string` sont [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) et [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Notes

Les lignes de code suivantes sont des déclarations équivalentes :

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> La taille de **wchar_t** est définie par l’implémentation. Si votre code dépend d' **wchar_t** à une certaine taille, vérifiez l’implémentation de votre plateforme (par exemple, avec `sizeof(wchar_t)`). Si vous avez besoin d’un type de chaîne de caractères dont la largeur reste identique sur toutes les plateformes, utilisez [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) ou [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)
