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
ms.openlocfilehash: 1b65cfbe156ba462af9e87abf82d63023cfdc44b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957436"
---
# <a name="discardblockengine-class"></a>discard_block_engine, classe

Génère une séquence aléatoire en ignorant les valeurs retournées par son moteur de base.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Paramètres

*Moteur* le type de moteur de base.

*P* **taille de bloc**. Nombre de valeurs dans chaque bloc.

*R* **bloc utilisé**. Nombre de valeurs dans chaque bloc qui sont utilisées. Les autres sont ignorées (`P` - `R`). **Condition préalable** : `0 < R ≤ P`

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
