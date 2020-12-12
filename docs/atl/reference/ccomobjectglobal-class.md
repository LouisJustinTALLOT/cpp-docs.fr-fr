---
description: 'En savoir plus sur : classe CComObjectGlobal'
title: CComObjectGlobal, classe
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
ms.openlocfilehash: 0f79acb0fdbb43f9456e08f26875d45eec9904c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151981"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal, classe

Cette classe gère un décompte de références sur le module contenant votre `Base` objet.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toute autre interface que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Constructeur.|
|[CComObjectGlobal :: ~ CComObjectGlobal](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal :: AddRef](#addref)|Implémente un global `AddRef` .|
|[CComObjectGlobal :: QueryInterface](#queryinterface)|Implémente un global `QueryInterface` .|
|[CComObjectGlobal :: Release](#release)|Implémente un global `Release` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal :: m_hResFinalConstruct](#m_hresfinalconstruct)|Contient le HRESULT retourné pendant la construction de l' `CComObjectGlobal` objet.|

## <a name="remarks"></a>Notes

`CComObjectGlobal` gère un décompte de références sur le module contenant votre `Base` objet. `CComObjectGlobal` garantit que votre objet ne sera pas supprimé tant que le module n’est pas libéré. Votre objet sera supprimé uniquement lorsque le nombre de références sur l’ensemble du module passe à zéro.

Par exemple, à l’aide de `CComObjectGlobal` , une fabrique de classe peut contenir un objet global commun qui est partagé par tous ses clients.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a> CComObjectGlobal :: AddRef

Incrémente le décompte de références de l’objet de 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics et les tests.

### <a name="remarks"></a>Notes

Par défaut, `AddRef` appelle `_Module::Lock` , où `_Module` est l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée de celle-ci.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a> CComObjectGlobal::CComObjectGlobal

Constructeur. Appelle `FinalConstruct` , puis définit [m_hResFinalConstruct](#m_hresfinalconstruct) sur le `HRESULT` retourné par `FinalConstruct` .

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Notes

Si vous n’avez pas dérivé votre classe de base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), vous devez fournir votre propre `FinalConstruct` méthode. Le destructeur appelle `FinalRelease`.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a> CComObjectGlobal :: ~ CComObjectGlobal

Destructeur.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a> CComObjectGlobal :: m_hResFinalConstruct

Contient le HRESULT de l’appel `FinalConstruct` pendant la construction de l' `CComObjectGlobal` objet.

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a> CComObjectGlobal :: QueryInterface

Récupère un pointeur vers le pointeur d’interface demandé.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par IID, ou NULL si l’interface est introuvable.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`QueryInterface` gère seulement des interfaces dans le tableau de mappage COM.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a> CComObjectGlobal :: Release

Décrémente le décompte de références de l’objet de 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur renvoyée

Dans les versions Debug, `Release` retourne une valeur qui peut être utile pour les diagnostics et les tests. Dans les versions sans débogage, `Release` retourne toujours 0.

### <a name="remarks"></a>Notes

Par défaut, `Release` appelle `_Module::Unlock` , où `_Module` est l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée de celle-ci.

## <a name="see-also"></a>Voir aussi

[CComObjectStack, classe](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
