---
title: IOpenRowsetImpl::CreateRowset | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d4554a2aeee3218ce505dc2c135167a3e38d55c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105177"
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
Crée un objet d’ensemble de lignes. Pas appelé directement par l’utilisateur. Consultez [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) dans le *de référence du programmeur OLE DB.*  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `RowsetClass`  
 Un membre de classe de modèle qui représente la classe d’ensemble de lignes de l’utilisateur. Généralement, généré par l’Assistant.  
  
 `pRowsetObj`  
 [out] Pointeur vers un objet d’ensemble de lignes. En général, ce paramètre n’est pas utilisé, mais il peut être utilisé si vous devez effectuer davantage de travail sur l’ensemble de lignes avant de le transmettre à un objet COM. La durée de vie de `pRowsetObj` est liée par `ppRowset`.  
  
 Pour les autres paramètres, consultez [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) dans le *de référence du programmeur OLE DB.*  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IOpenRowsetImpl, classe](../../data/oledb/iopenrowsetimpl-class.md)