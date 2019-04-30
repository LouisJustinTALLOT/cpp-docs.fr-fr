---
title: Microsoft::WRL::Wrappers, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 4b88ad0da31321a696c1238f1c9838d3b3a1c927
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391996"
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
|[CriticalSection, classe](criticalsection-class.md)|Représente un objet de section critique.|
|[Event, classe (WRL)](event-class-wrl.md)|Représente un événement.|
|[HandleT, classe](handlet-class.md)|Représente un handle à un objet.|
|[HString, classe](hstring-class.md)|Prend en charge des handles HSTRING.|
|[HStringReference, classe](hstringreference-class.md)|Représente un HSTRING créé à partir d’une chaîne existante.|
|[Mutex, classe](mutex-class.md)|Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.|
|[RoInitializeWrapper, classe](roinitializewrapper-class.md)|Initialise le Runtime de Windows.|
|[Semaphore, classe](semaphore-class.md)|Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.|
|[SRWLock, classe](srwlock-class.md)|Représente un verrou SRW.|

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)