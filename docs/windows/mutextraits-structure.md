---
title: MutexTraits (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs:
- C++
helpviewer_keywords:
- MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0406ec7938a623be7b16e0535e9d2c0c769f8392
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874588"
---
# <a name="mutextraits-structure"></a>MutexTraits (structure)
Définit les caractéristiques communes de la [Mutex](../windows/mutex-class1.md) classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct MutexTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[MutexTraits::Unlock, méthode](../windows/mutextraits-unlock-method.md)|Libère le contrôle exclusif d’une ressource partagée.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)