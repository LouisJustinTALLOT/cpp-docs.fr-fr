---
title: FactoryCacheFlags, énumération
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 250c8c8e7ade72bd1a9cd63f0b515774058f0723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214004"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags, énumération

Détermine si les objets de fabrique sont mis en cache.

## <a name="syntax"></a>Syntaxe

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Notes

Par défaut, la stratégie de mise en cache des fabriques est spécifiée en tant que paramètre de modèle [ModuleType](moduletype-enumeration.md) quand vous créez un objet de [module](module-class.md) . Pour remplacer cette stratégie, spécifiez une valeur **factorycacheflags,** quand vous créez un objet de fabrique.

|||
|-|-|
|`FactoryCacheDefault`|La stratégie de mise en cache de l’objet `Module` est utilisée.|
|`FactoryCacheEnabled`|Active la mise en cache d’usine quel que soit le paramètre de modèle `ModuleType` utilisé pour créer un objet `Module`.|
|`FactoryCacheDisabled`|Désactive la mise en cache de l’usine quel que soit le paramètre de modèle `ModuleType` utilisé pour créer un objet `Module`.|

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)
