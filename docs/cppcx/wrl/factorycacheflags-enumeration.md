---
title: FactoryCacheFlags, énumération
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 8cf4af2ac0b4557fc6b175b84c47f83dd8a6e4ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037443"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags, énumération

Détermine si les objets de fabrique sont mis en cache.

## <a name="syntax"></a>Syntaxe

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Notes

Par défaut, la fabrique de stratégie de mise en cache est spécifiée comme le [ModuleType](moduletype-enumeration.md) paramètre de modèle lorsque vous créez un [Module](module-class.md) objet. Pour remplacer cette stratégie, spécifiez un **FactoryCacheFlags** valeur lorsque vous créez un objet de fabrique.

|||
|-|-|
|`FactoryCacheDefault`|La stratégie de mise en cache de la `Module` objet est utilisé.|
|`FactoryCacheEnabled`|Permet la mise en cache de fabrique, quel que soit le `ModuleType` paramètre de modèle qui est utilisé pour créer un `Module` objet.|
|`FactoryCacheDisabled`|Désactive la mise en cache de fabrique, quel que soit le `ModuleType` paramètre de modèle qui est utilisé pour créer un `Module` objet.|

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)