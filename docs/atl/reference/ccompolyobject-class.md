---
title: CComPolyObject, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec995026b0142fc30470836b29697457be91937e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764808"
---
# <a name="ccompolyobject-class"></a>CComPolyObject, classe

Cette classe implémente `IUnknown` pour un objet regroupé ou.

## <a name="syntax"></a>Syntaxe

```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Paramètres

*contenu*  
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bien que toutes les autres interfaces souhaitées prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Constructeur.|
|[CComPolyObject :: ~ CComPolyObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Incrémente le décompte de références de l’objet.|
|[CComPolyObject::CreateInstance](#createinstance)|(Statique) Vous permet de créer un nouveau **CComPolyObject <** `contained` **>** objet sans la surcharge de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Effectue l’initialisation finale de `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Effectue une destruction finale des `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComPolyObject::Release](#release)|Décrémente de nombre de référence de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Délégués `IUnknown` appelle à inconnu externe si l’objet est agrégée ou à la `IUnknown` de l’objet si l’objet n’est pas agrégée.|

## <a name="remarks"></a>Notes

`CComPolyObject` implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pour un objet regroupé ou.

Lorsqu’une instance de `CComPolyObject` est créé, la valeur de l’élément externe inconnu est activée. Si sa valeur est NULL, `IUnknown` est implémentée pour un objet non regroupées en agrégats. Si l’inconnu extérieur n’est pas NULL, `IUnknown` est implémentée pour un objet agrégé.

L’avantage d’utiliser `CComPolyObject` est d’éviter d’avoir à la fois [CComAggObject](../../atl/reference/ccomaggobject-class.md) et [CComObject](../../atl/reference/ccomobject-class.md) dans votre module pour gérer les cas regroupés et. Un seul `CComPolyObject` objet gère les deux cas. Cela ne signifie qu’une seule copie de vtable et une seule copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, à l’aide de `CComPolyObject` peut entraîner une taille légèrement supérieure de module, car elle n’est pas optimisée pour un objet regroupé ou, comme le sont `CComAggObject` et `CComObject`.

Si la macro DECLARE_POLY_AGGREGATABLE est spécifiée dans la définition de classe de votre objet, `CComPolyObject` doit être utilisé pour créer votre objet. DECLARE_POLY_AGGREGATABLE sera déclarée automatiquement si vous utilisez l’Assistant Projet ATL pour créer un contrôle total ou le contrôle d’Internet Explorer.

Si agrégée, la `CComPolyObject` objet possède son propre `IUnknown`, indépendamment de l’objet externe `IUnknown`et gère son propre nombre de références. `CComPolyObject` utilise [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) pour déléguer à inconnu externe.

Pour plus d’informations sur l’agrégation, consultez l’article [principes de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComPolyObject::AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut-être être utiles pour le diagnostic ou de test.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

Constructeur.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*PV*  
[in] Un pointeur vers l’inconnu externe si l’objet doit être agrégées, ou NULL si l’objet si l’objet n’est pas agrégée.

### <a name="remarks"></a>Notes

Initialise le `CComContainedObject` membre de données, [m_contained](#m_contained)et incrémente le nombre de verrous du module.

Le destructeur décrémente le module nombre de verrous.

##  <a name="dtor"></a>  CComPolyObject :: ~ CComPolyObject

Destructeur.

```
~CComPolyObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appels [FinalRelease](#finalrelease), et décrémente le module nombre de verrous.

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

Vous permet de créer un nouveau **CComPolyObject <** `contained` **>** objet sans la surcharge de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Paramètres

*PP*  
[out] Un pointeur vers un **CComPolyObject <** `contained` **>** pointeur. Si `CreateInstance` échoue, *pp* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné est un décompte de références de zéro, appelez `AddRef` immédiatement, utilisez `Release` pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.

Si vous n’avez besoin un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans la surcharge de `CoCreateInstance`, utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Appelée au cours des dernières étapes de la construction d’objet, cette méthode exécute toute initialisation finale sur le [m_contained](#m_contained) membre de données.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

Appelé lors de la destruction d’objets, cette méthode libère le [m_contained](#m_contained) membre de données.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objet dérivé de votre classe.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Paramètres

*contenu*  
[in] Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bien que toutes les autres interfaces souhaitées prendre en charge sur l’objet.

### <a name="remarks"></a>Notes

`IUnknown` appelle via `m_contained` sont déléguées à inconnu externe si l’objet est agrégée, ou à la `IUnknown` de cet objet si l’objet n’est pas agrégée.

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*Q*  
L’interface COM.

*IID*  
[in] L’identificateur de l’interface demandée.

*ppvObject*  
[out] Un pointeur vers le pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est définie sur NULL.

*PP*  
[out] Un pointeur vers l’interface identifiée par `__uuidof(Q)`.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour un objet, si l’interface demandée est `IUnknown`, `QueryInterface` retourne un pointeur vers l’agrégées propre à l’objet `IUnknown` et incrémente le décompte de références. Sinon, cette méthode exécute une requête pour l’interface via la `CComContainedObject` membre de données, [m_contained](#m_contained).

##  <a name="release"></a>  CComPolyObject::Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions debug, `Release` retourne une valeur qui peut-être être utiles pour le diagnostic ou de test. Dans les versions non Debug, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)   
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
