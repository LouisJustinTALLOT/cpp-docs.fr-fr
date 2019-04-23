---
title: RuntimeClassType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 80e8a120f7e3666721ff839a2a696388a64d734e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035956"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (énumération)

Spécifie le type de [RuntimeClass](runtimeclass-class.md) instance qui est pris en charge.

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

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)