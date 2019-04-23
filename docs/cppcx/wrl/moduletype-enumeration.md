---
title: ModuleType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 3c7486cbc761975dd133f229f23dcf0b70e7e3ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039150"
---
# <a name="moduletype-enumeration"></a>ModuleType (énumération)

Spécifie si un module doit prendre en charge un serveur in-process ou un serveur out-of-process.

## <a name="syntax"></a>Syntaxe

```cpp
enum ModuleType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`InProc`|Un serveur in-process.|
|`OutOfProc`|Un serveur out-of-process.|
|`DisableCaching`|Désactiver le mécanisme de mise en cache sur le Module.|
|`InProcDisableCaching`|Combinaison de `InProc` et `DisableCaching`.|
|`OutOfProcDisableCaching`|Combinaison de `OutOfProc` et `DisableCaching`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)