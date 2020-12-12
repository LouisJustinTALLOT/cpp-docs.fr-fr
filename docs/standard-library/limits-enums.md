---
description: 'En savoir plus sur : &lt; limites &gt; enums'
title: '&lt;limits&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 115122a4901298018df8809be56a7fc69249d700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312863"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt;, énumérations

## <a name="float_denorm_style"></a><a name="float_denorm_style"></a> float_denorm_style

L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour représenter une valeur à virgule flottante dénormalisée (trop petite pour être représentée comme valeur normalisée) :

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Valeur renvoyée

L’énumération retourne :

- `denorm_indeterminate` Si la présence ou l’absence de formulaires dénormalisés ne peut pas être déterminée au moment de la traduction.

- `denorm_absent` Si les formulaires dénormalisés sont absents.

- `denorm_present` Si des formulaires dénormalisés sont présents.

### <a name="example"></a>Exemple

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm).

## <a name="float_round_style"></a><a name="float_round_style"></a> float_round_style

L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour arrondir une valeur à virgule flottante en une valeur entière.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Valeur renvoyée

L’énumération retourne :

- `round_indeterminate` Si la méthode d’arrondi ne peut pas être déterminée.

- `round_toward_zero` Si la valeur est arrondie à zéro.

- `round_to_nearest` Si la valeur est arrondie à l’entier le plus proche.

- `round_toward_infinity` Si le arrondi est éloigné de zéro.

- `round_toward_neg_infinity` Si la valeur est arrondie à un entier négatif.

### <a name="example"></a>Exemple

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style).
