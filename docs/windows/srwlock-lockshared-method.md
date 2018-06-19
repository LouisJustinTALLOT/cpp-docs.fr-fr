---
title: SRWLOCK::lockshared, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
dev_langs:
- C++
helpviewer_keywords:
- LockShared method
ms.assetid: 9d826a5c-b6a2-4430-ac85-d5753cbca889
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fccc72814ca5c4fff417e0b6221ef0f3c045a5bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33895747"
---
# <a name="srwlocklockshared-method"></a>SRWLock::LockShared, méthode
Acquiert un objet SRWLock en mode partagé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockShared LockShared();  
  
static SyncLockShared LockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `lock`  
 Pointeur vers un objet SRWLock.  
  
## <a name="return-value"></a>Valeur de retour  
 Un objet SRWLock en mode partagé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [SRWLock, classe](../windows/srwlock-class.md)