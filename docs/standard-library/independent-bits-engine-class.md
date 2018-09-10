---
title: independent_bits_engine, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb76c477c54192dc6b6b969ecd4cdd32850c015f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110303"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine, classe

Génère une séquence aléatoire de nombres avec un nombre spécifié de bits en recompressant les bits des valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Paramètres

*Moteur*<br/>
Type de moteur de base.

*W*<br/>
**Taille de mot**. Taille, en bits, de chaque nombre généré. **Condition préalable** : `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*<br/>
Type des résultats entiers non signés. Pour plus d’informations sur les types possibles, consultez [\<random>](../standard-library/random.md).

## <a name="members"></a>Membres

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette classe de modèle décrit un *adaptateur de moteur* qui produit des valeurs en recompressant les bits des valeurs retournées par son moteur de base, ce qui entraîne *W*-bit des valeurs.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
