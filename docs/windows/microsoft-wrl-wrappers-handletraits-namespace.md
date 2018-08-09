---
title: Microsoft::wrl::wrappers::HandleTraits Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c83b921aabeee34b583c8f771190ecf60edccb59
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015809"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits, espace de noms
Décrit les caractéristiques des types courants de ressources basées sur le handle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="structures"></a>Structures  
  
|Nom|Description|  
|----------|-----------------|  
|[CriticalSectionTraits, structure](../windows/criticalsectiontraits-structure.md)|Spécialise une `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction d’annulation d’une section critique.|  
|[EventTraits, structure](../windows/eventtraits-structure.md)|Définit les caractéristiques d’un `Event` handle de classe.|  
|[FileHandleTraits, structure](../windows/filehandletraits-structure.md)|Définit les caractéristiques d’un descripteur de fichier.|  
|[HANDLENullTraits, structure](../windows/handlenulltraits-structure.md)|Définit les caractéristiques communes d’un handle non initialisé.|  
|[HANDLETraits, structure](../windows/handletraits-structure.md)|Définit les caractéristiques communes d’une poignée.|  
|[MutexTraits, structure](../windows/mutextraits-structure.md)|Définit les caractéristiques communes de la [Mutex](../windows/mutex-class1.md) classe.|  
|[SemaphoreTraits, structure](../windows/semaphoretraits-structure.md)|Définit les caractéristiques communes d’un objet sémaphore.|  
|[SRWLockExclusiveTraits, structure](../windows/srwlockexclusivetraits-structure.md)|Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou exclusif.|  
|[SRWLockSharedTraits, structure](../windows/srwlocksharedtraits-structure.md)|Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou partagé.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)