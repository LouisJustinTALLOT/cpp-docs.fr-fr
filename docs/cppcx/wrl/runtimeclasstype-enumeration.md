---
title: RuntimeClassType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213575"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (énumération)

Spécifie le type d’instance [RuntimeClass](runtimeclass-class.md) qui est pris en charge.

## <a name="syntax"></a>Syntaxe

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Name|Description|
|----------|-----------------|
|`ClassicCom`|Classe Runtime COM classique.|
|`Delegate`|Équivaut à `ClassicCom`.|
|`InhibitFtmBase`|Désactive la prise en charge de `FtmBase` lorsque `__WRL_CONFIGURATION_LEGACY__` n’est pas défini.|
|`InhibitWeakReference`|Désactive la prise en charge de la référence faible.|
|`WinRt`|Classe Windows Runtime.|
|`WinRtClassicComMix`|Combinaison de `WinRt` et `ClassicCom`.|

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)
