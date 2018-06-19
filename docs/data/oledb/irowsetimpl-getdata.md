---
title: IRowsetImpl::GetData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
dev_langs:
- C++
helpviewer_keywords:
- GetData method [OLE DB]
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3e2a20e8f1948078aec6994516e05f83e95cdcc1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102603"
---
# <a name="irowsetimplgetdata"></a>IRowsetImpl::GetData
Récupère les données à partir de la copie de l’ensemble de lignes de la ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(GetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) dans les *de référence du programmeur OLE DB*.  
  
 Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrits dans les paramètres **IRowset::GetData**:  
  
|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|  
|--------------------------------|------------------------------------------------|  
|*pDstData*|`pData`|  
  
## <a name="remarks"></a>Notes  
 Gère également la conversion de données à l’aide de la DLL de la conversion de données OLE DB.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)