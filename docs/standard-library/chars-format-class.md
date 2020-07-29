---
title: énumération chars_format
ms.date: 07/22/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: 4c1d495c943be02b66d52d1986a783b29a8009c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230180"
---
# <a name="chars_format-enum"></a>énumération chars_format

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
| `scientific` | Oblige `from_chars()` à attendre et à analyser un exposant. Elle est similaire au `'e'` `printf()` spécificateur de format, qui est le format de la notation scientifique, par exemple`"1.729e+01"` |
| `fixed` | Oblige `from_chars()` à ne pas attendre ou à analyser un exposant. Elle est similaire au `'f'` `printf()` spécificateur de format, qui est le format de la virgule flottante, par exemple `"17.29"` .|
| `hex` | Oblige `from_chars()` à attendre le nombre au format hexadécimal, mais sans « 0x » de début. |
| `general` | Oblige `from_chars()` à accepter (mais pas à exiger) un exposant. Pour `to_chars()` , il est semblable au `g` spécificateur de format printf (), qui passe de la notation scientifique à la notation fixe. Il prend en considération l’exposant pour pouvoir générer une sortie raisonnablement compacte. Par exemple : `1e-5` génère `"1e-05"` , mais `1e-4` génère `"0.001"` . `1e5`génère dans `100000` , tandis que `1e6` génère `1e+06` . `1e0`produit `1` .|

## <a name="remarks"></a>Notes

Pour les fonctions [from_chars](charconv-functions.md#from_chars) , cet enum décrit le type d’entrée à attendre.
Pour les fonctions [to_chars](charconv-functions.md#to_chars) , il décrit le type de sortie à émettre.

## <a name="see-also"></a>Voir aussi

[\<charconv>](../standard-library/charconv.md)  
[spécificateurs de format printf ()](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)
