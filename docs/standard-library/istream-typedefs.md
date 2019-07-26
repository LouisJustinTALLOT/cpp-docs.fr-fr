---
title: '&lt;istream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 864854fa2697a76c2f3476bcb050d5f5d084dc9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458750"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt;, typedefs

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

Type `basic_iostream` spécialisé sur **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_iostream](../standard-library/basic-iostream-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="istream"></a>  istream

Type `basic_istream` spécialisé sur **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_istream](../standard-library/basic-istream-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="wiostream"></a>  wiostream

Type `basic_iostream` spécialisé sur **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_iostream](../standard-library/basic-iostream-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="wistream"></a>  wistream

Type `basic_istream` spécialisé sur **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_istream](../standard-library/basic-istream-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<istream>](../standard-library/istream.md)
