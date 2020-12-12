---
description: 'En savoir plus sur : énumération ModuleType'
title: ModuleType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 148f9594fd16a6c8a2af70ac0ff2ac03cd1f62e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209371"
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
|`OutOfProc`|Un serveur hors processus.|
|`DisableCaching`|Désactivez le mécanisme de mise en cache sur le module.|
|`InProcDisableCaching`|Combinaison de `InProc` et `DisableCaching` .|
|`OutOfProcDisableCaching`|Combinaison de `OutOfProc` et `DisableCaching` .|

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
