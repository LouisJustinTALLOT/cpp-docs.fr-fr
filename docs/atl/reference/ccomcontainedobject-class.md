---
title: Ccomcontainedobject, classe
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 15ea9be2a3576081901c9e744d89d33688fe838a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273580"
---
# <a name="ccomcontainedobject-class"></a>Ccomcontainedobject, classe

Cette classe implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) par délégation à l’objet propriétaire `IUnknown`.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Constructeur. Initialise le pointeur de membre à l’objet propriétaire `IUnknown`.|
|[CComContainedObject::~CComContainedObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Incrémente le décompte de références sur l’objet propriétaire.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Récupère l’objet propriétaire `IUnknown`.|
|[CComContainedObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l’interface demandée sur l’objet propriétaire.|
|[CComContainedObject::Release](#release)|Décrémente le décompte de références sur l’objet propriétaire.|

## <a name="remarks"></a>Notes

ATL utilise `CComContainedObject` dans les classes [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), et [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject` implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) par délégation à l’objet propriétaire `IUnknown`. (Le propriétaire est l’objet externe d’une agrégation ou de l’objet pour lequel une interface détachable est créée.) `CComContainedObject` appels `CComObjectRootEx`de `OuterQueryInterface`, `OuterAddRef`, et `OuterRelease`, hérités via `Base`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComContainedObject`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComContainedObject::AddRef

Incrémente le décompte de références sur l’objet propriétaire.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut-être être utiles pour le diagnostic ou de test.

##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject

Constructeur.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*pv*<br/>
[in] L’objet propriétaire `IUnknown`.

### <a name="remarks"></a>Notes

Définit le `m_pOuterUnknown` pointeur de membre (héritées par le biais du `Base` classe) à *pv*.

##  <a name="dtor"></a>  CComContainedObject::~CComContainedObject

Destructeur.

```
~CComContainedObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown

Retourne le `m_pOuterUnknown` pointeur de membre (héritées par le biais du *Base* classe) qui contient l’objet propriétaire `IUnknown`.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Valeur de retour

L’objet propriétaire `IUnknown`.

### <a name="remarks"></a>Notes

Cette méthode peut être virtuelle si `Base` a déclaré le [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) (macro).

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

Récupère un pointeur vers l’interface demandée sur l’objet propriétaire.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
[in] L’identificateur de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est définie sur NULL.

*pp*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par le type `Q`. Si l’objet ne prend pas en charge cette interface, *pp* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="release"></a>  CComContainedObject::Release

Décrémente le décompte de références sur l’objet propriétaire.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions debug, `Release` retourne une valeur qui peut-être être utiles pour le diagnostic ou de test. Dans les versions non debug `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
