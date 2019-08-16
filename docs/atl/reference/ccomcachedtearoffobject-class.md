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
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497537"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject, classe

Cette classe implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour une interface détachée.

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
Votre classe détachée, dérivée de `CComTearOffObjectBase` et des interfaces que vous souhaitez que votre objet déchire prenne en charge.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Constructeur.|
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Incrémente le décompte de références `CComCachedTearOffObject` pour un objet.|
|[CComCachedTearOffObject:: FinalConstruct](#finalconstruct)|Appelle la `m_contained::FinalConstruct` méthode de la classe Tear.|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Appelle la `m_contained::FinalRelease` méthode de la classe Tear.|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Retourne un pointeur vers le `IUnknown` de l' `CComCachedTearOffObject` objet ou vers l’interface demandée sur votre classe détachée (classe `contained`).|
|[CComCachedTearOffObject::Release](#release)|Décrémente le décompte de références pour `CComCachedTearOffObject` un objet et le détruit si le nombre de références est égal à 0.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Objet dérivé de votre classe Tear (la classe `contained`). `CComContainedObject`|

## <a name="remarks"></a>Notes

`CComCachedTearOffObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour une interface détachée. Cette classe diffère de `CComTearOffObject` `CComCachedTearOffObject` dans `IUnknown`, et est distincte de celle de l’objet `IUnknown` propriétaire (le propriétaire est l’objet pour lequel la destruction est créée). `CComCachedTearOffObject`conserve son propre décompte de références `IUnknown` sur son et le supprime une fois que son décompte de références est égal à zéro. Toutefois, si vous interrogez l’une de ses interfaces détachées, le décompte de références de l’objet `IUnknown` propriétaire sera incrémenté.

Si l' `CComCachedTearOffObject` objet qui implémente le déchirement est déjà instancié et que l’interface détachée est recherchée, le même `CComCachedTearOffObject` objet est réutilisé. En revanche, si une interface détachée implémentée par un `CComTearOffObject` est à nouveau interrogée par le biais de l’objet `CComTearOffObject` propriétaire, une autre instance est instanciée.

La `FinalRelease` classe propriétaire doit implémenter et appeler `Release` sur `CComCachedTearOffObject`le mis `IUnknown` en cache pour, ce qui décrémente son décompte de références. Cela entraînera `CComCachedTearOffObject`l' `FinalRelease` appel de et la suppression de la déchirure.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="addref"></a>  CComCachedTearOffObject::AddRef

Incrémente le décompte de références `CComCachedTearOffObject` de l’objet de 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics et les tests.

##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject

Constructeur.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*pv*<br/>
dans Pointeur vers le `IUnknown` `CComCachedTearOffObject`de.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre, [m_contained](#m_contained).

##  <a name="dtor"></a>  CComCachedTearOffObject::~CComCachedTearOffObject

Destructeur.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct

Appelle `m_contained::FinalConstruct` pour créer `m_contained`, l' `CComContainedObject` objet>utilisé`contained`pour accéder à l’interface implémentée par votre classe Tear. < 

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease

Appelle `m_contained::FinalRelease` la valeur `m_contained`Free, `CComContainedObject`l' <  objet>`contained`.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained

Objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe Tear.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*contained*<br/>
dans Votre classe détachée, dérivée de `CComTearOffObjectBase` et des interfaces que vous souhaitez que votre objet déchire prenne en charge.

### <a name="remarks"></a>Notes

Les méthodes `m_contained` héritées sont utilisées pour accéder à l’interface détachée dans votre classe détachée par le biais des objets, `FinalConstruct`et `FinalRelease`de `QueryInterface`l’objet Tear mis en cache.

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
dans GUID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*, ou null si l’interface est introuvable.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si l’interface demandée est `IUnknown`, retourne un pointeur vers le `CComCachedTearOffObject`propre `IUnknown` et incrémente le décompte de références. Sinon, interroge l’interface sur votre classe détachée à l’aide de la méthode [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) héritée de `CComObjectRootEx`.

##  <a name="release"></a>  CComCachedTearOffObject::Release

Décrémente le nombre de références de 1 et, si le nombre de références est 0, supprime l' `CComCachedTearOffObject` objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions sans débogage, retourne toujours 0. Dans les versions Debug, retourne une valeur qui peut être utile pour les diagnostics ou les tests.

## <a name="see-also"></a>Voir aussi

[CComTearOffObject, classe](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
