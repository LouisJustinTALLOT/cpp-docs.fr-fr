---
title: '&lt;streambuf&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8eb058f161a9f30ccf5e9d49307b50c215f79c22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376684"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt;, typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

Une spécialisation `basic_streambuf` de ce qui utilise **l’omble** comme paramètres de modèle.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Notes

Le type est synonyme pour le modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf

Une spécialisation `basic_streambuf` de ce qui utilise **wchar_t** comme paramètres de modèle.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Notes

Le type est synonyme pour le modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<>streambuf](../standard-library/streambuf.md)
