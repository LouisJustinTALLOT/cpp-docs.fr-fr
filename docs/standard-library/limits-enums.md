---
title: '&lt;limits&gt;, énumérations | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 356c98ce5c93d1e05a583fc30c4758c5d15d7529
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858157"
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

- **denorm_indeterminate** si la présence ou l’absence de formes dénormalisées ne peut pas être déterminée au moment de la traduction.

- **denorm_absent** en l’absence de formes dénormalisées.

- **denorm_present** en présence de formes dénormalisées.

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

- **round_indeterminate** si le mode d’arrondi ne peut pas être déterminé.

- **round_toward_zero** en cas d’arrondi vers zéro.

- **round_to_nearest** en cas d’arrondi à l’entier le plus proche.

- **round_toward_infinity** en cas d’arrondi vers l’infini.

- **round_toward_neg_infinity** en cas d’arrondi vers l’entier le plus négatif.

### <a name="example"></a>Exemple

Pour obtenir un exemple dans lequel les valeurs de cette énumération sont accessibles, consultez [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style).

## <a name="see-also"></a>Voir aussi

[\<limits>](../standard-library/limits.md)<br/>
