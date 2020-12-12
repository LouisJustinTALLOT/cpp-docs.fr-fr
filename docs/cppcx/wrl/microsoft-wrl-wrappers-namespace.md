---
description: 'En savoir plus sur : Microsoft :: WRL :: wrappers, espace de noms'
title: Microsoft::WRL::Wrappers, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 603fa14b0e43f481b1afe56d98e355d328f284fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209397"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers, espace de noms

Définit des types de wrappers RAII (Resource Acquisition Is Initialization) qui simplifient la gestion de la durée de vie des objets, des chaînes et des handles.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[CriticalSection, classe](criticalsection-class.md)|Représente un objet de section critique.|
|[Event, classe (WRL)](event-class-wrl.md)|Représente un événement.|
|[Handlet (classe)](handlet-class.md)|Représente un handle vers un objet.|
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

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
