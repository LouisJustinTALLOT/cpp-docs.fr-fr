---
description: 'En savoir plus sur &lt; : &gt; fonctions aléatoires'
title: '&lt;random&gt;, fonctions'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 39670fcd9b200a6bd56656bbfa07391fdd0d96be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163338"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt;, fonctions

## <a name="generate_canonical"></a><a name="generate_canonical"></a> generate_canonical

Retourne une valeur à virgule flottante à partir d'une séquence aléatoire.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Paramètres

*RealType*\
Type intégral à virgule flottante. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md) .

*Bits*\
Nombre de bits de caractère aléatoire à utiliser.

*Dynamo*\
Classe de générateur de nombres aléatoires.

*Général*\
Référence à une instance d’un générateur de nombres aléatoires de type *Generator*.

### <a name="remarks"></a>Notes

La fonction de modèle appelle à `operator()` plusieurs reprises et comprime les valeurs retournées dans une valeur à virgule flottante  `x` de type *RealType* jusqu’à ce qu’elle ait recueilli le nombre spécifié de bits de mantisse dans `x` . Le nombre spécifié est le plus petit des *bits* (qui doit être différent de zéro) et le nombre complet de bits de mantisse dans *RealType*. Le premier appel fournit les bits d'ordre le plus bas. La fonction retourne `x`.
