---
title: Mutextraits::Unlock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 7c4e5664-6d95-498a-95bb-d30b5e866c2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9b9d448ae9b73c5a47cc93da41dbcba186fdce0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010708"
---
# <a name="mutextraitsunlock-method"></a>MutexTraits::Unlock, méthode
Libère le contrôle exclusif d’une ressource partagée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *h*  
 Handle vers un objet mutex.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [MutexTraits, structure](../windows/mutextraits-structure.md)