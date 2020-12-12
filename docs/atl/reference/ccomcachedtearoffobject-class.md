---
description: 'En savoir plus sur : classe CComCachedTearOffObject'
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
ms.openlocfilehash: 321e92b6bdf59834cd6c74b417a1788beefbdcb8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146911"
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

*présent*<br/>
Votre classe détachée, dérivée de `CComTearOffObjectBase` et des interfaces que vous souhaitez que votre objet déchire prenne en charge.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Constructeur.|
|[CComCachedTearOffObject :: ~ CComCachedTearOffObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject :: AddRef](#addref)|Incrémente le décompte de références pour un `CComCachedTearOffObject` objet.|
|[CComCachedTearOffObject :: FinalConstruct](#finalconstruct)|Appelle la `m_contained::FinalConstruct` méthode de la classe Tear.|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Appelle la `m_contained::FinalRelease` méthode de la classe Tear.|
|[CComCachedTearOffObject :: QueryInterface](#queryinterface)|Retourne un pointeur vers le `IUnknown` de l' `CComCachedTearOffObject` objet ou vers l’interface demandée sur votre classe détachée (classe `contained` ).|
|[CComCachedTearOffObject :: Release](#release)|Décrémente le décompte de références pour un `CComCachedTearOffObject` objet et le détruit si le nombre de références est égal à 0.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCachedTearOffObject :: m_contained](#m_contained)|`CComContainedObject`Objet dérivé de votre classe Tear (la classe `contained` ).|

## <a name="remarks"></a>Notes

`CComCachedTearOffObject` implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour une interface détachée. Cette classe diffère de `CComTearOffObject` dans, et est `CComCachedTearOffObject` `IUnknown` distincte de celle de l’objet propriétaire `IUnknown` (le propriétaire est l’objet pour lequel la destruction est créée). `CComCachedTearOffObject` conserve son propre décompte de références sur son `IUnknown` et le supprime une fois que son décompte de références est égal à zéro. Toutefois, si vous interrogez l’une de ses interfaces détachées, le décompte de références de l’objet propriétaire `IUnknown` sera incrémenté.

Si l' `CComCachedTearOffObject` objet qui implémente le déchirement est déjà instancié et que l’interface détachée est recherchée, le même `CComCachedTearOffObject` objet est réutilisé. En revanche, si une interface détachée implémentée par un `CComTearOffObject` est à nouveau interrogée par le biais de l’objet propriétaire, une autre `CComTearOffObject` instance est instanciée.

La classe propriétaire doit implémenter `FinalRelease` et appeler `Release` sur le mis en cache `IUnknown` pour `CComCachedTearOffObject` , ce qui décrémente son décompte de références. Cela entraînera `CComCachedTearOffObject` l' `FinalRelease` appel de et la suppression de la déchirure.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a> CComCachedTearOffObject :: AddRef

Incrémente le décompte de références de l' `CComCachedTearOffObject` objet de 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics et les tests.

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a> CComCachedTearOffObject::CComCachedTearOffObject

Constructeur.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
dans Pointeur vers le `IUnknown` de `CComCachedTearOffObject` .

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre, [m_contained](#m_contained).

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a> CComCachedTearOffObject :: ~ CComCachedTearOffObject

Destructeur.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](#finalrelease).

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a> CComCachedTearOffObject :: FinalConstruct

Appelle `m_contained::FinalConstruct` pour créer `m_contained` , l' `CComContainedObject` <  `contained` objet> utilisé pour accéder à l’interface implémentée par votre classe Tear.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a> CComCachedTearOffObject::FinalRelease

Appelle `m_contained::FinalRelease` la valeur Free `m_contained` , l' `CComContainedObject` <  `contained` objet>.

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a> CComCachedTearOffObject :: m_contained

Objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe Tear.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*présent*<br/>
dans Votre classe détachée, dérivée de `CComTearOffObjectBase` et des interfaces que vous souhaitez que votre objet déchire prenne en charge.

### <a name="remarks"></a>Notes

Les méthodes `m_contained` héritées sont utilisées pour accéder à l’interface détachée dans votre classe détachée par le biais des objets, et de l’objet Tear mis en cache `QueryInterface` `FinalConstruct` `FinalRelease` .

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a> CComCachedTearOffObject :: QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*, ou null si l’interface est introuvable.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si l’interface demandée est `IUnknown` , retourne un pointeur vers le `CComCachedTearOffObject` propre `IUnknown` et incrémente le décompte de références. Sinon, interroge l’interface sur votre classe détachée à l’aide de la méthode [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) héritée de `CComObjectRootEx` .

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a> CComCachedTearOffObject :: Release

Décrémente le nombre de références de 1 et, si le nombre de références est 0, supprime l' `CComCachedTearOffObject` objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur renvoyée

Dans les versions sans débogage, retourne toujours 0. Dans les versions Debug, retourne une valeur qui peut être utile pour les diagnostics ou les tests.

## <a name="see-also"></a>Voir aussi

[CComTearOffObject, classe](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
