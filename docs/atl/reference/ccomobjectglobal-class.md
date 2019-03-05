---
title: Ccomobjectglobal, classe
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: ec3abd04ce72cce98dae72a1ed8cbb8d9fe72079
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267431"
---
# <a name="ccomobjectglobal-class"></a>Ccomobjectglobal, classe

Cette classe gère un décompte de références sur le module contenant votre `Base` objet.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que toute autre interface souhaitées prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Constructeur.|
|[CComObjectGlobal::~CComObjectGlobal](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Implémente un global `AddRef`.|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implémente un global `QueryInterface`.|
|[CComObjectGlobal::Release](#release)|Implémente un global `Release`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Contient le HRESULT retourné pendant la construction de la `CComObjectGlobal` objet.|

## <a name="remarks"></a>Notes

`CComObjectGlobal` gère un décompte de références sur le module contenant votre `Base` objet. `CComObjectGlobal` garantit que votre objet ne sera pas supprimé tant que le module n’est pas libéré. Votre objet n’est supprimée que lorsque le décompte de références sur l’ensemble du module atteint zéro.

Par exemple, à l’aide de `CComObjectGlobal`, une fabrique de classe peut contenir un objet global commun qui est partagé par tous ses clients.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

Incrémente le décompte de références de l’objet de 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour les diagnostics et de test.

### <a name="remarks"></a>Notes

Par défaut, `AddRef` appels `_Module::Lock`, où `_Module` est l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée à partir de celui-ci.

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

Constructeur. Appels `FinalConstruct` et définit ensuite [m_hResFinalConstruct](#m_hresfinalconstruct) à la `HRESULT` retourné par `FinalConstruct`.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Notes

Si vous n’avez pas dérivé votre classe de base à partir de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), vous devez fournir votre propre `FinalConstruct` (méthode). Le destructeur appelle `FinalRelease`.

##  <a name="dtor"></a>  CComObjectGlobal::~CComObjectGlobal

Destructeur.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appels [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

Contient le HRESULT de l’appel `FinalConstruct` pendant la construction de la `CComObjectGlobal` objet.

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

Récupère un pointeur vers le pointeur d’interface demandé.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
[in] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Pointeur vers le pointeur d’interface identifié par iid, ou NULL si l’interface est introuvable.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`QueryInterface` gère seulement des interfaces dans le tableau de mappage COM.

##  <a name="release"></a>  CComObjectGlobal::Release

Décrémente le décompte de références de l’objet de 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions debug, `Release` retourne une valeur qui peut être utile pour les diagnostics et de test. Dans les versions non debug `Release` retourne toujours 0.

### <a name="remarks"></a>Notes

Par défaut, `Release` appels `_Module::Unlock`, où `_Module` est l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée à partir de celui-ci.

## <a name="see-also"></a>Voir aussi

[CComObjectStack, classe](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
