---
title: IRowsetImpl::GetNextRows | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
dev_langs:
- C++
helpviewer_keywords:
- GetNextRows method
ms.assetid: 1c0975d6-d770-4884-830b-6986c6fa8e65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c7106fa4f74ae087a76090b40f86e5c4e5fe947e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102639"
---
# <a name="irowsetimplgetnextrows"></a>IRowsetImpl::GetNextRows
Extrait des lignes séquentiellement, sans oublier la position précédente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(GetNextRows )(HCHAPTER hReserved,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowset::GetNextRows](https://msdn.microsoft.com/en-us/library/ms709827.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)   
 [IRowsetImpl::ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)