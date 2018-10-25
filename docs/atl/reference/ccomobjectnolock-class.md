---
title: Ccomobjectnolock, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45bb74921693b4f033fbff578a12c980816a6aea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083384"
---
# <a name="ccomobjectnolock-class"></a>Ccomobjectnolock, classe

Cette classe implémente `IUnknown` pour un objet non regroupées en agrégats, mais ne pas incrémenter le module nombre de verrous dans le constructeur.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Paramètres

*base de*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que toute autre interface souhaitées prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructeur.|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|Incrémente le décompte de références sur l’objet.|
|[CComObjectNoLock::QueryInterface](#queryinterface)|Retourne un pointeur vers l’interface demandée.|
|[CComObjectNoLock::Release](#release)|Décrémente le décompte de références sur l’objet.|

## <a name="remarks"></a>Notes

`CComObjectNoLock` est similaire à [CComObject](../../atl/reference/ccomobject-class.md) car il implémente [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pour un objet non regroupées en agrégats ; Toutefois, `CComObjectNoLock` ne pas incrémenter le verrou du module compte dans le constructeur.

ATL utilise `CComObjectNoLock` en interne pour les fabriques de classes. En règle générale, vous ne serez pas utiliser cette classe directement.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

Incrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut-être être utiles pour le diagnostic ou de test.

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

Constructeur. Contrairement aux [CComObject](../../atl/reference/ccomobject-class.md), n’incrémente pas le nombre de verrous du module.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Paramètres

<em>void\*</em><br/>
[in] Ce paramètre sans nom n’est pas utilisé. Il existe pour la symétrie avec d’autres `CComXXXObjectXXX` constructeurs.

##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock

Destructeur.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appels [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*IID*<br/>
[in] L’identificateur de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="release"></a>  CComObjectNoLock::Release

Décrémente le décompte de références sur l’objet.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Dans les versions debug, `Release` retourne une valeur qui peut-être être utiles pour le diagnostic ou de test. Dans les versions non debug `Release` retourne toujours 0.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
