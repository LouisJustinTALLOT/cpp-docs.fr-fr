---
title: CriticalSectionTraits (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs:
- C++
helpviewer_keywords:
- CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5534173d594b8fc09ceca8ec44a1c1223bc550b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870549"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (structure)
Spécialise un objet CriticalSection pour prendre en charge une section critique non valide ou une fonction d’annulation d’une section critique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`Type`|Un `typedef` qui définit un pointeur vers une section critique. `Type` est défini en tant que `typedef CRITICAL_SECTION* Type;`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue, méthode](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Spécialiser un modèle CriticalSection afin que le modèle est toujours non valide.|  
|[CriticalSectionTraits::Unlock, méthode](../windows/criticalsectiontraits-unlock-method.md)|Spécialiser un modèle CriticalSection afin qu’il prend en charge la propriété de libération de l’objet spécifié de section critique.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)