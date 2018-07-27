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
ms.openlocfilehash: 558578a82f1906d7481abebc5e1f1719b1983724
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269935"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl, classe
Fournit une implémentation de la [IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx) objet.  
  
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
 Consultez [IGetDataSource::GetDataSource](https://msdn.microsoft.com/library/ms725443.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  
 Cette option est utile si vous avez besoin accéder aux propriétés de l’objet de source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
