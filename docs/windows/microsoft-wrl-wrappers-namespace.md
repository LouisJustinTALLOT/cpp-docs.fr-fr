---
title: Microsoft::wrl::wrappers Namespace | Documents Microsoft
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
ms.openlocfilehash: fa666c1a5de2962a4479b355966c1e8282f2989b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878279"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers, espace de noms
Définit les types de wrapper de l’initialisation d’est d’Acquisition de ressources (RAII) qui simplifient la gestion de la durée de vie des objets, les chaînes et les handles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|[HandleT, classe](../windows/handlet-class.md)|Représente un handle d’un objet.|  
|[HString, classe](../windows/hstring-class.md)|Prend en charge pour la manipulation des descripteurs de HSTRING.|  
|[HStringReference, classe](../windows/hstringreference-class.md)|Représente un HSTRING est créé à partir d’une chaîne existante.|  
|[Mutex (classe)](../windows/mutex-class1.md)|Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.|  
|[RoInitializeWrapper, classe](../windows/roinitializewrapper-class.md)|Initialise le Windows Runtime.|  
|[Semaphore, classe](../windows/semaphore-class.md)|Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.|  
|[SRWLock, classe](../windows/srwlock-class.md)|Représente un verrou de lecteur/writer compacte.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)