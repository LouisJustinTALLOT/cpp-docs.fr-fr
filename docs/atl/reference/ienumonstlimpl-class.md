---
title: Classe IEnumOnSTLImpl
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329712"
---
# <a name="ienumonstlimpl-class"></a>Classe IEnumOnSTLImpl

Cette classe définit une interface d’enumérateur basée sur une collection de bibliothèque standard.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Un enumérateur COM. Voir [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) pour un exemple.

*piid*<br/>
Un pointeur à l’interface ID de l’interface d’enumérateur.

*T*<br/>
Le type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Une [classe de police de copie](../../atl/atl-copy-policy-classes.md).

*CollType CollType*<br/>
Une classe de conteneurs de la Bibliothèque Standard.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|La mise en œuvre de **Clone**.|
|[IEnumOnSTLImpl::Init](#init)|Initialise l'énumérateur.|
|[IEnumOnSTLImpl::Suivant](#next)|La mise en œuvre de **Next**.|
|[IEnumOnSTLImpl::Reset](#reset)|La mise en œuvre de **Reset**.|
|[IEnumOnSTLImpl::Skip](#skip)|La mise en œuvre de **Skip**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|L’itérateur qui représente la position actuelle de l’énumérateur au sein de la collection.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Un pointeur sur le contenant de la Bibliothèque standard CMD contenant les articles à énumérer.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|Le `IUnknown` pointeur de l’objet fournissant la collection.|

## <a name="remarks"></a>Notes

`IEnumOnSTLImpl`fournit la mise en œuvre d’une interface d’enumérateur COM où les éléments énumérés sont stockés dans un conteneur compatible avec la Bibliothèque standard. Cette classe est analogue à la classe [CComEnumImpl,](../../atl/reference/ccomenumimpl-class.md) qui fournit une implémentation pour une interface d’enumérateur basée sur un tableau.

> [!NOTE]
> Voir [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) pour plus de `CComEnumImpl` `IEnumOnSTLImpl`détails sur d’autres différences entre et .

Typiquement, vous *n’aurez pas* besoin de créer votre propre classe d’énumérateur en tirant de cette implémentation d’interface. Si vous souhaitez utiliser un enumérateur fourni par ATL sur la base d’un conteneur de bibliothèque standard, il est plus courant de créer une instance de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), ou de créer une classe de collecte qui renvoie un enumérateur en provenant [d’ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).

Toutefois, si vous avez besoin de fournir un enumérateur personnalisé (par exemple, celui qui expose les interfaces en plus de l’interface d’enumérateur), vous pouvez tirer de cette classe. Dans cette situation, il est probable que vous aurez besoin de remplacer la méthode [Clone](#clone) pour fournir votre propre implémentation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumOnSTLImpl::Init

Initialise l'énumérateur.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Paramètres

*pUnkForRelease*<br/>
[dans] Le `IUnknown` pointeur d’un objet qui doit être maintenu en vie pendant toute la durée de vie de l’énumérateur. Passer NULL si aucun objet de ce genre n’existe.

*Collection*<br/>
Une référence au conteneur de la Bibliothèque standard CMD qui contient les articles à énumérer.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si vous `Init` passez une référence à une collection détenue dans un autre objet, vous pouvez utiliser le paramètre *pUnkForRelease* pour vous assurer que l’objet, et la collection qu’il détient, est disponible aussi longtemps que l’enumérateur en a besoin.

Vous devez appeler cette méthode avant de passer un pointeur à l’interface d’enumérateur de retour à tous les clients.

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumOnSTLImpl::Clone

Cette méthode fournit la **Clone** mise en œuvre `CComEnumOnSTL`de la méthode Clone en créant un objet de type, en l’initialisant avec la même collection et l’itérateur utilisé par l’objet actuel, et en retournant l’interface sur l’objet nouvellement créé.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Paramètres

*ppEnum*<br/>
[out] L’interface d’enumérateur sur un objet nouvellement créé cloné à partir de l’enumérateur actuel.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

Le `IUnknown` pointeur de l’objet fournissant la collection.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Notes

Ce pointeur intelligent maintient une référence sur l’objet passé à [IEnumOnSTLImpl::Init](#init), s’assurant qu’il reste en vie pendant la durée de vie de l’enumérateur.

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

Ce membre souligne la collecte qui fournit les données qui conduisent à la mise en œuvre de l’interface d’enumérateur.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Notes

Ce membre est paralégé par un appel à [IEnumOnSTLImpl::Init](#init).

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumOnSTLImpl::m_iter

Ce membre détient l’itérateur utilisé pour marquer la position actuelle au sein de la collection et naviguer vers les éléments suivants.

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumOnSTLImpl::Suivant

Cette méthode fournit la mise en œuvre de la méthode **Suivant.**

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
[dans] Le nombre d’éléments demandés.

*rgelt*<br/>
[out] Le tableau à remplir avec les éléments.

*pceltFetched*<br/>
[out] Le nombre d’éléments effectivement retournés dans *rgelt*. Cela peut être inférieur *au celt* si moins *d’éléments de celt* restent dans la liste.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumOnSTLImpl::Reset

Cette méthode fournit la mise en œuvre de la méthode **Reset.**

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumOnSTLImpl::Skip

Cette méthode fournit la mise en œuvre de la méthode **Skip.**

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
[dans] Le nombre d’éléments à sauter.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
