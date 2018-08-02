---
title: Asyncbase::get_status, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1590d07a7b37e7dd3abf09377a03734299cb124c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460956"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status, méthode
Récupère une valeur qui indique l’état de l’opération asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *status*  
 L’emplacement où l’état doit être stocké. Pour plus d’informations, consultez l’énumération de Windows::Foundation::AsyncStatus.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Notes  
 Cette méthode implémente `IAsyncInfo::get_Status`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)