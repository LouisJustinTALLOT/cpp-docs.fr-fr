---
title: Classe CComObject
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
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327647"
---
# <a name="ccomobject-class"></a>Classe CComObject

Cette classe `IUnknown` met en œuvre pour un objet non agrégaté.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|Constructeur.|
|[CComObject: CComObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Incréments le compte de référence sur l’objet.|
|[CComObject::CréerInstance](#createinstance)|(Statique) Crée un `CComObject` nouvel objet.|
|[CComObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComObject::Libération](#release)|Décroisse le compte de référence sur l’objet.|

## <a name="remarks"></a>Notes

`CComObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet non agrégaté. Cependant, les `QueryInterface` `AddRef`appels `Release` à , `CComObjectRootEx`, et sont délégués à .

Pour plus d’informations sur l’utilisation `CComObject`, voir l’article [Fondamentaux de ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObject`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject::AddRef

Incréments le compte de référence sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction renvoie le nouveau nombre de références incrémentés sur l’objet. Cette valeur peut être utile pour le diagnostic ou les tests.

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject::CComObject

Le constructeur incrémente le nombre de serrures du module.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Paramètres

<em>void\*</em><br/>
[dans] Ce paramètre anonyme n’est pas utilisé. Il existe pour la symétrie avec d’autres `CComXXXObjectXXX` constructeurs.

### <a name="remarks"></a>Notes

Le destructeur le décréd.

Si `CComObject`un objet dérivé est construit avec succès à l’aide du **nouvel** opérateur, le nombre de références initiale est de 0. Pour définir le nombre de références à la valeur appropriée (1), faites un appel à la fonction [AddRef.](#addref)

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CComObject: CComObject

Destructeur.

```
CComObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources [allouées, appelle FinalRelease](ccomobjectrootex-class.md#finalrelease)et décrète le nombre de verrous du module.

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CréerInstance

Cette fonction statique vous permet de créer un nouvel `Base` **>** objet **CComObject<,** sans les frais généraux de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Paramètres

*Pp*<br/>
[out] Un pointeur à un `Base` **>** **pointeur de<CComObject.** En `CreateInstance` cas d’échec, *pp* est réglé à NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre `AddRef` de références `Release` de zéro, alors appelez immédiatement, puis utilisez pour libérer la référence sur le pointeur de l’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans frais généraux, `CoCreateInstance`utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject::Libération

Décroisse le compte de référence sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction renvoie le nouveau compte de référence décrément sur l’objet. Dans les constructions de débog, la valeur de retour peut être utile pour le diagnostic ou les tests. Dans les constructions non-debug, `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Classe CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Classe CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
