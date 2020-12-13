---
description: 'En savoir plus sur : classe shuffle_order_engine'
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
ms.openlocfilehash: 3be8438ac0809d697d081d998450bde09d1d583e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154017"
---
# <a name="shuffle_order_engine-class"></a>shuffle_order_engine, classe

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
**Taille** de la table. Nombre d'éléments dans la mémoire tampon (table). **Condition préalable**: `0 < K`

## <a name="members"></a>Membres

`shuffle_order_engine::shuffle_order_engine`\
`shuffle_order_engine::base`\
`shuffle_order_engine::base_type`\
`shuffle_order_engine::discard`\
`shuffle_order_engine::operator()`\
`shuffle_order_engine::seed`

Pour plus d’informations sur les membres du moteur, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

Ce modèle de classe décrit un *adaptateur de moteur* qui produit des valeurs en réordonnant les valeurs retournées par son moteur de base. Chaque constructeur remplit la table interne avec des valeurs *K* retournées par le moteur de base et un élément aléatoire est sélectionné à partir de la table quand une valeur est demandée.

## <a name="requirements"></a>Spécifications

**En-tête :**\<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
