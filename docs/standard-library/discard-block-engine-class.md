---
title: discard_block_engine, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: eb00945084affb2be9299953e5ca9352c56d3b32
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688104"
---
# <a name="discard_block_engine-class"></a>discard_block_engine, classe

Génère une séquence aléatoire en ignorant les valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Paramètres

@No__t_1 du *moteur*
Type de moteur de base.

@No__t_1 *P*
**Taille de bloc**. Nombre de valeurs dans chaque bloc.

*R*\
**Bloc utilisé**. Nombre de valeurs dans chaque bloc qui sont utilisées. Les autres sont ignorés (`P`  -  `R`). **Condition préalable** : `0 < R ≤ P`

## <a name="members"></a>Membres

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Ce modèle de classe décrit un adaptateur de moteur qui produit des valeurs en ignorant certaines des valeurs retournées par son moteur de base.

## <a name="requirements"></a>spécifications

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
