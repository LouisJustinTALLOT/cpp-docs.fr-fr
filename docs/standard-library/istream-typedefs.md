---
title: '&lt;istream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: f647fba2036f6c69cb02393e30553c66df34b9dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413292"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt;, typedefs

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

Un type `basic_iostream` spécialisé sur **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_iostream](../standard-library/basic-iostream-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="istream"></a>  istream

Un type `basic_istream` spécialisé sur **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_istream](../standard-library/basic-istream-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="wiostream"></a>  wiostream

Un type `basic_iostream` spécialisé sur **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_iostream](../standard-library/basic-iostream-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="wistream"></a>  wistream

Un type `basic_istream` spécialisé sur **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_istream](../standard-library/basic-istream-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="see-also"></a>Voir aussi

[\<istream>](../standard-library/istream.md)<br/>
