---
title: CSession::StartTransaction | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- StartTransaction method
ms.assetid: cd7bd2be-fad1-4e2b-932b-79d308efb8fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cddd3596befcba1e409d0f1575796438ee8c7011
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099028"
---
# <a name="csessionstarttransaction"></a>CSession::StartTransaction
Commence une nouvelle transaction pour cette session.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CSession, classe](../../data/oledb/csession-class.md)