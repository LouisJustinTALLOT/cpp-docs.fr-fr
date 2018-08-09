---
title: Synclockwithstatust::GetStatus, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4677239bbcaff0c72eb11ade259f47531a616f19
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649634"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat d’une opération d’attente sur l’objet qui est basé sur le **SyncLockWithStatusT** de classe, comme un [Mutex](../windows/mutex-class1.md) ou [sémaphore](../windows/semaphore-class.md). Zéro (0) indique que l’opération d’attente a renvoyé l’état signalé ; Sinon, un autre état s’est produite, telles que la valeur de délai d’expiration est écoulé.  
  
## <a name="remarks"></a>Notes  
 Récupère l’état d’attente de l’actuel **SyncLockWithStatusT** objet.  
  
 La fonction GetStatus() récupère la valeur de l’objet sous-jacent [status_](../windows/synclockwithstatust-status-data-member.md) membre de données. Quand un objet basé sur le **SyncLockWithStatusT** classe effectue une opération de verrouillage, l’objet attend tout d’abord l’objet devienne disponible. Le résultat de cette opération d’attente est stocké dans le `status_` membre de données. Les valeurs possibles de le `status_` membre de données sont les valeurs de retour de l’opération d’attente. Pour plus d’informations, consultez les valeurs de retour de la `WaitForSingleObjectEx()` (fonction) dans MSDN Library.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [SyncLockWithStatusT, classe](../windows/synclockwithstatust-class.md)