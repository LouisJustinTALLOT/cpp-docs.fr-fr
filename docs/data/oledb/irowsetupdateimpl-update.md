---
title: IRowsetUpdateImpl::Update | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c47ee5bf8c8ddc3436414e89b7d365c06158f195
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104241"
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
Transmet toutes les modifications apportées à la ligne depuis la dernière extraction ou de la mise à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hReserved`  
 [in] Correspond à la `hChapter` paramètre dans [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx).  
  
 Pour les autres paramètres, consultez [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="remarks"></a>Notes  
 Les modifications sont transmises en appelant [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Le consommateur doit appeler [CRowset::Update](../../data/oledb/crowset-update.md) pour que les modifications prennent effet. Définir *prgRowstatus* une valeur appropriée, comme décrit dans [états](https://msdn.microsoft.com/en-us/library/ms722752.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetUpdateImpl, classe](../../data/oledb/irowsetupdateimpl-class.md)