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
ms.openlocfilehash: 51964bb2d4cb13394f9efb0e36d572cf9309637d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605665"
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
|[Event, classe (bibliothèque de modèles Windows Runtime C++)](../windows/event-class-windows-runtime-cpp-template-library.md)|Représente un événement.|
|[HandleT, classe](../windows/handlet-class.md)|Représente un handle à un objet.|
|[HString, classe](../windows/hstring-class.md)|Prend en charge des handles HSTRING.|
|[HStringReference, classe](../windows/hstringreference-class.md)|Représente un HSTRING créé à partir d’une chaîne existante.|
|[Mutex (classe)](../windows/mutex-class1.md)|Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.|
|[RoInitializeWrapper, classe](../windows/roinitializewrapper-class.md)|Initialise le Runtime de Windows.|
|[Semaphore, classe](../windows/semaphore-class.md)|Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.|
|[SRWLock, classe](../windows/srwlock-class.md)|Représente un verrou SRW.|

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)