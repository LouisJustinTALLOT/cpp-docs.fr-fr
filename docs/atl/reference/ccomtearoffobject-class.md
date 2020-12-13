---
description: 'En savoir plus sur : classe CComTearOffObject'
title: CComTearOffObject, classe
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: b9fe9e7a790a004aec1de059415bd5f47572455b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142153"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject, classe

Cette classe implémente une interface détachée.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe détachée, dérivée de `CComTearOffObjectBase` et des interfaces que vous souhaitez que votre objet déchire prenne en charge.

ATL implémente ses interfaces détachées en deux phases : les `CComTearOffObjectBase` méthodes gèrent le nombre de références et `QueryInterface` , tandis que `CComTearOffObject` implémente [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Constructeur.|
|[CComTearOffObject :: ~ CComTearOffObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComTearOffObject :: AddRef](#addref)|Incrémente le décompte de références pour un `CComTearOffObject` objet.|
|[CComTearOffObject :: QueryInterface](#queryinterface)|Retourne un pointeur vers l’interface demandée sur votre classe détachable ou la classe propriétaire.|
|[CComTearOffObject :: Release](#release)|Décrémente le décompte de références pour un `CComTearOffObject` objet et le détruit.|

### <a name="ccomtearoffobjectbase-methods"></a>Méthodes CComTearOffObjectBase

|Fonction|Description|
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Constructeur.|

### <a name="ccomtearoffobjectbase-data-members"></a>Membres de données CComTearOffObjectBase

|Membre de données|Description|
|-|-|
|[m_pOwner](#m_powner)|Pointeur vers un `CComObject` dérivé de la classe propriétaire.|

## <a name="remarks"></a>Notes

`CComTearOffObject` implémente une interface détachée en tant qu’objet distinct qui est instancié uniquement lorsque cette interface est interrogée. La destruction est supprimée lorsque son nombre de références est égal à zéro. En règle générale, vous générez une interface détachée pour une interface rarement utilisée, car l’utilisation d’une déchirure enregistre un pointeur vtable dans toutes les instances de votre objet principal.

Vous devez dériver la classe qui implémente la déchirure à partir `CComTearOffObjectBase` et à partir des interfaces que vous souhaitez que votre objet déchire prenne en charge. `CComTearOffObjectBase` est mis en modèle sur la classe propriétaire et le modèle de thread. La classe propriétaire est la classe de l’objet pour lequel une déchirure est implémentée. Si vous ne spécifiez pas de modèle de thread, le modèle de thread par défaut est utilisé.

Vous devez créer une carte COM pour votre classe détachable. Lorsque ATL instancie la destruction, il crée `CComTearOffObject<CYourTearOffClass>` ou `CComCachedTearOffObject<CYourTearOffClass>` .

Par exemple, dans l’exemple BEEPer, la classe `CBeeper2` est la classe détachable et la `CBeeper` classe est la classe propriétaire :

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a> CComTearOffObject :: AddRef

Incrémente le décompte de références de l' `CComTearOffObject` objet d’une unité.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui peut être utile pour les diagnostics et les tests.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a> CComTearOffObject::CComTearOffObject

Constructeur.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
dans Pointeur qui sera converti en pointeur vers un `CComObject<Owner>` objet.

### <a name="remarks"></a>Notes

Incrémente de un le nombre de références du propriétaire.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a> CComTearOffObject :: ~ CComTearOffObject

Destructeur.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appelle FinalRelease et décrémente le nombre de verrous de module.

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a> CComTearOffObject::CComTearOffObjectBase

Constructeur.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Notes

Initialise le membre [m_pOwner](#m_powner) avec la valeur null.

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a> CComTearOffObject :: m_pOwner

Pointeur vers un objet [CComObject](../../atl/reference/ccomobject-class.md) dérivé de *owner*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Paramètres

*Propriétaire*<br/>
dans Classe pour laquelle un déchirement est implémenté.

### <a name="remarks"></a>Notes

Le pointeur est initialisé à la valeur NULL pendant la construction.

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a> CComTearOffObject :: QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans IID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*, ou null si l’interface est introuvable.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Interroge d’abord les interfaces sur votre classe détachée. Si l’interface n’est pas présente, interroge l’interface sur l’objet propriétaire. Si l’interface demandée est `IUnknown` , retourne le `IUnknown` du propriétaire.

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a> CComTearOffObject :: Release

Décrémente le décompte de références d’une unité et, si le nombre de références est égal à zéro, supprime le `CComTearOffObject` .

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Valeur renvoyée

Dans les versions sans débogage, retourne toujours la valeur zéro. Dans les versions Debug, retourne une valeur qui peut être utile pour les diagnostics ou les tests.

## <a name="see-also"></a>Voir aussi

[CComCachedTearOffObject, classe](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
