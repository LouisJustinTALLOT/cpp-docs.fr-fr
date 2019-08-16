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
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497136"
---
# <a name="ccomobject-class"></a>CComObject, classe

Cette classe implémente `IUnknown` pour un objet non agrégé.

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
|[CComObject::~CComObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Incrémente le décompte de références sur l’objet.|
|[CComObject::CreateInstance](#createinstance)|Statique Crée un `CComObject` objet.|
|[CComObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComObject::Release](#release)|Décrémente le décompte de références sur l’objet.|

## <a name="remarks"></a>Notes

`CComObject`implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pour un objet non agrégé. Toutefois, les appels `QueryInterface`à `AddRef`, et `Release` sont délégués à `CComObjectRootEx`.

Pour plus d’informations sur `CComObject`l’utilisation de, consultez l’article [notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObject`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="addref"></a>  CComObject::AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction retourne le nouveau nombre de références incrémentées sur l’objet. Cette valeur peut être utile pour les diagnostics ou les tests.

##  <a name="ccomobject"></a>  CComObject::CComObject

Le constructeur incrémente le nombre de verrous de module.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Paramètres

<em>void\*</em><br/>
dans Ce paramètre sans nom n’est pas utilisé. Il existe pour la symétrie avec `CComXXXObjectXXX` d’autres constructeurs.

### <a name="remarks"></a>Notes

Le destructeur le décrémente.

Si un `CComObject`objet dérivé de est correctement construit à l’aide de l’opérateur **New** , le nombre de références initiales est 0. Pour définir le décompte de références à la valeur appropriée (1), effectuez un appel à la fonction [AddRef](#addref) .

##  <a name="dtor"></a>  CComObject::~CComObject

Destructeur.

```
CComObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease)et décrémente le nombre de verrous de module.

##  <a name="createinstance"></a>  CComObject::CreateInstance

Cette fonction statique vous permet de créer un nouvel objet **CComObject <** `Base` **>** , sans la surcharge de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Paramètres

*pp*<br/>
à Pointeur vers un pointeur de **<** `Base` **>** CComObject. En `CreateInstance` cas d’échec, *pp* a la valeur null.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet retourné a un nombre de références égal à zéro, `AddRef` donc appelez-le `Release` immédiatement, puis utilisez pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.

Si vous n’avez pas besoin d’un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet `CoCreateInstance`sans la surcharge de, utilisez [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.

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

*iid*<br/>
dans Identificateur de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

*pp*<br/>
à Pointeur vers le pointeur d’interface identifié par le `Q`type. Si l’objet ne prend pas en charge cette interface, *pp* a la valeur null.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="release"></a>  CComObject::Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Cette fonction retourne le nouveau décompte de références décrémenté sur l’objet. Dans les versions Debug, la valeur de retour peut être utile pour les diagnostics ou les tests. Dans les versions sans débogage `Release` , retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
