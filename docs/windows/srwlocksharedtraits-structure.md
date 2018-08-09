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
ms.openlocfilehash: c606a1a7d32a02442e767a31543a76a4dccf295e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652472"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (structure)
Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou partagé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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