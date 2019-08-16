---
title: IConnectionPointContainerImpl, classe
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
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496022"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl, classe

Cette classe implémente un conteneur de points de connexion pour gérer une collection d’objets [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IConnectionPointContainerImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crée un énumérateur pour itérer au sein des points de connexion pris en charge dans l’objet connectable.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Récupère un pointeur d’interface vers le point de connexion qui prend en charge l’IID spécifié.|

## <a name="remarks"></a>Notes

`IConnectionPointContainerImpl`implémente un conteneur de points de connexion pour gérer une collection d’objets [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) . `IConnectionPointContainerImpl`fournit deux méthodes qu’un client peut appeler pour récupérer des informations supplémentaires sur un objet connectable:

- `EnumConnectionPoints`permet au client de déterminer les interfaces sortantes prises en charge par l’objet.

- `FindConnectionPoint`permet au client de déterminer si l’objet prend en charge une interface sortante spécifique.

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

Crée un énumérateur pour itérer au sein des points de connexion pris en charge dans l’objet connectable.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) dans la SDK Windows.

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

Récupère un pointeur d’interface vers le point de connexion qui prend en charge l’IID spécifié.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
