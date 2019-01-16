---
title: ModuleType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 937649eada481f7c45359fa0816266f62dc03875
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335999"
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

## <a name="requirements"></a>Spécifications

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)