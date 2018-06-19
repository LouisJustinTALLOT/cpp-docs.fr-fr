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
ms.openlocfilehash: f89e6e0fc83a83ece82793050441fec9a1e7978b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844495"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine, classe

Génère une séquence aléatoire de nombres avec un nombre spécifié de bits en recompressant les bits des valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Paramètres

`Engine` Le type de moteur de base.

`W` **Taille de mot**. Taille, en bits, de chaque nombre généré. **Condition préalable** : `0 < W ≤ numeric_limits<UIntType>::digits`

`UIntType` Type de résultat de l’entier non signé. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

## <a name="members"></a>Membres

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette classe de modèle décrit un *adaptateur de moteur* qui produit des valeurs en recompressant les bits à partir des valeurs retournées par son moteur de base, ce qui produit des valeurs de `W` bits.

## <a name="requirements"></a>Spécifications

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
