---
title: shuffle_order_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
ms.openlocfilehash: 972ba83afb5478cd89314817ba823b8d5657c9c8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450417"
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine, classe

Génère une séquence aléatoire en réordonnançant les valeurs retournées à partir de son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>Paramètres

*Rotation*\
Type de moteur de base.

*DK*\
**Taille de table**. Nombre d'éléments dans la mémoire tampon (table). **Condition préalable** : `0 < K`

## <a name="members"></a>Membres

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette classe de modèle décrit un *adaptateur de moteur* qui produit des valeurs en réordonnançant les valeurs retournées par son moteur de base. Chaque constructeur remplit la table interne avec des valeurs *K* retournées par le moteur de base et un élément aléatoire est sélectionné à partir de la table quand une valeur est demandée.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
