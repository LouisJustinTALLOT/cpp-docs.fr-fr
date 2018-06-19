---
title: Asyncbase::currentStatus, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75b9a07fd88caa9db7f2f145069b0d8857b79fe9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859688"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus, méthode
Récupère l’état de l’opération asynchrone actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `status`  
 L’emplacement où cette opération stocke l’état actuel.  
  
## <a name="remarks"></a>Notes  
 Cette opération est thread-safe.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase (classe)](../windows/asyncbase-class.md)   
 [AsyncStatusInternal, énumération](../windows/asyncstatusinternal-enumeration.md)