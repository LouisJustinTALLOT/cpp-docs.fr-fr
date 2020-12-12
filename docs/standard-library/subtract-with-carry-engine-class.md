---
description: 'En savoir plus sur : classe subtract_with_carry_engine'
title: subtract_with_carry_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
ms.openlocfilehash: 9d2c082f2c7b8405cf8cd25bce6a77d263fd8f64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183384"
---
# <a name="subtract_with_carry_engine-class"></a>subtract_with_carry_engine, classe

Génère une séquence aléatoire en utilisant l'algorithme Substract With Carry (Lagged Fibonacci).

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Paramètres

*UIntType*\
Type des résultats entiers non signés. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md) .

*S*\
**Taille de mot**. Taille de chaque mot, en bits, de la séquence d'état. **Condition préalable**: `0 < W ≤ numeric_limits<UIntType>::digits`

*X*\
**Décalage court**. Nombre de valeurs entières. **Condition préalable**: `0 < S < R`

*R*\
**Décalage long**. Détermine la périodicité dans la série générée.

## <a name="members"></a>Membres

`subtract_with_carry_engine::subtract_with_carry_engine`
`subtract_with_carry_engine::max`\
`subtract_with_carry_engine::min`\
`subtract_with_carry_engine::discard`\
`subtract_with_carry_engine::operator()`\
`subtract_with_carry_engine::seed`

`default_seed` est une constante membre, définie comme `19780503u`, utilisée comme valeur de paramètre par défaut pour `subtract_with_carry_engine::seed` et le constructeur de valeur unique.

Pour plus d’informations sur les membres du moteur, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

Le `substract_with_carry_engine` modèle de classe est une amélioration par rapport à l' [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Aucun de ces moteurs n’est aussi rapide ni ne produit des résultats d’aussi bonne qualité que [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Ce moteur produit des valeurs d’un type intégral non signé spécifié par l’utilisateur à l’aide de la relation de périodicité ( *période*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M` , où `cy(i)` a la valeur `1` si `x(i - S) - x(i - R) - cy(i - 1) < 0` , sinon `0` , et `M` a la valeur `2` <sup>W</sup>. L’état du moteur est un indicateur de transport plus des valeurs *R* . Ces valeurs sont constituées des dernières valeurs *r* retournées si `operator()` a été appelé au moins une fois *r* , sinon les `N` valeurs qui ont été retournées et les dernières `R - N` valeurs de la valeur initiale.

L'argument de modèle `UIntType` doit être assez volumineux pour contenir des valeurs jusqu'à `M - 1`.

Bien que vous puissiez construire un générateur directement à partir de ce moteur, vous pouvez aussi utiliser l’un des typedefs prédéfinis suivants :

`ranlux24_base` : utilisé comme base pour `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base` : utilisé comme base pour `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Pour plus d’informations sur l’algorithme du moteur Substract With Carry, consultez l’article Wikipedia [Lagged Fibonacci generator](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Spécifications

**En-tête :**\<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
