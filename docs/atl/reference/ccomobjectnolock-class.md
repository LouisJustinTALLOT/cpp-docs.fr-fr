---
description: 'En savoir plus sur : classe CComObjectNoLock'
title: CComObjectNoLock, classe
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: 97708250ecd9637c52daf5db82f39d1a12565399
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142491"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock, classe

Cette classe implémente `IUnknown` pour un objet non agrégé, mais n’incrémente pas le nombre de verrous de module dans le constructeur.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toute autre interface que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructeur.|
|[CComObjectNoLock :: ~ CComObjectNoLock](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectNoLock :: AddRef](#addref)|Incrémente le décompte de références sur l’objet.|
|[CComObjectNoLock :: QueryInterface](#queryinterface)|Retourne un pointeur vers l’interface demandée.|
|[CComObjectNoLock :: Release](#release)|Décrémente le décompte de références sur l’objet.|

## <a name="remarks"></a>Notes

`CComObjectNoLock` est semblable à [CComObject](../../atl/reference/ccomobject-class.md) en ce qu’il implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet non agrégé. Toutefois, `CComObjectNoLock` n’incrémente pas le nombre de verrous de module dans le constructeur.

ATL utilise en `CComObjectNoLock` interne pour les fabriques de classes. En général, vous n’utiliserez pas cette classe directement.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a> CComObjectNoLock :: AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics ou les tests.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a> CComObjectNoLock::CComObjectNoLock

Constructeur. Contrairement à [CComObject](../../atl/reference/ccomobject-class.md), n’incrémente pas le nombre de verrous de module.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Paramètres

<em>void\*</em><br/>
dans Ce paramètre sans nom n’est pas utilisé. Il existe pour la symétrie avec d’autres `CComXXXObjectXXX` constructeurs.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a> CComObjectNoLock :: ~ CComObjectNoLock

Destructeur.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a> CComObjectNoLock :: QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans Identificateur de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a> CComObjectNoLock :: Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur renvoyée

Dans les versions Debug, `Release` retourne une valeur qui peut être utile pour les diagnostics ou les tests. Dans les versions sans débogage, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
