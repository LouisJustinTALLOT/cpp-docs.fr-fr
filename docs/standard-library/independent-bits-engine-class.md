---
title: independent_bits_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: a90e4be4ff6e92734f6b2e6804f8059be78e66b9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456343"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine, classe

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
**Taille de mot**. Taille, en bits, de chaque nombre généré. **Condition préalable** : `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*\
Type des résultats entiers non signés. Pour plus d’informations sur les types possibles, consultez [\<random>](../standard-library/random.md).

## <a name="members"></a>Membres

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette classe de modèle décrit un *adaptateur de moteur* qui produit des valeurs en reballant les bits à partir des valeurs retournées par son moteur de base, ce qui a pour résultat des valeurs de type *W*-bit.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
