---
title: '&lt;ostream&gt;, typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 3f5511cfbf73ddf74fa12954e1a108d8accf875e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852577"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;, typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

Crée un type à partir de basic_ostream qui est spécialisé sur `char`, et `char_traits` spécialisé sur `char`.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md) qui est spécialisé pour les éléments de type `char` ayant les caractéristiques de caractère par défaut.

## <a name="wostream"></a>  wostream

Crée un type à partir de basic_ostream qui est spécialisé sur `wchar_t`, et `char_traits` spécialisé sur `wchar_t`.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md) qui est spécialisé pour les éléments de type `wchar_t` ayant les caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)<br/>
