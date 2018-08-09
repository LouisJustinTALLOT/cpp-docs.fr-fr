---
title: SemaphoreTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
dev_langs:
- C++
helpviewer_keywords:
- SemaphoreTraits structure
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c953efc6e9f4b3904404ae362b6beca7f88192d2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018267"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (structure)
Définit les caractéristiques communes d’un **sémaphore** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[SemaphoreTraits::Unlock, méthode](../windows/semaphoretraits-unlock-method.md)|Contrôle de versions d’une ressource partagée.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)