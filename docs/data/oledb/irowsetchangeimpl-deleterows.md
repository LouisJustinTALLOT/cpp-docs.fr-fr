---
title: IRowsetChangeImpl::DeleteRows | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
dev_langs: C++
helpviewer_keywords: DeleteRows method
ms.assetid: 462ad4f1-3b2a-4134-9733-be65708aa1d9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 92ae29bc2a9e3d7e2fc246b4f43e3a7f586475da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetchangeimpldeleterows"></a>IRowsetChangeImpl::DeleteRows
Supprime les lignes à partir de l’ensemble de lignes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD ( DeleteRows )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetChange::DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetChangeImpl, classe](../../data/oledb/irowsetchangeimpl-class.md)