---
title: '&lt;ostream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 02936fdfc990ea65a99b2875cf7f482eb2ce4ebe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370870"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;, typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

Crée un type à partir de basic_ostream qui est spécialisé sur **char** et `char_traits` spécialisé sur **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="wostream"></a>  wostream

Crée un type à partir de basic_ostream qui est spécialisé sur **wchar_t** et `char_traits` spécialisé sur **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)<br/>
