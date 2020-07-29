---
title: '&lt;string_view &gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 6aadd4ad3ff08a0b020fd8e683e60063fe516c63
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215593"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view &gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

Type qui décrit une spécialisation du modèle de classe [basic_string_view](../standard-library/basic-string-view-class.md) avec des éléments de type **`char`** .

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Notes

Les lignes de code suivantes sont des déclarations équivalentes :

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a><a name="u16string_view"></a>u16string_view

Type qui décrit une spécialisation du modèle de classe [basic_string_view](../standard-library/basic-string-view-class.md) avec des éléments de type **`char16_t`** .

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Notes

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

Type qui décrit une spécialisation du modèle de classe [basic_string_view](../standard-library/basic-string-view-class.md) avec des éléments de type **`char32_t`** .

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Notes

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

Type qui décrit une spécialisation du modèle de classe [basic_string_view](../standard-library/basic-string-view-class.md) avec des éléments de type **`wchar_t`** .

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Notes

Les lignes de code suivantes sont des déclarations équivalentes :

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Pour obtenir la liste des constructeurs de chaînes, consultez [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> La taille de **`wchar_t`** est de deux octets sur Windows, mais ce n’est pas nécessairement le cas pour toutes les plateformes. Si vous avez besoin d’un string_view type à caractères larges dont la largeur est garantie pour rester identique sur toutes les plateformes, utilisez [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) ou [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Voir aussi

[\<string_view>](../standard-library/string-view.md)
