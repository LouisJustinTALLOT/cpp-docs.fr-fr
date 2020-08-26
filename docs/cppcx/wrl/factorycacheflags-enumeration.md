---
title: FactoryCacheFlags, énumération
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 3381b2bcfcbf298270b547199ae614291855a2f7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843272"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags, énumération

Détermine si les objets de fabrique sont mis en cache.

## <a name="syntax"></a>Syntaxe

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Notes

Par défaut, la stratégie de mise en cache des fabriques est spécifiée en tant que paramètre de modèle [ModuleType](moduletype-enumeration.md) quand vous créez un objet de [module](module-class.md) . Pour remplacer cette stratégie, spécifiez une valeur **factorycacheflags,** quand vous créez un objet de fabrique.

| Stratégie | Description |
|-|-|
|`FactoryCacheDefault`|La stratégie de mise en cache de l' `Module` objet est utilisée.|
|`FactoryCacheEnabled`|Active la mise en cache d’usine quel que soit le `ModuleType` paramètre de modèle utilisé pour créer un `Module` objet.|
|`FactoryCacheDisabled`|Désactive la mise en cache de l’usine quel que soit le `ModuleType` paramètre de modèle utilisé pour créer un `Module` objet.|

## <a name="requirements"></a>Configuration requise

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
