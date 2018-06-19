---
title: IDBPropertiesImpl::SetProperties | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- SetProperties method
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5067173da531bb8a4f437666ccfc9c9c61bb47f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106477"
---
# <a name="idbpropertiesimplsetproperties"></a>IDBPropertiesImpl::SetProperties
Définit les propriétés dans les groupes de propriétés de Source de données et de l’initialisation, pour les objets de source de données, ou le groupe de propriétés d’initialisation, pour les énumérateurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="remarks"></a>Notes  
 Si le fournisseur est initialisé, cette méthode définit les valeurs des propriétés dans le **DBPROPSET_DATASOURCE**, **DBPROPSET_DATASOURCEINFO**, **DBPROPSET_DBINIT** propriété groupes de l’objet de source de données. Si le fournisseur n’est pas initialisé, il définit **DBPROPSET_DBINIT** uniquement les propriétés de groupe.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Idbpropertiesimpl, classe](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)