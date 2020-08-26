---
title: discard_block_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: 6f7b11c360f58e6a838b22fbf2c68366dce973a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846288"
---
# <a name="discard_block_engine-class"></a>discard_block_engine, classe

Génère une séquence aléatoire en ignorant les valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Paramètres

*Rotation*\
Type de moteur de base.

*P*\
**Taille de bloc**. Nombre de valeurs dans chaque bloc.

*R*\
**Bloc utilisé**. Nombre de valeurs dans chaque bloc qui sont utilisées. Les autres sont ignorés ( `P`  -  `R` ). **Condition préalable**: `0 < R ≤ P`

## <a name="members"></a>Membres

`discard_block_engine::discard_block_engine`\
`discard_block_engine::base`\
`discard_block_engine::base_type`\
`discard_block_engine::discard`\
`discard_block_engine::operator()`\
`discard_block_engine::seed`

Pour plus d’informations sur les membres du moteur, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

Ce modèle de classe décrit un adaptateur de moteur qui produit des valeurs en ignorant certaines des valeurs retournées par son moteur de base.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
