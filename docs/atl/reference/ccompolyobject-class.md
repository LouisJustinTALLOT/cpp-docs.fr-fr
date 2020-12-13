---
description: 'En savoir plus sur : classe CComPolyObject'
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
ms.openlocfilehash: 1584fd03882b0eb0618bd20b54134317efd17ba8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142400"
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

*présent*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject :: CComPolyObject](#ccompolyobject)|Constructeur.|
|[CComPolyObject :: ~ CComPolyObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComPolyObject :: AddRef](#addref)|Incrémente le décompte de références de l’objet.|
|[CComPolyObject :: CreateInstance](#createinstance)|Statique Vous permet de créer un nouvel objet de **<CComPolyObject** `contained` **>** sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject :: FinalConstruct](#finalconstruct)|Effectue l’initialisation finale de `m_contained` .|
|[CComPolyObject :: FinalRelease](#finalrelease)|Exécute la destruction finale de `m_contained` .|
|[CComPolyObject :: QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComPolyObject :: Release](#release)|Décrémente le décompte de références de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject :: m_contained](#m_contained)|Délègue les `IUnknown` appels à l’objet externe inconnu si l’objet est agrégé ou au `IUnknown` de l’objet si l’objet n’est pas agrégé.|

## <a name="remarks"></a>Notes

`CComPolyObject` implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet agrégé ou non agrégé.

Lorsqu’une instance de `CComPolyObject` est créée, la valeur de l’externe Unknown est vérifiée. Si la valeur est NULL, `IUnknown` est implémenté pour un objet non agrégé. Si le inconnu externe n’est pas NULL, `IUnknown` est implémenté pour un objet agrégé.

L’avantage de l’utilisation de `CComPolyObject` est que vous évitez d’avoir à la fois [CComAggObject](../../atl/reference/ccomaggobject-class.md) et [CComObject](../../atl/reference/ccomobject-class.md) dans votre module pour gérer les cas agrégés et non agrégés. Un seul `CComPolyObject` objet gère les deux cas. Cela signifie qu’une seule copie de la vtable et une copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, l’utilisation de `CComPolyObject` peut entraîner une taille de module légèrement supérieure, car elle n’est pas optimisée pour un objet agrégé ou non agrégé, comme c’est le cas `CComAggObject` et `CComObject` .

Si la macro DECLARE_POLY_AGGREGATABLE est spécifiée dans la définition de classe de votre objet, `CComPolyObject` sera utilisée pour créer votre objet. DECLARE_POLY_AGGREGATABLE est automatiquement déclarée si vous utilisez l’Assistant Projet ATL pour créer un contrôle contrôle total ou Internet Explorer.

Si elle est agrégée, l' `CComPolyObject` objet a son propre `IUnknown` , séparé de l’objet externe `IUnknown` , et conserve son propre nombre de références. `CComPolyObject` utilise [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) pour déléguer à l’externe inconnu.

Pour plus d’informations sur l’agrégation, consultez l’article [notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a> CComPolyObject :: AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics ou les tests.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a> CComPolyObject :: CComPolyObject

Constructeur.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
dans Pointeur vers le externe inconnu si l’objet doit être agrégé, ou NULL si l’objet n’est pas agrégé.

### <a name="remarks"></a>Notes

Initialise les `CComContainedObject` données membres, [m_contained](#m_contained)et incrémente le nombre de verrous de module.

Le destructeur décrémente le nombre de verrous de module.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a> CComPolyObject :: ~ CComPolyObject

Destructeur.

```
~CComPolyObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appelle [FinalRelease](#finalrelease)et décrémente le nombre de verrous de module.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a> CComPolyObject :: CreateInstance

Vous permet de créer un nouvel objet de **<CComPolyObject** `contained` **>** sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
à Pointeur vers un pointeur de **<CComPolyObject** `contained` **>** . En cas d' `CreateInstance` échec, *pp* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre de références égal à zéro, donc appelez-le `AddRef` immédiatement, puis utilisez `Release` pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans la surcharge de `CoCreateInstance` , utilisez [CComCoClass :: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a> CComPolyObject :: FinalConstruct

Appelée au cours des dernières étapes de la construction de l’objet, cette méthode effectue toute initialisation finale sur le [m_contained](#m_contained) membre de données.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a> CComPolyObject :: FinalRelease

Appelée lors de la destruction de l’objet, cette méthode libère le membre de données [m_contained](#m_contained) .

```cpp
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a> CComPolyObject :: m_contained

Objet [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) dérivé de votre classe.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*présent*<br/>
dans Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

### <a name="remarks"></a>Notes

`IUnknown` les appels via `m_contained` sont délégués à l’objet externe inconnu si l’objet est agrégé, ou au `IUnknown` de cet objet si l’objet n’est pas agrégé.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a> CComPolyObject :: QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*Question*<br/>
Interface COM.

*vaut*<br/>
dans Identificateur de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

*p*<br/>
à Pointeur vers l’interface identifiée par `__uuidof(Q)` .

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour un objet agrégé, si l’interface demandée est `IUnknown` , `QueryInterface` retourne un pointeur vers le propriétaire de l’objet agrégé `IUnknown` et incrémente le décompte de références. Sinon, cette méthode interroge l’interface par le biais du `CComContainedObject` membre de données, [m_contained](#m_contained).

## <a name="ccompolyobjectrelease"></a><a name="release"></a> CComPolyObject :: Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur renvoyée

Dans les versions Debug, `Release` retourne une valeur qui peut être utile pour les diagnostics ou les tests. Dans les versions de débogage, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
