---
title: CComObject, classe
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: 57c054915ce98dd8cff6bb772cdd40f4b0f2b768
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660471"
---
# <a name="ccomobject-class"></a>CComObject, classe

Cette classe implémente `IUnknown` pour un objet non regroupées en agrégats.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Paramètres

*base de*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bien que toutes les autres interfaces souhaitées prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|Constructeur.|
|[CComObject::~CComObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Incrémente le décompte de références sur l’objet.|
|[CComObject::CreateInstance](#createinstance)|(Statique) Crée un nouveau `CComObject` objet.|
|[CComObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComObject::Release](#release)|Décrémente le décompte de références sur l’objet.|

## <a name="remarks"></a>Notes

`CComObject` implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pour un objet non regroupées en agrégats. Toutefois, les appels à `QueryInterface`, `AddRef`, et `Release` sont déléguées à `CComObjectRootEx`.

Pour plus d’informations sur l’utilisation de `CComObject`, consultez l’article [principes de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObject`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComObject::AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction retourne le nouveau décompte de références incrémenté sur l’objet. Cette valeur peut être utile pour le test ou de diagnostics.

##  <a name="ccomobject"></a>  CComObject::CComObject

Le constructeur incrémente le nombre de verrous du module.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Paramètres

<em>void\*</em><br/>
[in] Ce paramètre sans nom n’est pas utilisé. Il existe pour la symétrie avec d’autres `CComXXXObjectXXX` constructeurs.

### <a name="remarks"></a>Notes

Le destructeur décrémente il.

Si un `CComObject`-objet dérivé est construit correctement à l’aide de la **nouveau** opérateur, le nombre de référence initiale est 0. Pour définir le nombre de références à la valeur appropriée (1), effectuez un appel à la [AddRef](#addref) (fonction).

##  <a name="dtor"></a>  CComObject::~CComObject

Destructeur.

```
CComObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appels [FinalRelease](ccomobjectrootex-class.md#finalrelease), et décrémente le module nombre de verrous.

##  <a name="createinstance"></a>  CComObject::CreateInstance

Cette fonction statique vous permet de créer un nouveau **CComObject <** `Base` **>** objet, sans la surcharge de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Paramètres

*PP*<br/>
[out] Un pointeur vers un **CComObject <** `Base` **>** pointeur. Si `CreateInstance` échoue, *pp* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné est un décompte de références de zéro, appelez `AddRef` immédiatement, utilisez `Release` pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.

Si vous ne pas nécessitant un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans la surcharge de `CoCreateInstance`, utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*IID*<br/>
[in] L’identificateur de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est définie sur NULL.

*PP*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par le type `Q`. Si l’objet ne prend pas en charge cette interface, *pp* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="release"></a>  CComObject::Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction retourne le nouveau décompte de références décrémenté sur l’objet. Dans les versions debug, la valeur de retour peut être utile pour les diagnostics ou de test. Dans les versions non debug `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
