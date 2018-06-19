---
title: SRWLOCK::trylockexclusive, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1cc9ee8a63d7403c3de408c924eeab07f1d0efa1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892655"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive, méthode
Tente d’acquérir un objet SRWLock en mode exclusif pour l’objet SRWLock actuelle ou spécifiée. Si l’appel réussit, le thread appelant prend possession du verrou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `lock`  
 Pointeur vers un objet SRWLock.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, un objet SRWLock en mode exclusif et que le thread appelant prend possession du verrou. Sinon, une SRWLock de l’objet dont l’état n’est pas valide.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [SRWLock, classe](../windows/srwlock-class.md)