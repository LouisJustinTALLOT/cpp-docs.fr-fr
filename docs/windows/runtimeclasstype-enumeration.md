---
title: RuntimeClassType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 62a82d5fab9fd22e23a5244d4fda3b7f5202304c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626809"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (énumération)

Spécifie le type de [RuntimeClass](../windows/runtimeclass-class.md) instance qui est pris en charge.

## <a name="syntax"></a>Syntaxe

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ClassicCom`|Une classe d’exécution COM classique.|
|`Delegate`|Équivalent à `ClassicCom`.|
|`InhibitFtmBase`|Désactive `FtmBase` prise en charge de `__WRL_CONFIGURATION_LEGACY__` n’est pas défini.|
|`InhibitWeakReference`|Désactive la prise en charge de la référence faible.|
|`WinRt`|Une classe Windows Runtime.|
|`WinRtClassicComMix`|Combinaison de `WinRt` et `ClassicCom`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)