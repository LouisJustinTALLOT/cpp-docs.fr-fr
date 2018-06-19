---
title: Semaphoretraits::Unlock, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0914c6ff83e881f92963fc8a548ddeff587db75e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892245"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock, méthode
Contrôle des versions d’une ressource partagée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `h`  
 Handle vers un objet de sémaphore.  
  
## <a name="remarks"></a>Notes  
 Si l’opération de déverrouillage échoue, Unlock() émet une erreur qui indique la cause de l’échec.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [SemaphoreTraits, structure](../windows/semaphoretraits-structure.md)