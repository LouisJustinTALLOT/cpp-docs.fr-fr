---
title: '&lt;random&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 87b640d4f3aa3fbfa23ad5603d84102301e71ea4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240385"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt;, fonctions

## <a name="generate_canonical"></a> generate_canonical

Retourne une valeur à virgule flottante à partir d'une séquence aléatoire.

> [!NOTE]
> La norme C++ ISO spécifie que cette fonction doit retourner des valeurs dans la plage [`0`, `1`). Visual Studio n'est pas encore conforme à cette contrainte. Comme solution de contournement pour générer des valeurs dans cette plage, utilisez [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Paramètres

*RealType*\
Type intégral à virgule flottante. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

*Bits*\
Générateur de nombres aléatoires.

*Gen*\
Générateur de nombres aléatoires.

### <a name="remarks"></a>Notes

Les appels de fonction de modèle `operator()` de *Gen* à plusieurs reprises et compresse les valeurs retournées en une valeur à virgule flottante `x` de type *RealType* jusqu'à ce qu’elle ait recueilli le nombre spécifié de bits de mantisse dans `x`. Le nombre spécifié est le plus petit de *Bits* (qui doit être différente de zéro) et le nombre total de bits de mantisse dans *RealType*. Le premier appel fournit les bits d'ordre le plus bas. La fonction retourne `x`.
