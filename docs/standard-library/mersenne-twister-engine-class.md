---
title: mersenne_twister_engine, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::mersenne_twister_engine
dev_langs:
- C++
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 504d561dd0d7fbc640c898aa8aa70a70337accb8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860643"
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine, classe

Génère une séquence aléatoire d'entiers de haute qualité selon l'algorithme twister de Mersenne.

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Paramètres

`UIntType` Type de résultat de l’entier non signé. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

`W` **Taille de mot**. Taille de chaque mot, en bits, de la séquence d'état. **Condition préalable** : `2u < W ≤ numeric_limits<UIntType>::digits`

`N` **Taille de l’état**. Nombre d'éléments (valeurs) dans la séquence d'état.

`M` **Taille de décalage**. Nombre d'éléments à ignorer pendant chaque torsion. **Condition préalable** : `0 < M ≤ N`

`R` **Masque de bits**. **Condition préalable** : `R ≤ W`

`A` **Masque XOR**. **Condition préalable** : `A ≤ (1u<<W) - 1u`

`U`, `S`, `T`, `L` **Tempering les paramètres de décalage**. Utilisés comme valeurs de décalage pendant le brouillage (altération). Condition préalable :`U,S,T,L ≤ W`

`D`, `B`, `C` **Tempering les paramètres de masque de bits**. Utilisés comme valeurs de masque de bits pendant le brouillage (altération). Condition préalable :`D,B,C ≤ (1u<<W) - 1u`

`F` **Multiplicateur d’initialisation**. Aide à l'initialisation de la séquence. Condition préalable :`F ≤ (1u<<W) - 1u`

## <a name="members"></a>Membres

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` est une constante membre, définie comme `5489u`, utilisée comme valeur de paramètre par défaut pour `mersenne_twister_engine::seed` et le constructeur de valeur unique.

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette classe de modèle décrit un moteur de nombres aléatoires, avec retour de valeurs sur l’intervalle fermé [ `0`, `2`<sup>W</sup> - `1`]. Il contient une valeur intégrale élevée avec `W * (N - 1) + R` bits. Il extrait `W` bits à la fois de cette valeur élevée et, quand il a utilisé tous les bits, il déforme la valeur élevée en décalant et en combinant les bits pour avoir un nouvel ensemble de bits dans lequel procéder à l'extraction. L'état du moteur est représenté par les dernières valeurs de `N` `W` bits utilisées si `operator()` a été appelé au moins `N` fois, sinon les valeurs de `M` `W` bits utilisées et les dernières valeurs `N - M` de la valeur initiale.

Le générateur déforme la valeur élevée qu'il contient en utilisant un registre à décalage de commentaires généralisés déformés défini par les valeurs de décalage `N` et `M`, une valeur de torsion `R` et un masque XOR conditionnel `A`. En outre, les bits du registre à décalage brut sont brouillés (altérés) selon une matrice de brouillage des bits définie par les valeurs `U`, `D`, `S`, `B`, `T`, `C` et `L`.

L’argument de modèle `UIntType` doit être assez volumineux pour contenir des valeurs jusqu’à `2`<sup>W</sup> - `1`. Les valeurs des autres arguments de modèle doivent être conformes aux spécifications suivantes : `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

Bien que vous puissiez construire un générateur directement à partir de ce moteur, nous vous conseillons d’utiliser l’un des typedefs prédéfinis suivants :

`mt19937` : moteur twister Mersenne 32 bits (Matsumoto et Nishimura, 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64` : moteur twister Mersenne 64 bits (Matsumoto et Nishimura, 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Pour plus d’informations sur l’algorithme twister de Mersenne, consultez l’article de Wikipedia [Mersenne twister](http://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Exemple

Pour obtenir un exemple de code, consultez [\<random>](../standard-library/random.md).

## <a name="requirements"></a>Spécifications

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
