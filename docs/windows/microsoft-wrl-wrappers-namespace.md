---
title: Microsoft::WRL::Wrappers, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: eac85d10351a141ce561da4272d033644128608f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535484"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers, espace de noms

Définit les types de wrapper Resource Acquisition est d’initialisation (RAII) qui simplifient la gestion de la durée de vie des objets, les chaînes et les descripteurs.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedef

|Nom|Description|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[CriticalSection, classe](../windows/criticalsection-class.md)|Représente un objet de section critique.|
|[Event, classe (WRL)](../windows/event-class-wrl.md)|Représente un événement.|
|[HandleT, classe](../windows/handlet-class.md)|Représente un handle à un objet.|
|[HString, classe](../windows/hstring-class.md)|Prend en charge des handles HSTRING.|
|[HStringReference, classe](../windows/hstringreference-class.md)|Représente un HSTRING créé à partir d’une chaîne existante.|
|[Mutex, classe](../windows/mutex-class.md)|Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.|
|[RoInitializeWrapper, classe](../windows/roinitializewrapper-class.md)|Initialise le Runtime de Windows.|
|[Semaphore, classe](../windows/semaphore-class.md)|Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.|
|[SRWLock, classe](../windows/srwlock-class.md)|Représente un verrou SRW.|

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)