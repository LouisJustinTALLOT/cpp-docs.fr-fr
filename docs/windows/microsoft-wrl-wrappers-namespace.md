---
title: Microsoft::wrl::wrappers Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b1a63494e06ce3117e7e8fccd1d0cbca8cdb4d0
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250339"
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
|[Classe d’événements (WRL)](../windows/event-class-wrl.md)|Représente un événement.|
|[HandleT, classe](../windows/handlet-class.md)|Représente un handle à un objet.|
|[HString, classe](../windows/hstring-class.md)|Prend en charge des handles HSTRING.|
|[HStringReference, classe](../windows/hstringreference-class.md)|Représente un HSTRING créé à partir d’une chaîne existante.|
|[Mutex (classe)](../windows/mutex-class.md)|Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.|
|[RoInitializeWrapper, classe](../windows/roinitializewrapper-class.md)|Initialise le Runtime de Windows.|
|[Semaphore, classe](../windows/semaphore-class.md)|Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.|
|[SRWLock, classe](../windows/srwlock-class.md)|Représente un verrou SRW.|

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)