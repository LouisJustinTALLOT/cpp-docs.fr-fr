---
title: '&lt;ostream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: ff9f19f56c8d8fdb9e469e6361a5419468fe7e67
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846405"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;, typedefs

[ostream](#ostream)\
[wostream](#wostream)

## <a name="ostream"></a><a name="ostream"></a> ostream

Crée un type à partir de basic_ostream qui est spécialisé sur **`char`** et `char_traits` spécialisé sur **`char`** .

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **`char`** avec des caractéristiques de caractère par défaut.

## <a name="wostream"></a><a name="wostream"></a> wostream

Crée un type à partir de basic_ostream qui est spécialisé sur **`wchar_t`** et `char_traits` spécialisé sur **`wchar_t`** .

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **`wchar_t`** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)
