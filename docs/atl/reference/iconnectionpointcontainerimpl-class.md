---
title: Classe IConnectionPointContainerImpl
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: f6009a1341d6715d6d2f170d3ff2aa1aa4ffcb96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329866"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Classe IConnectionPointContainerImpl

Cette classe implémente un conteneur de points de connexion pour gérer une collection d’objets [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IConnectionPointContainerImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crée un enumérateur à itérer à travers les points de connexion pris en charge dans l’objet connectable.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Récupère un pointeur d’interface au point de connexion qui prend en charge l’IID spécifié.|

## <a name="remarks"></a>Notes

`IConnectionPointContainerImpl`implémente un conteneur de points de connexion pour gérer une collection d’objets [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md) `IConnectionPointContainerImpl`fournit deux méthodes qu’un client peut appeler pour récupérer plus d’informations sur un objet connectable :

- `EnumConnectionPoints`permet au client de déterminer quelles interfaces sortantes l’objet prend en charge.

- `FindConnectionPoint`permet au client de déterminer si l’objet prend en charge une interface sortante spécifique.

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, voir l’article [Points de connexion](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

Crée un enumérateur à itérer à travers les points de connexion pris en charge dans l’objet connectable.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Notes

Voir [IConnectionPointContainer::EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) dans le Windows SDK.

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

Récupère un pointeur d’interface au point de connexion qui prend en charge l’IID spécifié.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Notes

Voir [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
