---
description: 'En savoir plus sur : énumération RuntimeClassType'
title: RuntimeClassType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 10055d79148124e886c4da50e40ffdb7d3d0fec0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135276"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (énumération)

Spécifie le type d’instance [RuntimeClass](runtimeclass-class.md) qui est pris en charge.

## <a name="syntax"></a>Syntaxe

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ClassicCom`|Classe Runtime COM classique.|
|`Delegate`|Équivalent à `ClassicCom`.|
|`InhibitFtmBase`|Désactive la `FtmBase` prise en charge lorsque `__WRL_CONFIGURATION_LEGACY__` n’est pas défini.|
|`InhibitWeakReference`|Désactive la prise en charge de la référence faible.|
|`WinRt`|Classe Windows Runtime.|
|`WinRtClassicComMix`|Combinaison de `WinRt` et `ClassicCom`.|

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
