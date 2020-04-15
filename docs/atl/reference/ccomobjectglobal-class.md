---
title: Classe CComObjectGlobal
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
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327634"
---
# <a name="ccomobjectglobal-class"></a>Classe CComObjectGlobal

Cette classe gère un compte de `Base` référence sur le module contenant votre objet.

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
|[CComObjectGlobal: CComObjectGlobal](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Mise en `AddRef`œuvre d’un global .|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Mise en `QueryInterface`œuvre d’un global .|
|[CComObjectGlobal::Libération](#release)|Mise en `Release`œuvre d’un global .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Contient le HRESULT retourné `CComObjectGlobal` pendant la construction de l’objet.|

## <a name="remarks"></a>Notes

`CComObjectGlobal`gère un compte de référence `Base` sur le module contenant votre objet. `CComObjectGlobal`s’assure que votre objet ne sera pas supprimé tant que le module n’est pas libéré. Votre objet ne sera supprimé que lorsque le compte de référence sur l’ensemble du module sera à zéro.

Par exemple, `CComObjectGlobal`l’utilisation , une usine de classe peut contenir un objet global commun qui est partagé par tous ses clients.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::AddRef

Incréments le nombre de références de l’objet par 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic et les tests.

### <a name="remarks"></a>Notes

Par `AddRef` défaut, `_Module::Lock`les `_Module` appels , où est l’exemple global de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée de celui-ci.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal

Constructeur. Appels, `FinalConstruct` puis met [m_hResFinalConstruct](#m_hresfinalconstruct) à `HRESULT` la `FinalConstruct`retournée par .

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Notes

Si vous n’avez pas dérivé votre classe de base de `FinalConstruct` [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), vous devez fournir votre propre méthode. Le destructeur appelle `FinalRelease`.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObjectGlobal: CComObjectGlobal

Destructeur.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct

Contient le HRESULT `FinalConstruct` de l’appel pendant la construction de l’objet. `CComObjectGlobal`

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObjectGlobal::QueryInterface

Récupère un pointeur sur le pointeur d’interface demandé.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface identifié par iid, ou NULL si l’interface n’est pas trouvée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`QueryInterface` gère seulement des interfaces dans le tableau de mappage COM.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObjectGlobal::Libération

Décroisse le nombre de références de l’objet par 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions `Release` de débog, retourne une valeur qui peut être utile pour le diagnostic et les tests. Dans les constructions non-debug, `Release` retourne toujours 0.

### <a name="remarks"></a>Notes

Par `Release` défaut, `_Module::Unlock`les `_Module` appels , où est l’exemple global de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée de celui-ci.

## <a name="see-also"></a>Voir aussi

[Classe CComObjectStack](../../atl/reference/ccomobjectstack-class.md)<br/>
[Classe CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Classe CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
