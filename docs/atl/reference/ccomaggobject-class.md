---
description: 'En savoir plus sur : CComAggObject, classe'
title: CComAggObject, classe
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: 84af79678221ae74a151a4821039ff1d7a743cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152358"
---
# <a name="ccomaggobject-class"></a>CComAggObject, classe

Cette classe implémente l’interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé. Par définition, un objet agrégé est contenu dans un objet externe. La `CComAggObject` classe est semblable à la [classe CComObject](../../atl/reference/ccomobject-class.md), à ceci près qu’elle expose une interface qui est directement accessible aux clients externes.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Paramètres

*présent*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComAggObject :: CComAggObject](#ccomaggobject)|Constructeur.|
|[CComAggObject :: ~ CComAggObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComAggObject :: AddRef](#addref)|Incrémente le décompte de références sur l’objet agrégé.|
|[CComAggObject :: CreateInstance](#createinstance)|Cette fonction statique vous permet de créer un nouvel objet **CComAggObject<** `contained` **>** sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject :: FinalConstruct](#finalconstruct)|Effectue l’initialisation finale de `m_contained` .|
|[CComAggObject :: FinalRelease](#finalrelease)|Exécute la destruction finale de `m_contained` .|
|[CComAggObject :: QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComAggObject :: Release](#release)|Décrémente le décompte de références sur l’objet agrégé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComAggObject :: m_contained](#m_contained)|Délègue `IUnknown` les appels à l’externe inconnu.|

## <a name="remarks"></a>Notes

`CComAggObject` implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé. `CComAggObject` possède sa propre `IUnknown` interface, séparée de l’interface de l’objet externe `IUnknown` , et gère son propre nombre de références.

Pour plus d’informations sur l’agrégation, consultez l’article [notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a> CComAggObject :: AddRef

Incrémente le décompte de références sur l’objet agrégé.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics ou les tests.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a> CComAggObject :: CComAggObject

Constructeur.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
dans Inconnu externe.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre, [m_contained](#m_contained)et incrémente le nombre de verrous de module.

Le destructeur décrémente le nombre de verrous de module.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a> CComAggObject :: ~ CComAggObject

Destructeur.

```
~CComAggObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appelle [FinalRelease](#finalrelease)et décrémente le nombre de verrous de module.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a> CComAggObject :: CreateInstance

Cette fonction statique vous permet de créer un nouvel objet **CComAggObject<** `contained` **>** sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
à Pointeur vers un **CComAggObject \<**<em> contenu </em>**> pointeur * *. En cas d' `CreateInstance` échec, *pp* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre de références égal à zéro, donc appelez-le `AddRef` immédiatement, puis utilisez `Release` pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans la surcharge de `CoCreateInstance` , utilisez [CComCoClass :: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a> CComAggObject :: FinalConstruct

Appelée au cours des dernières étapes de la construction de l’objet, cette méthode effectue toute initialisation finale sur le membre [m_contained](#m_contained) .

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a> CComAggObject :: FinalRelease

Appelée lors de la destruction de l’objet, cette méthode libère le membre [m_contained](#m_contained) .

```cpp
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a> CComAggObject :: m_contained

Objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*présent*<br/>
dans Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

### <a name="remarks"></a>Notes

Tous les `IUnknown` appels via `m_contained` sont délégués à l’externe inconnu.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a> CComAggObject :: QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans Identificateur de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

*p*<br/>
à Pointeur vers le pointeur d’interface identifié par le type `Q` . Si l’objet ne prend pas en charge cette interface, *pp* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si l’interface demandée est `IUnknown` , `QueryInterface` retourne un pointeur vers le propriétaire de l’objet agrégé `IUnknown` et incrémente le décompte de références. Sinon, cette méthode interroge l’interface par le biais du `CComContainedObject` membre, [m_contained](#m_contained).

## <a name="ccomaggobjectrelease"></a><a name="release"></a> CComAggObject :: Release

Décrémente le décompte de références sur l’objet agrégé.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur renvoyée

Dans les versions Debug, `Release` retourne une valeur qui peut être utile pour les diagnostics ou les tests. Dans les versions sans débogage, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (classe)](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
