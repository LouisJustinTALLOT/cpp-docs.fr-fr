---
title: SRWLockSharedTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db9a16671be21b2df7a4ce4f9d87a8b66e097e33
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020146"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (structure)
Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou partagé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct SRWLockSharedTraits;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`Type`|Synonyme pour un pointeur vers le [SRWLOCK](../windows/srwlock-class.md) classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue, méthode](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Récupère un **SRWLockSharedTraits** objet qui est toujours non valide.|  
|[SRWLockSharedTraits::Unlock, méthode](../windows/srwlocksharedtraits-unlock-method.md)|Libère le contrôle exclusif du spécifié `SRWLock` objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)