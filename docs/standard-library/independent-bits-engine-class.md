---
description: 'En savoir plus sur : classe independent_bits_engine'
title: independent_bits_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 8da68469c266fae1f9c966b586ea66973d871dc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231681"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine, classe

Génère une séquence aléatoire de nombres avec un nombre spécifié de bits en recompressant les bits des valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Paramètres

*Rotation*\
Type de moteur de base.

*S*\
**Taille de mot**. Taille, en bits, de chaque nombre généré. **Condition préalable**: `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*\
Type des résultats entiers non signés. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md) .

## <a name="members"></a>Membres

`independent_bits_engine::independent_bits_engine`\
`independent_bits_engine::base`\
`independent_bits_engine::base_type`\
`independent_bits_engine::discard`\
`independent_bits_engine::operator()`\
`independent_bits_engine::seed`

Pour plus d’informations sur les membres du moteur, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

Ce modèle de classe décrit un *adaptateur de moteur* qui produit des valeurs en reballant les bits à partir des valeurs retournées par son moteur de base, ce qui donne des valeurs de type *W*-bit.

## <a name="requirements"></a>Spécifications

**En-tête :**\<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
