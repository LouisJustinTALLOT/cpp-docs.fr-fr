---
title: Platform::IDisposable (interface)
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637435"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable (interface)

Utilisée pour libérer des ressources non managées.

## <a name="syntax"></a>Syntaxe

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Attributs

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Membres

L’interface IDisposable hérite de l’interface IUnknown. IDisposable a également les types de membre suivants :

**Méthodes**

L’interface IDisposable possède les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|Suppression|Utilisée pour libérer des ressources non managées.|

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform