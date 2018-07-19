---
title: '&lt;ostream&gt;, typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 094952a76d8e46e4244cf57a8c5a47c929f3ae37
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960350"
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
