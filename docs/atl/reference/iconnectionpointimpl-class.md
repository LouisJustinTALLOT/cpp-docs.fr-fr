---
title: Classe de IConnectionPointImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444dea401fa711b40e4d8229b26c9cdbf6d1fcbc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362638"
---
# <a name="iconnectionpointimpl-class"></a>Classe de IConnectionPointImpl
Cette classe implémente un point de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IConnectionPointImpl`.  
  
 `piid`  
 Pointeur vers l’IID de l’interface représentée par l’objet de point de connexion.  
  
 `CDV`  
 Une classe qui gère les connexions. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), ce qui permet un nombre illimité de connexions. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|Établit une connexion entre le point de connexion et un récepteur.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Crée un énumérateur pour itérer via les connexions pour le point de connexion.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Récupère l’IID de l’interface représentée par le point de connexion.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Récupère un pointeur d’interface vers l’objet connectable.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|Termine une connexion précédemment établie via `Advise`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|Gère les connexions pour le point de connexion.|  
  
## <a name="remarks"></a>Notes  
 `IConnectionPointImpl` implémente un point de connexion, ce qui permet à un objet d’exposer une interface sortante au client. Le client implémente cette interface sur un objet appelé récepteur.  
  
 ATL utilise [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) pour implémenter l’objet connectable. Chaque point de connexion dans l’objet connectable représente une interface sortante, identifiée par `piid`. Classe *CDV* gère les connexions entre le point de connexion et un récepteur. Chaque connexion est identifiée par un « cookie ».  
  
 Pour plus d’informations sur l’utilisation de points de connexion dans les ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="advise"></a>  IConnectionPointImpl::Advise  
 Établit une connexion entre le point de connexion et un récepteur.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>Notes  
 Utilisez [Unadvise](#unadvise) pour mettre fin à l’appel de la connexion.  
  
 Consultez [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) dans le Kit de développement logiciel Windows.  
  
##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections  
 Crée un énumérateur pour itérer via les connexions pour le point de connexion.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) dans le Kit de développement logiciel Windows.  
  
##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface  
 Récupère l’IID de l’interface représentée par le point de connexion.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) dans le Kit de développement logiciel Windows.  
  
##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer  
 Récupère un pointeur d’interface vers l’objet connectable.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) dans le Kit de développement logiciel Windows.  
  
##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec  
 Gère les connexions entre l’objet de point de connexion et un récepteur.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>Notes  
 Par défaut, `m_vec` est de type [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).  
  
##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise  
 Termine une connexion précédemment établie via [Advise](#advise).  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
