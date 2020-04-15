---
title: Classe ICollectionOnSTLImpl
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329910"
---
# <a name="icollectiononstlimpl-class"></a>Classe ICollectionOnSTLImpl

Cette classe fournit des méthodes utilisées par une classe de collecte.

## <a name="syntax"></a>Syntaxe

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Une interface de collection COM.

*CollType CollType*<br/>
Une classe de conteneurs de la Bibliothèque Standard.

*itemType*<br/>
Le type d’article exposé par l’interface du conteneur.

*CopyItem (en anglais)*<br/>
Une [classe de police de copie](../../atl/atl-copy-policy-classes.md).

*Enumtype*<br/>
Une classe d’enumérateur [compatible CComEnumOnSTL.](../../atl/reference/ccomenumonstl-class.md)

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Retourne un objet d’enumérateur pour la collection.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Retourne le nombre d’éléments de la collection.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Renvoie l’article demandé de la collection.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|Collection.|

## <a name="remarks"></a>Notes

Cette classe fournit la mise en œuvre de trois méthodes d’une interface de collecte: [getcount](#get_count), [get_Item](#get_item), et [get__NewEnum](#newenum).

Pour utiliser cette classe :

- Définissez (ou empruntez) une interface de collection que vous souhaitez implémenter.

- Dérivez votre classe d’une spécialisation de basé sur cette interface de `ICollectionOnSTLImpl` collection.

- Utilisez votre classe dérivée pour implémenter `ICollectionOnSTLImpl`toutes les méthodes de l’interface de collecte non gérée par .

> [!NOTE]
> Si l’interface de collection est une double interface, dérivez `ICollectionOnSTLImpl` votre classe [d’IDispatchImpl](../../atl/reference/idispatchimpl-class.md), en passant `IDispatch` la spécialisation comme le premier paramètre de modèle si vous voulez ATL pour fournir la mise en œuvre des méthodes.

- Ajoutez des articles au [membre m_coll](#m_coll) pour remplir la collection.

Pour plus d’informations et d’exemples, voir [ATL Collections et Enumerators](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectionOnSTLImpl::getcount

Cette méthode renvoie le nombre d’articles de la collection.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Paramètres

*pcount*<br/>
[out] Le nombre d’éléments de la collection.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectionOnSTLImpl::get_Item

Cette méthode renvoie l’élément spécifié de la collection.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Paramètres

*Index*<br/>
[dans] L’index à 1 base d’un élément de la collection.

*pvar pvar*<br/>
[out] L’élément correspondant à *l’indice*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’élément est obtenu en copiant les données à la position spécifiée dans [m_coll](#m_coll) en utilisant `ICollectionOnSTLImpl` la méthode de copie de la classe de politique de [copie](../../atl/atl-copy-policy-classes.md) adoptée comme un argument de modèle dans la spécialisation.

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectionOnSTLImpl::get__NewEnum

Retourne un objet d’enumérateur pour la collection.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Paramètres

*ppUnk*<br/>
[out] Le pointeur **IUnknown** d’un objet d’enumérateur nouvellement créé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’enumérateur nouvellement créé maintient un itérateur sur la collection originale, `m_coll`(donc aucune copie n’est faite) et détient une référence COM sur l’objet de collection pour s’assurer que la collection reste vivante alors qu’il ya des enumérateurs exceptionnels.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectionOnSTLImpl::m_coll

Ce membre détient les articles représentés par la collection.

```
CollType m_coll;
```

## <a name="see-also"></a>Voir aussi

[Échantillon d’ATLCollections](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
