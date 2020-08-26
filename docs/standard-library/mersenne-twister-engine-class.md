---
title: mersenne_twister_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: 24663b12efaef66f29c7f755ab45df5ef973755c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846418"
---
# <a name="mersenne_twister_engine-class"></a>mersenne_twister_engine, classe

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

*UIntType*\
Type des résultats entiers non signés. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md) .

*S*\
**Taille de mot**. Taille de chaque mot, en bits, de la séquence d'état. **Condition préalable**: `2u < W ≤ numeric_limits<UIntType>::digits`

*N*\
**Taille de l’état**. Nombre d'éléments (valeurs) dans la séquence d'état.

*Lecteur*\
**Taille de décalage**. Nombre d'éléments à ignorer pendant chaque torsion. **Condition préalable**: `0 < M ≤ N`

*R*\
**Bits du masque**. **Condition préalable**: `R ≤ W`

*Un*\
**Masque XOR**. **Condition préalable**: `A ≤ (1u<<W) - 1u`

*U*, *S*, *T*, *L*\
**Paramètres de décalage d’altération**. Utilisés comme valeurs de décalage pendant le brouillage (altération). Condition préalable :`U,S,T,L ≤ W`

*D*, *B*, *C*\
**Paramètres de masque de bits d’altération**. Utilisés comme valeurs de masque de bits pendant le brouillage (altération). Condition préalable :`D,B,C ≤ (1u<<W) - 1u`

*FA*\
**Multiplicateur d’initialisation**. Aide à l'initialisation de la séquence. Condition préalable :`F ≤ (1u<<W) - 1u`

## <a name="members"></a>Membres

`mersenne_twister_engine::mersenne_twister_engine`\
`mersenne_twister_engine::discard`\
`mersenne_twister_engine::max`\
`mersenne_twister_engine::min`\
`mersenne_twister_engine::operator()`\
`mersenne_twister_engine::seed`

`default_seed` est une constante membre, définie comme `5489u`, utilisée comme valeur de paramètre par défaut pour `mersenne_twister_engine::seed` et le constructeur de valeur unique.

Pour plus d’informations sur les membres du moteur, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

Ce modèle de classe décrit un moteur de nombres aléatoires, en retournant des valeurs sur l’intervalle fermé [ `0` , `2` <sup>W</sup>  -  `1` ]. Il contient une valeur intégrale élevée avec `W * (N - 1) + R` bits. Il extrait *W* bits à la fois de cette valeur élevée et, quand il a utilisé tous les bits, il déforme la valeur élevée en décalant et en combinant les bits afin qu’il dispose d’un nouvel ensemble de bits à extraire. L’état du moteur est les valeurs de dernier `N` `W` bit utilisées si `operator()` a été appelé au moins *N* fois, sinon les `M` `W` valeurs de bits utilisées et les dernières `N - M` valeurs de la valeur initiale.

Le générateur déforme la valeur élevée qu’il contient à l’aide d’un registre de décalage de commentaires généralisés, défini par les valeurs de décalage *N* et *M*, une valeur de torsion *R*et un masque XOR conditionnel *a*. En outre, les bits du Registre à décalage brut sont brouillés (tempérés) selon une matrice de brouillage des bits définie par les valeurs *U*, *D*, *S*, *B*, *T*, *C*et *L*.

L’argument de modèle `UIntType` doit être suffisamment grand pour contenir des valeurs jusqu’à `2` <sup>W</sup>  -  `1` . Les valeurs des autres arguments de modèle doivent être conformes aux spécifications suivantes : `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

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

Pour plus d’informations sur l’algorithme twister de Mersenne, consultez l’article de Wikipedia [Mersenne twister](https://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Exemple

Pour obtenir un exemple de code, consultez [\<random>](../standard-library/random.md) .

## <a name="requirements"></a>Configuration requise

**En-tête :**\<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
