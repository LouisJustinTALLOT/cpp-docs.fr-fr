---
title: '&lt;streambuf&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 3c5dbefba8e2106c6e3e678002bce26fffd26a62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215619"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt;, typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

Spécialisation de `basic_streambuf` qui utilise **`char`** comme paramètres de modèle.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **`char`** avec des caractéristiques de caractère par défaut.

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf (

Spécialisation de `basic_streambuf` qui utilise **`wchar_t`** comme paramètres de modèle.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **`wchar_t`** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<streambuf>](../standard-library/streambuf.md)
