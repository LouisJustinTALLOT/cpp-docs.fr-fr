---
title: '&lt;limits&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245356"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt;, énumérations

## <a name="float_denorm_style"></a> float_denorm_style

L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour représenter une valeur à virgule flottante dénormalisée (trop petite pour être représentée comme valeur normalisée) :

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Valeur de retour

L’énumération retourne :

- `denorm_indeterminate` Si la présence ou l’absence de formes dénormalisées ne peut pas être déterminée au moment de la traduction.

- `denorm_absent` Si les formes dénormalisées sont absents.

- `denorm_present` Si les formes dénormalisées sont présents.

### <a name="example"></a>Exemples

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm).

## <a name="float_round_style"></a> float_round_style

L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour arrondir une valeur à virgule flottante en une valeur entière.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Valeur de retour

L’énumération retourne :

- `round_indeterminate` Si le mode d’arrondi ne peut pas être déterminé.

- `round_toward_zero` Si l’arrondi vers zéro.

- `round_to_nearest` Si l’arrondi à l’entier le plus proche.

- `round_toward_infinity` Si l’arrondi.

- `round_toward_neg_infinity` Si l’arrondi au nombre entier plus négative.

### <a name="example"></a>Exemples

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style).
