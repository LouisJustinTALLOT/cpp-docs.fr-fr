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
ms.openlocfilehash: 0c828708a088c8fe31075a8fe8504f3a1f8c14b4
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337095"
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
 *T*  
 Une classe dérivée de `IRowsetCreator`.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[SetSite](#setsite)|Définit le site qui contient l’objet d’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 Cette classe hérite de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) et remplace [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Lorsqu’un objet de commande ou de la session du fournisseur crée un ensemble de lignes, il appelle `QueryInterface` sur l’objet d’ensemble de lignes que vous recherchez `IObjectWithSite` et appelle `SetSite` en passant l’objet d’ensemble de lignes `IUnkown` interface en tant que l’interface du site.  

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite
Définit le site qui contient l’objet d’ensemble de lignes. Pour plus d’informations, consultez [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pCreator*  
 [in] Pointeur vers le `IUnknown` pointeur d’interface du site de gestion de l’objet d’ensemble de lignes.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 En outre, `IRowsetCreatorImpl::SetSite` permet OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` propriétés. 

## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)