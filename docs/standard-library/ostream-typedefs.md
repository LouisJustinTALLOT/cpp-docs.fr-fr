---
title: '&lt;ostream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373580"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;, typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

Crée un type de basic_ostream qui est `char_traits` spécialisé sur **l’omble** et spécialisé sur **l’omble**chevalier.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="wostream"></a><a name="wostream"></a>wostream (wostream)

Crée un type à partir de basic_ostream qui `char_traits` est spécialisé sur **wchar_t** et spécialisé sur **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ostream](../standard-library/basic-ostream-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<>ostream](../standard-library/ostream.md)
