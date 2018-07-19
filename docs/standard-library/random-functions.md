---
title: '&lt;random&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 5b0cd634dad099669d803d4a2717fc9198151781
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954156"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt;, fonctions

## <a name="generate_canonical"></a>  generate_canonical

Retourne une valeur à virgule flottante à partir d'une séquence aléatoire.

> [!NOTE]
> La norme C++ ISO spécifie que cette fonction doit retourner des valeurs dans la plage [`0`, `1`). Visual Studio n'est pas encore conforme à cette contrainte. Comme solution de contournement pour générer des valeurs dans cette plage, utilisez [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Paramètres

*RealType* type intégral à virgule flottante. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

*Bits* le Générateur de nombres aléatoires.

*Gen* le Générateur de nombres aléatoires.

### <a name="remarks"></a>Notes

Les appels de fonction de modèle `operator()` de *Gen* à plusieurs reprises et compresse les valeurs retournées en une valeur à virgule flottante `x` de type *RealType* jusqu'à ce qu’elle ait recueilli le nombre spécifié de bits de mantisse dans `x`. Le nombre spécifié est le plus petit de *Bits* (qui doit être différente de zéro) et le nombre total de bits de mantisse dans *RealType*. Le premier appel fournit les bits d'ordre le plus bas. La fonction retourne `x`.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
