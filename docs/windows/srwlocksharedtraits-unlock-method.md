---
title: Srwlocksharedtraits::Unlock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7601504c8d1caec02df4b70f97893848e7ff1a5
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012597"
---
# <a name="srwlocksharedtraitsunlock-method"></a>SRWLockSharedTraits::Unlock, méthode
Libère le contrôle exclusif du spécifié `SRWLock` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static void Unlock(  
   _In_ Type srwlock  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *SRWLOCK*  
 Un handle vers un `SRWLock` objet.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [SRWLockSharedTraits, structure](../windows/srwlocksharedtraits-structure.md)