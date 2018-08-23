---
title: ModuleType, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe8d41aded38db7cde5316e04cfa1689845aa4e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595470"
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

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)