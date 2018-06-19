---
title: IErrorRecordsImpl::GetErrorHelpContext | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
dev_langs:
- C++
helpviewer_keywords:
- GetErrorHelpContext method
ms.assetid: 53d70239-0d64-482e-9ad4-4e1f4f02d5a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 684f619dfbf8318951d5668789b6aad18ae48aef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101576"
---
# <a name="ierrorrecordsimplgeterrorhelpcontext"></a>IErrorRecordsImpl::GetErrorHelpContext
Obtient l’ID de contexte d’aide à partir d’un enregistrement d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      DWORD GetErrorHelpContext(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rCurError`  
 Un `ERRORINFO` enregistrement dans un **IErrorInfo** interface.  
  
## <a name="return-value"></a>Valeur de retour  
 L’ID de contexte d’aide pour l’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IErrorRecordsImpl, classe](../../data/oledb/ierrorrecordsimpl-class.md)