---
title: Classe CComCachedTearOffObject
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: 019b90c932de144d05fbf05f3ca339f4e5d6edd1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748106"
---
# <a name="ccomcachedtearoffobject-class"></a>Classe CComCachedTearOffObject

Cette classe [implémente IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour une interface déchirante.

## <a name="syntax"></a>Syntaxe

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Paramètres

*Contenues*<br/>
Votre classe de déchirure, `CComTearOffObjectBase` dérivée et les interfaces que vous voulez que votre objet de déchirure à prendre en charge.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Constructeur.|
|[CComCachedTearOffObject: :-CComCachedTearOffObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Incréments le nombre `CComCachedTearOffObject` de références pour un objet.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Appelle `m_contained::FinalConstruct` la méthode (la classe de déchirure).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Appelle `m_contained::FinalRelease` la méthode (la classe de déchirure).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Retourne un pointeur à `IUnknown` `CComCachedTearOffObject` l’objet, ou à l’interface demandée sur votre classe de déchirure (la classe `contained`).|
|[CComCachedTearOffObject::Libération](#release)|Décrément le nombre de `CComCachedTearOffObject` références pour un objet et le détruit si le nombre de références est de 0.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Un `CComContainedObject` objet dérivé de votre classe `contained`de déchirure (la classe ).|

## <a name="remarks"></a>Notes

`CComCachedTearOffObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour une interface déchirante. Cette classe diffère `CComTearOffObject` de `CComCachedTearOffObject` celle `IUnknown`qui a son propre, `IUnknown` séparée de l’objet du propriétaire (le propriétaire est l’objet pour lequel la déchirure est en cours de création). `CComCachedTearOffObject`maintient son propre compte `IUnknown` de référence sur son et se supprime une fois que son nombre de références est nul. Toutefois, si vous interrogez pour l’une de ses interfaces déchirantes, le nombre de références de l’objet du `IUnknown` propriétaire sera incrémenté.

Si `CComCachedTearOffObject` l’objet implémentant la déchirure est déjà instantané et que l’interface de `CComCachedTearOffObject` déchirure est demandée à nouveau, le même objet est réutilisé. En revanche, si une interface de `CComTearOffObject` déchirure implémentée par un `CComTearOffObject` est à nouveau interrogée par l’intermédiaire de l’objet propriétaire, un autre sera instantanée.

La classe propriétaire `FinalRelease` doit `Release` mettre en `IUnknown` œuvre et faire appel à la mise en cache pour le `CComCachedTearOffObject`, qui va décroisser son nombre de références. Cela va `CComCachedTearOffObject`provoquer `FinalRelease` d’être appelé et supprimer la déchirure.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOffObject::AddRef

Incréments le nombre `CComCachedTearOffObject` de références de l’objet par 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic et les tests.

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

Constructeur.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
[dans] Pointeur `IUnknown` à `CComCachedTearOffObject`la de la .

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre, [m_contained](#m_contained).

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearOffObject: :-CComCachedTearOffObject

Destructeur.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](#finalrelease).

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

Appels `m_contained::FinalConstruct` à `m_contained`créer, l’objet `CComContainedObject` <  `contained`> utilisé pour accéder à l’interface implémentée par votre classe de déchirure.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

Appels `m_contained::FinalRelease` à `m_contained`la `CComContainedObject` <  `contained` gratuité , l’objet>.

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CComCachedTearOffObject::m_contained

Un objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe de déchirure.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*Contenues*<br/>
[dans] Votre classe de déchirure, `CComTearOffObjectBase` dérivée et les interfaces que vous voulez que votre objet de déchirure à prendre en charge.

### <a name="remarks"></a>Notes

Les `m_contained` méthodes hérite sont utilisées pour accéder à l’interface déchirante dans votre classe `QueryInterface` `FinalConstruct`de `FinalRelease`déchirure à travers l’objet en cache déchirer, , , et .

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface identifié par *iid*, ou NULL si l’interface n’est pas trouvée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si l’interface `IUnknown`demandée est `CComCachedTearOffObject`, retourne `IUnknown` un pointeur à la propre de la 'et incréments le nombre de référence. Sinon, les requêtes pour l’interface sur votre classe de déchirure `CComObjectRootEx`en utilisant la méthode [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) hérité de .

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOffObject::Libération

Décroisse le compte de référence par 1 et, si `CComCachedTearOffObject` le nombre de références est de 0, supprime l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions non-debug, retourne toujours 0. Dans les constructions de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="see-also"></a>Voir aussi

[Classe CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)<br/>
[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
