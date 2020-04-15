---
title: Classe CComTearOffObject
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
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327323"
---
# <a name="ccomtearoffobject-class"></a>Classe CComTearOffObject

Cette classe met en œuvre une interface déchirante.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe de déchirure, `CComTearOffObjectBase` dérivée et les interfaces que vous voulez que votre objet de déchirure à prendre en charge.

ATL implémente ses interfaces déchirantes `CComTearOffObjectBase` en deux phases `QueryInterface`— `CComTearOffObject` les méthodes gèrent le nombre de références et, tandis que les impléments [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Constructeur.|
|[CComTearOffObject: :CComTearOffObject](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Incréments le nombre `CComTearOffObject` de références pour un objet.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Retourne un pointeur à l’interface demandée sur votre classe de déchirure ou la classe propriétaire.|
|[CComTearOffObject::Libération](#release)|Décrément le nombre de `CComTearOffObject` références pour un objet et le détruit.|

### <a name="ccomtearoffobjectbase-methods"></a>Méthodes CComTearOffObjectBase

|||
|-|-|
|[CComTearOffObjectBase (en)](#ccomtearoffobjectbase)|Constructeur.|

### <a name="ccomtearoffobjectbase-data-members"></a>Membres CComTearOffObjectBase Data

|||
|-|-|
|[m_pOwner](#m_powner)|Un pointeur `CComObject` à un dérivé de la classe propriétaire.|

## <a name="remarks"></a>Notes

`CComTearOffObject`implémente une interface déchirante comme un objet séparé qui n’est instantané que lorsque cette interface est interrogée. La déchirure est supprimée lorsque son nombre de références devient nul. Typiquement, vous construisez une interface déchirante pour une interface qui est rarement utilisée, puisque l’utilisation d’une déchirure enregistre un pointeur vtable dans tous les cas de votre objet principal.

Vous devez tirer la classe implémenter la déchirure et `CComTearOffObjectBase` à partir des interfaces que vous voulez que votre objet de déchirure à prendre en charge. `CComTearOffObjectBase`est templatisé sur la classe propriétaire et le modèle de thread. La classe propriétaire est la classe de l’objet pour lequel une déchirure est mise en œuvre. Si vous ne spécifiez pas un modèle de thread, le modèle de thread par défaut est utilisé.

Vous devez créer une carte COM pour votre classe de déchirure. Lorsque ATL instantanéiates la déchirure, `CComTearOffObject<CYourTearOffClass>` il `CComCachedTearOffObject<CYourTearOffClass>`va créer ou .

Par exemple, dans l’échantillon `CBeeper2` BEEPER, la classe `CBeeper` est la classe de déchirure et la classe est la classe propriétaire:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearOffObject::AddRef

Incréments le nombre `CComTearOffObject` de références de l’objet par un.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic et les tests.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

Constructeur.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
[dans] Pointeur qui sera converti en `CComObject<Owner>` pointeur en un objet.

### <a name="remarks"></a>Notes

Incréments le nombre de références du propriétaire par un.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComTearOffObject: :CComTearOffObject

Destructeur.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées, appelle FinalRelease et décrète le nombre de verrous du module.

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

Constructeur.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Notes

Initialise le [m_pOwner](#m_powner) membre de NULL.

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearOffObject::m_pOwner

Un pointeur à un objet [CComObject](../../atl/reference/ccomobject-class.md) dérivé du *propriétaire*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Paramètres

*Propriétaire*<br/>
[dans] La classe pour laquelle une déchirure est mise en œuvre.

### <a name="remarks"></a>Notes

Le pointeur est paralysé à NULL pendant la construction.

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComTearOffObject::QueryInterface

Récupère un pointeur vers l'interface demandée.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] L’IID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface identifié par *iid*, ou NULL si l’interface n’est pas trouvée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Questions d’abord pour les interfaces sur votre classe de déchirure. Si l’interface n’est pas là, les requêtes pour l’interface sur l’objet propriétaire. Si l’interface `IUnknown`demandée `IUnknown` est, retourne le du propriétaire.

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearOffObject::Libération

Décrément le nombre de références par un et, si `CComTearOffObject`le nombre de références est nul, supprime le .

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Valeur de retour

Dans les constructions non-debug, retourne toujours zéro. Dans les constructions de débog, retourne une valeur qui peut être utile pour le diagnostic ou les tests.

## <a name="see-also"></a>Voir aussi

[Classe CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
