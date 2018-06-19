---
title: CDataSource::GetProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
dev_langs:
- C++
helpviewer_keywords:
- GetProperty method
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afe21f6f41491a4f62eda09e2df43aa470417e20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090485"
---
# <a name="cdatasourcegetproperty"></a>CDataSource::GetProperty
Retourne la valeur d’une propriété spécifiée pour l’objet de source de données connectée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetProperty(const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guid`  
 [in] Un GUID qui identifie la propriété à définir pour lequel retourner la propriété.  
  
 `propid`  
 [in] ID de propriété pour la propriété à retourner.  
  
 *pVariant*  
 [out] Un pointeur vers la variante où **GetProperty** retourne la valeur de la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir plusieurs propriétés, utilisez [GetProperties](../../data/oledb/cdatasource-getproperties.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDataSource, classe](../../data/oledb/cdatasource-class.md)