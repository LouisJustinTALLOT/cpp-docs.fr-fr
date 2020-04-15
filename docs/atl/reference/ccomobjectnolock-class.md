---
title: Classe CComObjectNoLock
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
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327611"
---
# <a name="ccomobjectnolock-class"></a>Classe CComObjectNoLock

Cette classe `IUnknown` implémente pour un objet non agrégaté, mais n’incrémente pas le nombre de verrouillage du module dans le constructeur.

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
|[CComObjectNoLock: CComObjectNoLock](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|Incréments le compte de référence sur l’objet.|
|[CComObjectNoLock:QueryInterface](#queryinterface)|Retourne un pointeur à l’interface demandée.|
|[CComObjectNoLock::Libération](#release)|Décroisse le compte de référence sur l’objet.|

## <a name="remarks"></a>Notes

`CComObjectNoLock`est similaire à [CComObject](../../atl/reference/ccomobject-class.md) en ce qu’il implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet non agrégaté; cependant, `CComObjectNoLock` n’incrémente pas le nombre de verrouillage de module dans le constructeur.

ATL `CComObjectNoLock` utilise en interne pour les usines de classe. En général, vous n’utiliserez pas cette classe directement.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectNoLock::AddRef

Incréments le compte de référence sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock

Constructeur. Contrairement à [CComObject](../../atl/reference/ccomobject-class.md), n’incrémente pas le nombre de verrous du module.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Paramètres

<em>void\*</em><br/>
[dans] Ce paramètre anonyme n’est pas utilisé. Il existe pour la symétrie avec d’autres `CComXXXObjectXXX` constructeurs.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComObjectNoLock: CComObjectNoLock

Destructeur.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObjectNoLock:QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] L’identifiant de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CComObjectNoLock::Libération

Décroisse le compte de référence sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions `Release` de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests. Dans les constructions non-debug, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
