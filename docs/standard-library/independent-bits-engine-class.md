---
title: independent_bits_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: f9c1c97795e6d4eeff64ba8be8f22602f4f3fbd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845768"
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

## <a name="requirements"></a>Configuration requise

**En-tête :**\<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
