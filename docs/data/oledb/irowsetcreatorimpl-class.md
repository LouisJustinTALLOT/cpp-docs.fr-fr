---
title: IRowsetCreatorImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51534ffb027e35bbab5a9473cf4190c14b384808
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118135"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl, classe

Effectue les mêmes fonctions que `IObjectWithSite` mais permet également les propriétés OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
### <a name="parameters"></a>Paramètres  

*T*<br/>
Une classe dérivée de `IRowsetCreator`.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[SetSite](#setsite)|Définit le site qui contient l’objet d’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  

Cette classe hérite de [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Lorsqu’un objet de commande ou de la session du fournisseur crée un ensemble de lignes, il appelle `QueryInterface` sur l’objet d’ensemble de lignes que vous recherchez `IObjectWithSite` et appelle `SetSite` en passant l’objet d’ensemble de lignes `IUnkown` interface en tant que l’interface du site.  

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

Définit le site qui contient l’objet d’ensemble de lignes. Pour plus d’informations, consultez [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>Paramètres  

*pCreator*<br/>
[in] Pointeur vers le `IUnknown` pointeur d’interface du site de gestion de l’objet d’ensemble de lignes.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

En outre, `IRowsetCreatorImpl::SetSite` permet OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` propriétés. 

## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)