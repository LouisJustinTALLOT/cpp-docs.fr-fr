---
title: IRowsetUpdateImpl::GetRowStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
dev_langs:
- C++
helpviewer_keywords:
- GetRowStatus method
ms.assetid: ce57e8be-5891-44d9-b3c5-59ffd3913678
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b646c257e1f8095852eaab2e4cbc4b25bd2ce06
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplgetrowstatus"></a>IRowsetUpdateImpl::GetRowStatus
Retourne l’état des lignes spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hReserved`  
 [in] Correspond à la `hChapter` paramètre dans [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx).  
  
 Pour les autres paramètres, consultez [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetUpdateImpl, classe](../../data/oledb/irowsetupdateimpl-class.md)