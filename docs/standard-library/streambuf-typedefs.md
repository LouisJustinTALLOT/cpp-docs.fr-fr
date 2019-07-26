---
title: '&lt;streambuf&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 178b489d92a4ed7340084490329fdf8fa16c2aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449586"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt;, typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Spécialisation de `basic_streambuf` qui utilise **char** comme paramètres de modèle.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="wstreambuf"></a>  wstreambuf

Spécialisation de `basic_streambuf` qui utilise **wchar_t** comme paramètres de modèle.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<streambuf>](../standard-library/streambuf.md)
