---
description: 'En savoir plus sur : &lt; ostream &gt; typedefs'
title: '&lt;ostream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 886fb729f389fac161e4d154e00898b530d1d9f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193017"
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
