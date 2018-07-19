---
title: '&lt;limits&gt;, énumérations | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 5795d146714c6eb00902518347138a98574679a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960646"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt;, énumérations

|||
|-|-|
|[float_denorm_style](#float_denorm_style)|[float_round_style](#float_round_style)|

## <a name="float_denorm_style"></a>  float_denorm_style, , énumération

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

### <a name="example"></a>Exemple

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm).

## <a name="float_round_style"></a>float_round_style, énumération

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

### <a name="example"></a>Exemple

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style).

## <a name="see-also"></a>Voir aussi

[\<limits>](../standard-library/limits.md)<br/>
