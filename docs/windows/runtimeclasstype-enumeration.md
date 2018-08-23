---
title: Runtimeclasstype, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3358455755ec4c00ebea85fc13fe0022c7b6697
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595452"
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