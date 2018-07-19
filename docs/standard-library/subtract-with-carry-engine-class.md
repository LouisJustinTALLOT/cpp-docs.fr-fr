---
title: subtract_with_carry_engine, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6bd4a7827ec5223297f3ec3195724b62d4dc72c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955304"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine, classe

Génère une séquence aléatoire en utilisant l'algorithme Substract With Carry (Lagged Fibonacci).

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Paramètres

*UIntType*  
 Type des résultats entiers non signés. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

*W*  
 **Taille de mot**. Taille de chaque mot, en bits, de la séquence d'état. **Condition préalable** : `0 < W ≤ numeric_limits<UIntType>::digits`

*S*  
 **Décalage court**. Nombre de valeurs entières. **Condition préalable** : `0 < S < R`

*R*  
 **Décalage long**. Détermine la périodicité dans la série générée.

## <a name="members"></a>Membres

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` est une constante membre, définie comme `19780503u`, utilisée comme valeur de paramètre par défaut pour `subtract_with_carry_engine::seed` et le constructeur de valeur unique.|||

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

La classe de modèle `substract_with_carry_engine` est une version améliorée du [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Aucun de ces moteurs n’est aussi rapide ni ne produit des résultats d’aussi bonne qualité que [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Ce moteur produit des valeurs d’un type intégral non signé, spécifié par l’utilisateur, à l’aide de la relation de périodicité ( *période*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, où `cy(i)` a la valeur `1` si `x(i - S) - x(i - R) - cy(i - 1) < 0`, sinon `0`, et `M` a la valeur `2`<sup>W</sup>. L’état du moteur est un carry indicateur plu *R* valeurs. Ces valeurs sont constituées de la dernière *R* valeurs retournées si `operator()` a été appelé au moins *R* fois, sinon le `N` les valeurs qui ont été retournés et la dernière `R - N` valeurs de la valeur de départ.

L'argument de modèle `UIntType` doit être assez volumineux pour contenir des valeurs jusqu'à `M - 1`.

Bien que vous puissiez construire un générateur directement à partir de ce moteur, vous pouvez aussi utiliser l’un des typedefs prédéfinis suivants :

`ranlux24_base` : utilisé comme base pour `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base` : utilisé comme base pour `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Pour plus d’informations sur l’algorithme du moteur Substract With Carry, consultez l’article Wikipedia [Lagged Fibonacci generator](http://go.microsoft.com/fwlink/p/?linkid=402445).

## <a name="requirements"></a>Spécifications

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
