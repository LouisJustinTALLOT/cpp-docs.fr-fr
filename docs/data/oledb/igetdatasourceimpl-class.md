---
title: Igetdatasourceimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aee6122e8dbcf85f882e5b78475a2c332b855721
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572164"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl, classe
Fournit une implémentation de la [IGetDataSource](/previous-versions/windows/desktop/ms709721\(v=vs.85\)) objet.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `IGetDataSourceImpl`.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetDataSource](#getdatasource)|Retourne un pointeur d’interface sur l’objet de source de données qui a créé la session.|  
  
## <a name="remarks"></a>Notes  
 Il s’agit une interface obligatoire sur la session pour obtenir un pointeur d’interface à l’objet de source de données.  

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource
Retourne un pointeur d’interface sur l’objet de source de données qui a créé la session.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IGetDataSource::GetDataSource](/previous-versions/windows/desktop/ms725443\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  
 Cette option est utile si vous avez besoin accéder aux propriétés de l’objet de source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)