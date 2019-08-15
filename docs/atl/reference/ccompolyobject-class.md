---
title: CComPolyObject (classe)
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
ms.openlocfilehash: deed29b5fb80ea8bbd06b3d50f45e38740b1619f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497153"
---
# <a name="ccompolyobject-class"></a>CComPolyObject (classe)

Cette classe implémente `IUnknown` pour un objet agrégé ou non agrégé.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Paramètres

*contained*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Constructeur.|
|[CComPolyObject::~CComPolyObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Incrémente le décompte de références de l’objet.|
|[CComPolyObject::CreateInstance](#createinstance)|Statique Vous permet de créer un nouvel objet de **<** `contained` **>** CComPolyObject sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Effectue l’initialisation finale de `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Exécute la destruction finale `m_contained`de.|
|[CComPolyObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComPolyObject::Release](#release)|Décrémente le décompte de références de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Délègue `IUnknown` les appels à l’objet externe inconnu si l’objet est agrégé ou `IUnknown` au de l’objet si l’objet n’est pas agrégé.|

## <a name="remarks"></a>Notes

`CComPolyObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé ou non agrégé.

Lorsqu’une instance de `CComPolyObject` est créée, la valeur de l’externe Unknown est vérifiée. Si la valeur est null `IUnknown` , est implémenté pour un objet non agrégé. Si le inconnu externe n’est pas null `IUnknown` , est implémenté pour un objet agrégé.

L’avantage de l' `CComPolyObject` utilisation de est que vous évitez d’avoir à la fois [CComAggObject](../../atl/reference/ccomaggobject-class.md) et [CComObject](../../atl/reference/ccomobject-class.md) dans votre module pour gérer les cas agrégés et non agrégés. Un seul `CComPolyObject` objet gère les deux cas. Cela signifie qu’une seule copie de la vtable et une copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, l' `CComPolyObject` utilisation de peut entraîner une taille de module légèrement supérieure, car elle n’est pas optimisée pour un objet agrégé ou non agrégé `CComAggObject` , `CComObject`comme c’est le cas et.

Si la macro DECLARE_POLY_AGGREGATABLE est spécifiée dans la définition de classe de votre `CComPolyObject` objet, sera utilisée pour créer votre objet. DECLARE_POLY_AGGREGATABLE sera automatiquement déclaré si vous utilisez l’Assistant Projet ATL pour créer un contrôle contrôle total ou Internet Explorer.

Si elle est agrégée `CComPolyObject` , l’objet a `IUnknown`son propre, séparé `IUnknown`de l’objet externe, et conserve son propre nombre de références. `CComPolyObject`utilise [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) pour déléguer à l’externe inconnu.

Pour plus d’informations sur l’agrégation, consultez l’article [notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="addref"></a>  CComPolyObject::AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics ou les tests.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

Constructeur.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*pv*<br/>
dans Pointeur vers le externe inconnu si l’objet doit être agrégé, ou NULL si l’objet n’est pas agrégé.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre de données, [m_contained](#m_contained), et incrémente le nombre de verrous de module.

Le destructeur décrémente le nombre de verrous de module.

##  <a name="dtor"></a>  CComPolyObject::~CComPolyObject

Destructeur.

```
~CComPolyObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appelle [FinalRelease](#finalrelease)et décrémente le nombre de verrous de module.

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

Vous permet de créer un nouvel objet de **<** `contained` **>** CComPolyObject sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Paramètres

*pp*<br/>
à Pointeur vers un pointeur de **<** `contained` **>** CComPolyObject. En `CreateInstance` cas d’échec, *pp* a la valeur null.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre de références égal à zéro, `AddRef` donc appelez-le `Release` immédiatement, puis utilisez pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel `CoCreateInstance`objet sans la surcharge de, utilisez [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Appelée au cours des dernières étapes de la construction de l’objet, cette méthode effectue toute initialisation finale sur le membre de données [m_contained](#m_contained) .

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

Appelée lors de la destruction de l’objet, cette méthode libère le membre de données [m_contained](#m_contained) .

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

Objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*contained*<br/>
dans Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

### <a name="remarks"></a>Notes

`IUnknown`les appels `m_contained` via sont délégués à l’objet externe inconnu si l’objet est agrégé, ou `IUnknown` au de cet objet si l’objet n’est pas agrégé.

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*Q*<br/>
Interface COM.

*iid*<br/>
dans Identificateur de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

*pp*<br/>
à Pointeur vers l’interface identifiée par `__uuidof(Q)`.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour un objet agrégé, si l’interface demandée est `IUnknown`, `QueryInterface` retourne un pointeur vers le propriétaire `IUnknown` de l’objet agrégé et incrémente le décompte de références. Sinon, cette méthode interroge l’interface par le biais `CComContainedObject` du membre de données, [m_contained](#m_contained).

##  <a name="release"></a>  CComPolyObject::Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions Debug `Release` , retourne une valeur qui peut être utile pour les diagnostics ou les tests. Dans les versions de débogage, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
