---
title: Microsoft::WRL::Wrappers, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: ece26b3f9928d44a593de830cf8a25c57e4c2d89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213744"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers, espace de noms

Définit des types de wrappers RAII (Resource Acquisition Is Initialization) qui simplifient la gestion de la durée de vie des objets, des chaînes et des handles.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|Name|Description|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Classes

|Name|Description|
|----------|-----------------|
|[CriticalSection, classe](criticalsection-class.md)|Représente un objet de section critique.|
|[Event, classe (WRL)](event-class-wrl.md)|Représente un événement.|
|[HandleT, classe](handlet-class.md)|Représente un handle vers un objet.|
|[HString, classe](hstring-class.md)|Prend en charge la manipulation des handles HSTRING.|
|[HStringReference, classe](hstringreference-class.md)|Représente un HSTRING créé à partir d’une chaîne existante.|
|[Mutex, classe](mutex-class.md)|Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.|
|[RoInitializeWrapper, classe](roinitializewrapper-class.md)|Initialise le Windows Runtime.|
|[Semaphore, classe](semaphore-class.md)|Représente un objet de synchronisation qui contrôle une ressource partagée pouvant prendre en charge un nombre limité d’utilisateurs.|
|[SRWLock, classe](srwlock-class.md)|Représente un verrou de lecture/écriture Slim.|

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)
