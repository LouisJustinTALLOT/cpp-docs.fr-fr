---
title: discard_block_engine, classe │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c9620003c1f57af966628dda2a5a0ab8352c6d2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107313"
---
# <a name="discardblockengine-class"></a>discard_block_engine, classe

Génère une séquence aléatoire en ignorant les valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Paramètres

*Moteur*<br/>
Type de moteur de base.

*P*<br/>
**Taille de bloc**. Nombre de valeurs dans chaque bloc.

*R*<br/>
**Bloc utilisé**. Nombre de valeurs dans chaque bloc qui sont utilisées. Les autres sont ignorées (`P` - `R`). **Condition préalable** : `0 < R ≤ P`

## <a name="members"></a>Membres

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Pour plus d’informations sur les membres moteurs, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette classe de modèle décrit un adaptateur de moteur qui produit des valeurs en écartant certaines des valeurs retournées par son moteur de base.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
