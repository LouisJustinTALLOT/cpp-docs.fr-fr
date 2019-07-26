---
title: '&lt;ostream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 18f30a12a6f4d2b97cb5dca3ace98e6241d856a7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447167"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;, typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

Crée un type à partir de basic_ostream qui est  spécialisé sur `char_traits` char et spécialisé sur **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="wostream"></a>  wostream

Crée un type à partir de basic_ostream qui est  spécialisé sur `char_traits` wchar_t et spécialisé sur **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)
