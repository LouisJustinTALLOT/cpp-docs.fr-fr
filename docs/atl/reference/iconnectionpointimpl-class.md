---
title: Classe IConnectionPointImpl
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329854"
---
# <a name="iconnectionpointimpl-class"></a>Classe IConnectionPointImpl

Cette classe implémente un point de connexion.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IConnectionPointImpl`dérivée de .

*piid*<br/>
Un pointeur à l’IID de l’interface représentée par l’objet point de connexion.

*Cdv*<br/>
Une classe qui gère les connexions. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), qui permet des connexions illimitées. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IConnectionPointImpl::Conseiller](#advise)|Établit un lien entre le point de connexion et un évier.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Crée un enumérateur à itérer à travers les connexions pour le point de connexion.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Récupère l’IID de l’interface représentée par le point de connexion.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Récupère un pointeur d’interface à l’objet connectable.|
|[IConnectionPointImpl::Unadvise](#unadvise)|Termine une connexion précédemment `Advise`établie par .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Gère les connexions pour le point de connexion.|

## <a name="remarks"></a>Notes

`IConnectionPointImpl`implémente un point de connexion, qui permet à un objet d’exposer une interface sortante au client. Le client implémente cette interface sur un objet appelé évier.

ATL utilise [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) pour implémenter l’objet connectable. Chaque point de connexion à l’intérieur de l’objet connectable représente une interface sortante, identifiée par *piid*. *CdV* de classe gère les connexions entre le point de connexion et un évier. Chaque connexion est identifiée de façon unique par un « cookie ».

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, voir l’article [Points de connexion](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionPointImpl::Conseiller

Établit un lien entre le point de connexion et un évier.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Notes

Utilisez [Unadvise](#unadvise) pour mettre fin à l’appel de connexion.

Voir [IConnectionPoint::Conseiller](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) dans le SDK Windows.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointImpl::EnumConnections

Crée un enumérateur à itérer à travers les connexions pour le point de connexion.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Notes

Voir [IConnectionPoint::EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) dans le SDK Windows.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface

Récupère l’IID de l’interface représentée par le point de connexion.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Notes

Voir [IConnectionPoint::GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) dans le SDK Windows.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer

Récupère un pointeur d’interface à l’objet connectable.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Notes

Voir [IConnectionPoint::GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) dans le SDK Windows.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointImpl::m_vec

Gère les connexions entre l’objet de point de connexion et un évier.

```
CDV m_vec;
```

### <a name="remarks"></a>Notes

Par défaut, `m_vec` est de type [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointImpl::Unadvise

Termine une connexion précédemment établie par [l’intermédiaire de Advise](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Notes

Voir [IConnectionPoint:Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
