---
title: Classe CComPolyObject
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: e30afef455db5f83afca8ff9e515f39f015c3b8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327558"
---
# <a name="ccompolyobject-class"></a>Classe CComPolyObject

Cette classe `IUnknown` met en œuvre pour un objet agrégé ou non.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Paramètres

*Contenues*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Constructeur.|
|[CComPolyObject: :CComPolyObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Incréments le nombre de références de l’objet.|
|[CComPolyObject::CréerInstance](#createinstance)|(Statique) Vous permet de créer un nouvel `contained` **>** objet **CComPolyObject<** sans les frais généraux de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Effectue l’initialisation `m_contained`finale de .|
|[CComPolyObject::FinalRelease](#finalrelease)|Effectue la destruction `m_contained`finale de .|
|[CComPolyObject:QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComPolyObject::Libération](#release)|Décrément le nombre de références de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Les `IUnknown` délégués appellent vers l’extérieur inconnu si `IUnknown` l’objet est agrégé ou à l’objet si l’objet n’est pas agrégé.|

## <a name="remarks"></a>Notes

`CComPolyObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé ou non agrégat.

Lorsqu’une `CComPolyObject` instance est créée, la valeur de l’inconnu extérieur est vérifiée. S’il est `IUnknown` NULL, est implémenté pour un objet non agrégaté. Si l’inconnu externe `IUnknown` n’est pas NULL, est implémenté pour un objet agrégé.

L’avantage `CComPolyObject` de l’utilisation est que vous évitez d’avoir à la fois [CComAggObject](../../atl/reference/ccomaggobject-class.md) et [CComObject](../../atl/reference/ccomobject-class.md) dans votre module pour traiter les cas agrégés et non-agrégatés. Un `CComPolyObject` seul objet gère les deux cas. Cela signifie qu’une seule copie de la table v et une copie des fonctions existent dans votre module. Si votre vtable est grand, cela peut diminuer considérablement la taille de votre module. Cependant, si votre vtable `CComPolyObject` est petite, l’utilisation peut entraîner une taille de module légèrement plus grande `CComAggObject` parce `CComObject`qu’elle n’est pas optimisée pour un objet agrégé ou non agrégat, comme le sont et .

Si la macro DECLARE_POLY_AGGREGATABLE est spécifiée dans la `CComPolyObject` définition de classe de votre objet, sera utilisée pour créer votre objet. DECLARE_POLY_AGGREGATABLE sera automatiquement déclaré si vous utilisez l’assistant de projet ATL pour créer un contrôle complet ou un contrôle Internet Explorer.

S’il est `CComPolyObject` agrégé, `IUnknown`l’objet a son `IUnknown`propre, séparé de l’objet extérieur, et maintient son propre nombre de références. `CComPolyObject`utilise [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) pour déléguer à l’inconnu extérieur.

Pour plus d’informations sur l’agrégation, voir l’article [Fondamentaux d’ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef

Incréments le compte de référence sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject

Constructeur.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
[dans] Un pointeur vers l’extérieur inconnu si l’objet doit être agrégé, ou NULL si l’objet si l’objet n’est pas agrégé.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre des données, [m_contained](#m_contained)et incrédigne le nombre de verrous du module.

Le destructeur décrète le nombre de verrous du module.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject: :CComPolyObject

Destructeur.

```
~CComPolyObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources [allouées, appelle FinalRelease](#finalrelease)et décrète le nombre de verrous du module.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CréerInstance

Vous permet de créer un nouvel `contained` **>** objet **CComPolyObject<** sans les frais généraux de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Paramètres

*Pp*<br/>
[out] Un pointeur à un `contained` **>** **pointeur CComPolyObject<** pointeur. En `CreateInstance` cas d’échec, *pp* est réglé à NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre `AddRef` de références `Release` de zéro, alors appelez immédiatement, puis utilisez pour libérer la référence sur le pointeur de l’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans frais généraux, `CoCreateInstance`utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct

Appelée lors des dernières étapes de la construction de l’objet, cette méthode effectue une initialisation finale sur le membre [m_contained](#m_contained) données.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease

Appelée lors de la destruction d’objets, cette méthode libère le [m_contained](#m_contained) membre des données.

```
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPolyObject::m_contained

Un objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*Contenues*<br/>
[dans] Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

### <a name="remarks"></a>Notes

`IUnknown`les `m_contained` appels à travers sont délégués à l’inconnu `IUnknown` externe si l’objet est agrégé, ou à l’objet si l’objet n’est pas agrégé.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject:QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*Q*<br/>
L’interface COM.

*Iid*<br/>
[dans] L’identifiant de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est réglé sur NULL.

*Pp*<br/>
[out] Un pointeur à `__uuidof(Q)`l’interface identifiée par .

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour un objet agrégé, si `IUnknown`l’interface demandée est, `QueryInterface` renvoie `IUnknown` un pointeur à l’objet agrégé propre et incréments le nombre de référence. Sinon, cette méthode interroge pour `CComContainedObject` l’interface à travers le membre de données, [m_contained](#m_contained).

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Libération

Décroisse le compte de référence sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions `Release` de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests. Dans les constructions nondebug, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
