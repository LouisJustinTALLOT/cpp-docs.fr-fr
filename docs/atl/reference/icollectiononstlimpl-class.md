---
description: 'En savoir plus sur : ICollectionOnSTLImpl, classe'
title: ICollectionOnSTLImpl, classe
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
ms.openlocfilehash: 089fc0fbd8f410d740646e2a653b076d32448647
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139604"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl, classe

Cette classe fournit des méthodes utilisées par une classe de collection.

## <a name="syntax"></a>Syntaxe

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Interface de collection COM.

*CollType*<br/>
Classe de conteneur de la bibliothèque standard C++.

*itemType*<br/>
Type d’élément exposé par l’interface de conteneur.

*CopyItem*<br/>
[Classe de stratégie de copie](../../atl/atl-copy-policy-classes.md).

*EnumType*<br/>
Classe d’énumérateur compatible [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md).

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ICollectionOnSTLImpl :: get__NewEnum](#newenum)|Retourne un objet énumérateur pour la collection.|
|[ICollectionOnSTLImpl :: GetCount](#get_count)|Retourne le nombre d’éléments dans la collection.|
|[ICollectionOnSTLImpl :: get_Item](#get_item)|Retourne l’élément demandé de la collection.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[ICollectionOnSTLImpl :: m_coll](#m_coll)|Collection.|

## <a name="remarks"></a>Notes

Cette classe fournit l’implémentation pour trois méthodes d’une interface de collection : [GetCount](#get_count), [get_Item](#get_item)et [get__NewEnum](#newenum).

Pour utiliser cette classe :

- Définissez (ou empruntez) une interface de collection que vous souhaitez implémenter.

- Dérivez votre classe d’une spécialisation `ICollectionOnSTLImpl` basée sur cette interface de collection.

- Utilisez votre classe dérivée pour implémenter toutes les méthodes de l’interface de collection non gérée par `ICollectionOnSTLImpl` .

> [!NOTE]
> Si l’interface de collection est une interface double, dérivez votre classe de [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), en passant la `ICollectionOnSTLImpl` spécialisation comme premier paramètre de modèle si vous souhaitez que ATL fournisse l’implémentation des `IDispatch` méthodes.

- Ajoutez des éléments au membre [m_coll](#m_coll) pour remplir la collection.

Pour plus d’informations et d’exemples, consultez [collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a> ICollectionOnSTLImpl :: GetCount

Cette méthode retourne le nombre d’éléments dans la collection.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Paramètres

*pcount*<br/>
à Nombre d’éléments dans la collection.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a> ICollectionOnSTLImpl :: get_Item

Cette méthode retourne l’élément spécifié de la collection.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Paramètres

*Index*<br/>
dans Index de base 1 d’un élément dans la collection.

*pvar*<br/>
à Élément correspondant à l' *index*.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’élément est obtenu en copiant les données à la position spécifiée dans [m_coll](#m_coll) à l’aide de la méthode de copie de la [classe de stratégie de copie](../../atl/atl-copy-policy-classes.md) passée comme argument de modèle dans la `ICollectionOnSTLImpl` spécialisation.

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a> ICollectionOnSTLImpl :: get__NewEnum

Retourne un objet énumérateur pour la collection.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Paramètres

*ppUnk*<br/>
à Pointeur **IUnknown** d’un objet énumérateur nouvellement créé.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’énumérateur nouvellement créé maintient un itérateur sur la collection d’origine, `m_coll` , (donc aucune copie n’est effectuée) et contient une référence com sur l’objet de collection pour garantir que la collection reste active alors qu’il existe des énumérateurs en attente.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a> ICollectionOnSTLImpl :: m_coll

Ce membre contient les éléments représentés par la collection.

```
CollType m_coll;
```

## <a name="see-also"></a>Voir aussi

[Exemple ATLCollections](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
