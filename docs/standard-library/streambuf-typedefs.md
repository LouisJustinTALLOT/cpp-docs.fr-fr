---
title: '&lt;streambuf&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866210"
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

Le type est un synonyme du modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="wstreambuf"></a>  wstreambuf

Une spécialisation de `basic_streambuf` qui utilise **wchar_t** comme paramètres de modèle.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<streambuf>](../standard-library/streambuf.md)
