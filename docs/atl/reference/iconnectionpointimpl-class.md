---
description: 'En savoir plus sur : classe IConnectionPointImpl'
title: IConnectionPointImpl, classe
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
ms.openlocfilehash: d87eb0821a3a48d171c196c891b5f5c7aacb9cdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139579"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl, classe

Cette classe implémente un point de connexion.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IConnectionPointImpl` .

*piid*<br/>
Pointeur vers l’IID de l’interface représentée par l’objet de point de connexion.

*CDV*<br/>
Classe qui gère les connexions. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), ce qui permet des connexions illimitées. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IConnectionPointImpl :: Advise](#advise)|Établit une connexion entre le point de connexion et un récepteur.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Crée un énumérateur pour itérer au sein des connexions pour le point de connexion.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Récupère l’IID de l’interface représentée par le point de connexion.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Récupère un pointeur d’interface vers l’objet connectable.|
|[IConnectionPointImpl :: Unadvise](#unadvise)|Met fin à une connexion précédemment établie par le biais de `Advise` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IConnectionPointImpl :: m_vec](#m_vec)|Gère les connexions pour le point de connexion.|

## <a name="remarks"></a>Notes

`IConnectionPointImpl` implémente un point de connexion, qui permet à un objet d’exposer une interface sortante au client. Le client implémente cette interface sur un objet appelé récepteur.

ATL utilise [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) pour implémenter l’objet connectable. Chaque point de connexion dans l’objet connectable représente une interface sortante, identifiée par *piid*. La classe *CDV* gère les connexions entre le point de connexion et un récepteur. Chaque connexion est identifiée de manière unique par un « cookie ».

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a> IConnectionPointImpl :: Advise

Établit une connexion entre le point de connexion et un récepteur.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Notes

Utilisez [Unadvise](#unadvise) pour mettre fin à l’appel de connexion.

Consultez [IConnectionPoint :: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) dans le SDK Windows.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a> IConnectionPointImpl::EnumConnections

Crée un énumérateur pour itérer au sein des connexions pour le point de connexion.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPoint :: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) dans la SDK Windows.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a> IConnectionPointImpl::GetConnectionInterface

Récupère l’IID de l’interface représentée par le point de connexion.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPoint :: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) dans la SDK Windows.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a> IConnectionPointImpl::GetConnectionPointContainer

Récupère un pointeur d’interface vers l’objet connectable.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPoint :: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) dans la SDK Windows.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a> IConnectionPointImpl :: m_vec

Gère les connexions entre l’objet de point de connexion et un récepteur.

```
CDV m_vec;
```

### <a name="remarks"></a>Notes

Par défaut, `m_vec` est de type [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a> IConnectionPointImpl :: Unadvise

Met fin à une connexion précédemment établie par le biais de la [notification](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPoint :: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
