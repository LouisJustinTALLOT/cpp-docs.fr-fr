---
description: 'En savoir plus sur les éléments suivants : enum chars_format'
title: chars_format, énumération
ms.date: 08/03/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: af458f96e3e9dbe4db9d1adab1c529403cefcaa6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325179"
---
# <a name="chars_format-enum"></a>chars_format, énumération

Utilisé avec la [\<charconv>](charconv.md) bibliothèque pour spécifier le format à virgule flottante pour les conversions numériques Primitives.

## <a name="syntax"></a>Syntaxe

```cpp
enum class chars_format {
    scientific = unspecified,
    fixed = unspecified,
    hex = unspecified,
    general = fixed | scientific
};
```

### <a name="members"></a>Membres

|Élément|Description|
|-|-|
| `scientific` | Oblige `from_chars()` à attendre et à analyser un exposant. Elle est similaire au `printf()` spécificateur de format `'e'` , qui est le format de la notation scientifique, comme `"1.729e+01"` . |
| `fixed` | Oblige `from_chars()` à ne pas attendre ou à analyser un exposant. Elle est similaire au `printf()` spécificateur de format `'f'` , qui est le format de la virgule flottante, par exemple `"17.29"` .|
| `hex` | Oblige `from_chars()` à attendre le nombre au format hexadécimal, mais sans début `0x` . |
| `general` | Oblige `from_chars()` à accepter (mais pas à exiger) un exposant. Pour `to_chars()` , il est semblable au `printf()` spécificateur de format `'g'` , qui bascule entre la notation scientifique ou fixe. Il prend en considération l’exposant pour pouvoir générer une sortie raisonnablement compacte. Par exemple : `1e-5` génère `"1e-05"` , mais `1e-4` génère `"0.001"` . `1e5` génère dans `100000` , tandis que `1e6` génère `1e+06` . `1e0` produit `1` .|

## <a name="remarks"></a>Notes

Pour les fonctions [from_chars](charconv-functions.md#from_chars) , cet enum décrit le type d’entrée à attendre.
Pour les fonctions [to_chars](charconv-functions.md#to_chars) , il décrit le type de sortie à émettre.

## <a name="requirements"></a>Spécifications

**En-tête :**\<charconv>

**Espace de noms :** std

/std : c++ 17, ou version ultérieure, est requis.

## <a name="see-also"></a>Voir aussi

[\<charconv>](../standard-library/charconv.md)  
[spécificateurs de format printf ()](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)
