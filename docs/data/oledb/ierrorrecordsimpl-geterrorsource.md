---
title: IErrorRecordsImpl::GetErrorSource | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
dev_langs:
- C++
helpviewer_keywords:
- GetErrorSource method
ms.assetid: 5436f1ce-c5a4-403b-a62b-c58e70e5c925
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f076bb7c7d436e65473aadb197a90eae51b07fd4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100380"
---
# <a name="ierrorrecordsimplgeterrorsource"></a>IErrorRecordsImpl::GetErrorSource
Obtient le code source qui a provoqué l’erreur à partir d’un enregistrement d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      LPOLESTR GetErrorSource(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rCurError`  
 Un `ERRORINFO` enregistrement dans un **IErrorInfo** interface.  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers une chaîne contenant le code source de l’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IErrorRecordsImpl, classe](../../data/oledb/ierrorrecordsimpl-class.md)