---
title: '&lt;istream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: e9228bddcc3b99503b6b5f0e93b5ed6eeed773d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363094"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt;, typedefs

||||
|-|-|-|
|[iostream](#iostream)|[istream (en)](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a><a name="iostream"></a>iostream

Un `basic_iostream` type spécialisé sur **l’omble**chevalier.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_iostream](../standard-library/basic-iostream-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="istream"></a><a name="istream"></a>istream (en)

Un `basic_istream` type spécialisé sur **l’omble**chevalier.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_istream](../standard-library/basic-istream-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="wiostream"></a><a name="wiostream"></a>wiostream

Un `basic_iostream` type spécialisé sur **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_iostream](../standard-library/basic-iostream-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="wistream"></a><a name="wistream"></a>wistream (wistream)

Un `basic_istream` type spécialisé sur **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_istream](../standard-library/basic-istream-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<>istream](../standard-library/istream.md)
