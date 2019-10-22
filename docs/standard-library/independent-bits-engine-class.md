---
title: independent_bits_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 28c9301d270ef516a1acc59f6ab06f0e61a1c9c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687927"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine, classe

Génère une séquence aléatoire de nombres avec un nombre spécifié de bits en recompressant les bits des valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Paramètres

@No__t_1 du *moteur*
Type de moteur de base.

*W* \
**Taille de mot**. Taille, en bits, de chaque nombre généré. **Condition préalable** : `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType* \
Type des résultats entiers non signés. Pour découvrir les types possibles, consultez [\<random>](../standard-library/random.md).

## <a name="members"></a>Membres

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Ce modèle de classe décrit un *adaptateur de moteur* qui produit des valeurs en reballant les bits à partir des valeurs retournées par son moteur de base, ce qui donne des valeurs de type *W*-bit.

## <a name="requirements"></a>spécifications

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
