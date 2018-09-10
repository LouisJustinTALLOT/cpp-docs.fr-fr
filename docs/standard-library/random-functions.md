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
ms.openlocfilehash: e01c1d71cbc0b3990e40a38484cc9c7a2cc3ebcc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102796"
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

*RealType*<br/>
Type intégral à virgule flottante. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

*Bits*<br/>
Générateur de nombres aléatoires.

*Gen*<br/>
Générateur de nombres aléatoires.

### <a name="remarks"></a>Notes

Les appels de fonction de modèle `operator()` de *Gen* à plusieurs reprises et compresse les valeurs retournées en une valeur à virgule flottante `x` de type *RealType* jusqu'à ce qu’elle ait recueilli le nombre spécifié de bits de mantisse dans `x`. Le nombre spécifié est le plus petit de *Bits* (qui doit être différente de zéro) et le nombre total de bits de mantisse dans *RealType*. Le premier appel fournit les bits d'ordre le plus bas. La fonction retourne `x`.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
