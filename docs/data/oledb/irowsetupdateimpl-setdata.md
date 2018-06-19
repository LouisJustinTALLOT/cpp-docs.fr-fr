---
title: IRowsetUpdateImpl::SetData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: adb15394f4470e23c0ecec2e704829c973c7f3a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103666"
---
# <a name="irowsetupdateimplsetdata"></a>IRowsetUpdateImpl::SetData
Définit les valeurs de données dans une ou plusieurs colonnes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="remarks"></a>Notes  
 Cette méthode remplace la [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) méthode inclut, mais la mise en cache des données d’origine pour permettre le traitement immédiat ou différé de l’opération.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetUpdateImpl, classe](../../data/oledb/irowsetupdateimpl-class.md)