---
title: '&lt;streambuf&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 505739861771a05dd39741f432579a6e9b2d0c26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664059"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt;, typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Une spécialisation de `basic_streambuf` qui utilise **char** en tant que les paramètres du modèle.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="wstreambuf"></a>  wstreambuf

Une spécialisation de `basic_streambuf` qui utilise **wchar_t** en tant que les paramètres du modèle.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_streambuf](../standard-library/basic-streambuf-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="see-also"></a>Voir aussi

[\<streambuf>](../standard-library/streambuf.md)<br/>
