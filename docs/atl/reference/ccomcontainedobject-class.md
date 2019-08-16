---
title: CComContainedObject, classe
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
ms.openlocfilehash: c5e2fa64cc0938e632a37eac7dd1d6e9111c3d98
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497317"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject, classe

Cette classe implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en déléguant au de `IUnknown`l’objet propriétaire.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Constructeur. Initialise le pointeur membre vers le de `IUnknown`l’objet propriétaire.|
|[CComContainedObject:: ~ CComContainedObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Incrémente le décompte de références sur l’objet propriétaire.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Récupère le de `IUnknown`l’objet propriétaire.|
|[CComContainedObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l’interface demandée sur l’objet propriétaire.|
|[CComContainedObject::Release](#release)|Décrémente le décompte de références sur l’objet propriétaire.|

## <a name="remarks"></a>Notes

ATL utilise `CComContainedObject` dans les classes [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)et [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en déléguant aux objets de `IUnknown`propriétaire. (Le propriétaire est soit l’objet externe d’une agrégation, soit l’objet pour lequel une interface détachée est créée.) lesappels`CComObjectRootEx`, `OuterQueryInterface` ,et`OuterRelease`, sont tous hérités`Base`de. `OuterAddRef` `CComContainedObject`

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComContainedObject`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="addref"></a>  CComContainedObject::AddRef

Incrémente le décompte de références sur l’objet propriétaire.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics ou les tests.

##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject

Constructeur.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*pv*<br/>
dans De `IUnknown`l’objet propriétaire.

### <a name="remarks"></a>Notes

Définit le `m_pOuterUnknown` pointeur de membre (hérité via `Base` la classe) sur *PV*.

##  <a name="dtor"></a>  CComContainedObject::~CComContainedObject

Destructeur.

```
~CComContainedObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown

Retourne le `m_pOuterUnknown` pointeur membre (hérité par le biais de la classe de *base* ) qui contient `IUnknown`le de l’objet propriétaire.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Valeur de retour

De `IUnknown`l’objet propriétaire.

### <a name="remarks"></a>Notes

Cette méthode peut être virtuelle si `Base` a déclaré la macro [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) .

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

Récupère un pointeur vers l’interface demandée sur l’objet propriétaire.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
dans Identificateur de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

*pp*<br/>
à Pointeur vers le pointeur d’interface identifié par le `Q`type. Si l’objet ne prend pas en charge cette interface, *pp* a la valeur null.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="release"></a>  CComContainedObject::Release

Décrémente le décompte de références sur l’objet propriétaire.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions Debug `Release` , retourne une valeur qui peut être utile pour les diagnostics ou les tests. Dans les versions sans débogage `Release` , retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
