---
title: CComCachedTearOffObject, classe
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
ms.openlocfilehash: fb7821da03e1ca69c850fa1a295851faf4af4c5b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277532"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject, classe

Cette classe implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pour une interface détachable.

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

*contained*<br/>
Votre classe détachable, dérivée de `CComTearOffObjectBase` et les interfaces vous souhaitez que votre objet détachable pour prendre en charge.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Constructeur.|
|[CComCachedTearOffObject::~CComCachedTearOffObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Incrémente le décompte de références pour un `CComCachedTearOffObject` objet.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Appelle le `m_contained::FinalConstruct` (la détachable méthode classe).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Appelle le `m_contained::FinalRelease` (la détachable méthode classe).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Retourne un pointeur vers le `IUnknown` de la `CComCachedTearOffObject` objet, ou vers l’interface demandée sur votre classe détachable (la classe `contained`).|
|[CComCachedTearOffObject::Release](#release)|Décrémente le décompte de références pour un `CComCachedTearOffObject` de l’objet et il détruit si le décompte de références est 0.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Un `CComContainedObject` objet dérivé de votre classe détachable (la classe `contained`).|

## <a name="remarks"></a>Notes

`CComCachedTearOffObject` implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pour une interface détachable. Cette classe diffère `CComTearOffObject` dans la mesure `CComCachedTearOffObject` possède son propre `IUnknown`, indépendamment de l’objet propriétaire `IUnknown` (le propriétaire est l’objet pour lequel le détachable est créé). `CComCachedTearOffObject` conserve son propre le décompte de références sur son `IUnknown` et se supprime lui-même une fois que son décompte de références est égal à zéro. Toutefois, si vous interrogez des ses détachable interfaces, le décompte de références de l’objet propriétaire `IUnknown` est incrémenté.

Si le `CComCachedTearOffObject` implémentant le détachable est déjà instancié, et l’interface détachable est interrogée pour là encore, dans le même objet `CComCachedTearOffObject` objet est réutilisé. En revanche, si une interface détachable implémentée par un `CComTearOffObject` est à nouveau interrogée pour via l’objet propriétaire, un autre `CComTearOffObject` sera instancié.

La classe propriétaire doit implémenter `FinalRelease` et appelez `Release` sur la mise en cache `IUnknown` pour le `CComCachedTearOffObject`, qui décrémente son décompte de références. Cela entraîne `CComCachedTearOffObject`de `FinalRelease` pour être appelée et supprimer le détachable.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComCachedTearOffObject::AddRef

Incrémente le décompte de références le `CComCachedTearOffObject` objet par 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour les diagnostics et de test.

##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject

Constructeur.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*pv*<br/>
[in] Pointeur vers le `IUnknown` de la `CComCachedTearOffObject`.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre, [m_contained](#m_contained).

##  <a name="dtor"></a>  CComCachedTearOffObject::~CComCachedTearOffObject

Destructeur.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appels [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct

Appels `m_contained::FinalConstruct` créer `m_contained`, le `CComContainedObject` <  `contained`> objet utilisé pour accéder à l’interface implémentée par votre classe détachable.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease

Appels `m_contained::FinalRelease` pour libérer `m_contained`, le `CComContainedObject` <  `contained`> objet.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objet dérivé de votre classe détachable.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*contained*<br/>
[in] Votre classe détachable, dérivée de `CComTearOffObjectBase` et les interfaces vous souhaitez que votre objet détachable pour prendre en charge.

### <a name="remarks"></a>Notes

Les méthodes `m_contained` hérite sont utilisés pour accéder à l’interface détachable dans votre classe détachable via l’objet mis en cache détachable `QueryInterface`, `FinalConstruct`, et `FinalRelease`.

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
[in] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *iid*, ou NULL si l’interface est introuvable.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si l’interface demandée est `IUnknown`, retourne un pointeur vers le `CComCachedTearOffObject`de propre `IUnknown` et incrémente le décompte de références. Sinon, les requêtes pour l’interface sur votre classe détachables à l’aide de la [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) héritée de la méthode `CComObjectRootEx`.

##  <a name="release"></a>  CComCachedTearOffObject::Release

Décrémente le décompte de références par 1 et, si le décompte de références est 0, supprime le `CComCachedTearOffObject` objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions non debug retourne toujours 0. Dans les versions debug, retourne une valeur qui peut-être être utiles pour le diagnostic ou de test.

## <a name="see-also"></a>Voir aussi

[CComTearOffObject, classe](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
