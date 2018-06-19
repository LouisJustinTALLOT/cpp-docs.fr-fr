---
title: Microsoft::wrl::wrappers::HandleTraits Namespace | Documents Microsoft
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
ms.openlocfilehash: b114d067249e78d7fb935e473cc3cc952c76fe02
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878032"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits, espace de noms
Décrit les caractéristiques de types courants de ressources basé sur le handle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="structures"></a>Structures  
  
|Nom|Description|  
|----------|-----------------|  
|[CriticalSectionTraits, structure](../windows/criticalsectiontraits-structure.md)|Spécialise une `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction d’annulation d’une section critique.|  
|[EventTraits, structure](../windows/eventtraits-structure.md)|Définit les caractéristiques d’un `Event` handle de classe.|  
|[FileHandleTraits, structure](../windows/filehandletraits-structure.md)|Définit les caractéristiques d’un handle de fichier.|  
|[HANDLENullTraits, structure](../windows/handlenulltraits-structure.md)|Définit les caractéristiques communes d’un handle non initialisé.|  
|[HANDLETraits, structure](../windows/handletraits-structure.md)|Définit les caractéristiques communes d’un handle.|  
|[MutexTraits, structure](../windows/mutextraits-structure.md)|Définit les caractéristiques communes de la [Mutex](../windows/mutex-class1.md) classe.|  
|[SemaphoreTraits, structure](../windows/semaphoretraits-structure.md)|Définit les caractéristiques communes d’un objet sémaphore.|  
|[SRWLockExclusiveTraits, structure](../windows/srwlockexclusivetraits-structure.md)|Décrit des caractéristiques communes de la `SRWLock` classe en mode de verrou exclusif.|  
|[SRWLockSharedTraits, structure](../windows/srwlocksharedtraits-structure.md)|Décrit des caractéristiques communes de la `SRWLock` classe en mode de verrou partagé.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)