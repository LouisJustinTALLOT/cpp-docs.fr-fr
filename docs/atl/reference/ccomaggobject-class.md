---
title: Classe CComAggObject
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
ms.openlocfilehash: 9f05e83c8d0a1fd68fce3228dea9cfeab6183c96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321172"
---
# <a name="ccomaggobject-class"></a>Classe CComAggObject

Cette classe implémente l’interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé. Par définition, un objet agrégé est contenu dans un objet extérieur. La `CComAggObject` classe est similaire à la [classe CComObject](../../atl/reference/ccomobject-class.md), sauf qu’elle expose une interface qui est directement accessible aux clients externes.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Paramètres

*Contenues*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Constructeur.|
|[CComAggObject: CComAggObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Incréments le compte de référence sur l’objet agrégé.|
|[CComAggObject::CréerInstance](#createinstance)|Cette fonction statique vous permet de créer un nouvel `contained` **>** objet **CComAggObject<** sans les frais généraux de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Effectue l’initialisation `m_contained`finale de .|
|[CComAggObject::FinalRelease](#finalrelease)|Effectue la destruction `m_contained`finale de .|
|[CComAggObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComAggObject::Libération](#release)|Décrète le nombre de références sur l’objet agrégé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Les `IUnknown` délégués appellent à l’inconnu extérieur.|

## <a name="remarks"></a>Notes

`CComAggObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé. `CComAggObject`a sa `IUnknown` propre interface, séparée de `IUnknown` l’interface de l’objet extérieur, et maintient son propre nombre de références.

Pour plus d’informations sur l’agrégation, voir l’article [Fondamentaux d’ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAggObject::AddRef

Incréments le compte de référence sur l’objet agrégé.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComAggObject::CComAggObject

Constructeur.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
[dans] L’inconnu extérieur.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre, [m_contained,](#m_contained)et incréments le nombre de verrouillage du module.

Le destructeur décrète le nombre de verrous du module.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAggObject: CComAggObject

Destructeur.

```
~CComAggObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources [allouées, appelle FinalRelease](#finalrelease)et décrète le nombre de verrous du module.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAggObject::CréerInstance

Cette fonction statique vous permet de créer un nouvel `contained` **>** objet **CComAggObject<** sans les frais généraux de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Paramètres

*Pp*<br/>
[out] Un pointeur d’un **CComAggObject\<**<em>contenait</em> **>** un pointeur. En `CreateInstance` cas d’échec, *pp* est réglé à NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre `AddRef` de références `Release` de zéro, alors appelez immédiatement, puis utilisez pour libérer la référence sur le pointeur de l’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans frais généraux, `CoCreateInstance`utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAggObject::FinalConstruct

Appelée lors des dernières étapes de la construction de l’objet, cette méthode effectue une initialisation finale sur le [m_contained](#m_contained) membre.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAggObject::FinalRelease

Appelée lors de la destruction d’objets, cette méthode libère le [m_contained](#m_contained) membre.

```
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAggObject::m_contained

Un objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*Contenues*<br/>
[dans] Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

### <a name="remarks"></a>Notes

Tous `IUnknown` les `m_contained` appels sont délégués à l’inconnu extérieur.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAggObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] L’identifiant de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est réglé sur NULL.

*Pp*<br/>
[out] Un pointeur au pointeur `Q`d’interface identifié par type . Si l’objet ne prend pas en charge cette interface, *pp* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si l’interface `IUnknown` `QueryInterface` demandée est, renvoie un `IUnknown` pointeur à l’objet agrégé propre et incréments le nombre de référence. Sinon, cette méthode interroge pour `CComContainedObject` l’interface à travers le membre, [m_contained](#m_contained).

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAggObject::Libération

Décrète le nombre de références sur l’objet agrégé.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions `Release` de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests. Dans les constructions non-debug, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Classe CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Classe CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
