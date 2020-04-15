---
title: Classe CComContainedObject
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
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320797"
---
# <a name="ccomcontainedobject-class"></a>Classe CComContainedObject

Cette classe met en œuvre [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en `IUnknown`déléguant à l’objet du propriétaire .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Constructeur. Initialise le pointeur du membre `IUnknown`à l’objet du propriétaire .|
|[CComContainedObject::CComContainedObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Incréments le compte de référence sur l’objet propriétaire.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Récupère l’objet du `IUnknown`propriétaire .|
|[CComContainedObject::QueryInterface](#queryinterface)|Récupère un pointeur sur l’interface demandée sur l’objet propriétaire.|
|[CComContainedObject::Libération](#release)|Décroisse le compte de référence sur l’objet propriétaire.|

## <a name="remarks"></a>Notes

ATL `CComContainedObject` utilise dans les classes [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), et [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en déléguant `IUnknown`à l’objet du propriétaire . (Le propriétaire est soit l’objet extérieur d’une agrégation, soit l’objet pour lequel une interface de déchirure est créée.) `CComContainedObject` appels `CComObjectRootEx` `OuterQueryInterface`, `OuterAddRef`, `OuterRelease`et , `Base`tous hérités à travers .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComContainedObject`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef

Incréments le compte de référence sur l’objet propriétaire.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

Constructeur.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
[dans] L’objet du `IUnknown`propriétaire .

### <a name="remarks"></a>Notes

Définit `m_pOuterUnknown` le pointeur membre `Base` (hérité par la classe) à *pv*.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComContainedObject::CComContainedObject

Destructeur.

```
~CComContainedObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

Retourne `m_pOuterUnknown` le pointeur membre (hérité par la classe `IUnknown` *de base)* qui détient l’objet du propriétaire .

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Valeur de retour

L’objet du `IUnknown`propriétaire .

### <a name="remarks"></a>Notes

Cette méthode peut `Base` être virtuelle si a déclaré le [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) macro.

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComContainedObject::QueryInterface

Récupère un pointeur sur l’interface demandée sur l’objet propriétaire.

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

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Libération

Décroisse le compte de référence sur l’objet propriétaire.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions `Release` de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests. Dans les constructions non-debug, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
