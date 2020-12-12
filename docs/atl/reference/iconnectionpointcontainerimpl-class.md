---
description: 'En savoir plus sur : classe IConnectionPointContainerImpl'
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
ms.openlocfilehash: 77499954f65b5a447d2f5773c0b4c1dbdbfc5c22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139592"
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
Votre classe, dérivée de `IConnectionPointContainerImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crée un énumérateur pour itérer au sein des points de connexion pris en charge dans l’objet connectable.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Récupère un pointeur d’interface vers le point de connexion qui prend en charge l’IID spécifié.|

## <a name="remarks"></a>Notes

`IConnectionPointContainerImpl` implémente un conteneur de points de connexion pour gérer une collection d’objets [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) . `IConnectionPointContainerImpl` fournit deux méthodes qu’un client peut appeler pour récupérer des informations supplémentaires sur un objet connectable :

- `EnumConnectionPoints` permet au client de déterminer les interfaces sortantes prises en charge par l’objet.

- `FindConnectionPoint` permet au client de déterminer si l’objet prend en charge une interface sortante spécifique.

Pour plus d’informations sur l’utilisation des points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a> IConnectionPointContainerImpl::EnumConnectionPoints

Crée un énumérateur pour itérer au sein des points de connexion pris en charge dans l’objet connectable.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPointContainer :: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) dans la SDK Windows.

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a> IConnectionPointContainerImpl::FindConnectionPoint

Récupère un pointeur d’interface vers le point de connexion qui prend en charge l’IID spécifié.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Notes

Consultez [IConnectionPointContainer :: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Interfaces](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
