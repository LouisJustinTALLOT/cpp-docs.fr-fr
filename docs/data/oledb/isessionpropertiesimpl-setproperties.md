---
title: ISessionPropertiesImpl::SetProperties | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- SetProperties method
ms.assetid: 2e1219ed-0e1e-460e-84d6-031acfbfd3d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a174829873442cb0b3e2b50d5e6ba8476f938cc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102317"
---
# <a name="isessionpropertiesimplsetproperties"></a>ISessionPropertiesImpl::SetProperties
Définit les propriétés dans le **DBPROPSET_SESSION** groupe de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [ISessionProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms714405.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Isessionpropertiesimpl, classe](../../data/oledb/isessionpropertiesimpl-class.md)   
 [ISessionPropertiesImpl::GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)