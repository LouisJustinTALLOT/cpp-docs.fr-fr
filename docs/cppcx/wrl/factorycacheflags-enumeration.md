---
description: 'En savoir plus sur : énumération Factorycacheflags,'
title: FactoryCacheFlags, énumération
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 68a86049bf1f6287a84ae4df2e27dbe3c63c91c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198503"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags, énumération

Détermine si les objets de fabrique sont mis en cache.

## <a name="syntax"></a>Syntaxe

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Notes

Par défaut, la stratégie de mise en cache des fabriques est spécifiée en tant que paramètre de modèle [ModuleType](moduletype-enumeration.md) quand vous créez un objet de [module](module-class.md) . Pour remplacer cette stratégie, spécifiez une valeur **factorycacheflags,** quand vous créez un objet de fabrique.

| Policy | Description |
|-|-|
|`FactoryCacheDefault`|La stratégie de mise en cache de l' `Module` objet est utilisée.|
|`FactoryCacheEnabled`|Active la mise en cache d’usine quel que soit le `ModuleType` paramètre de modèle utilisé pour créer un `Module` objet.|
|`FactoryCacheDisabled`|Désactive la mise en cache de l’usine quel que soit le `ModuleType` paramètre de modèle utilisé pour créer un `Module` objet.|

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
