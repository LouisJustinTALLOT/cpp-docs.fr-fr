---
title: IEnumOnSTLImpl, classe
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
ms.openlocfilehash: 7cf777f3ff0d298f224157735a06bf57a2c10cf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495859"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl, classe

Cette classe définit une interface d’énumérateur basée sur C++ une collection de bibliothèques standard.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Énumérateur COM. Pour obtenir un exemple, consultez [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Type d’élément exposé par l’interface de l’énumérateur.

*Copy*<br/>
[Classe de stratégie de copie](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Classe C++ de conteneur de bibliothèque standard.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|Implémentation de **clone**.|
|[IEnumOnSTLImpl::Init](#init)|Initialise l'énumérateur.|
|[IEnumOnSTLImpl::Next](#next)|Implémentation de **Next**.|
|[IEnumOnSTLImpl::Reset](#reset)|Implémentation de **Reset**.|
|[IEnumOnSTLImpl::Skip](#skip)|L’implémentation de **Skip**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Itérateur qui représente la position actuelle de l’énumérateur dans la collection.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Pointeur vers le C++ conteneur de bibliothèque standard contenant les éléments à énumérer.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown` Pointeur de l’objet qui fournit la collection.|

## <a name="remarks"></a>Notes

`IEnumOnSTLImpl`fournit l’implémentation pour une interface d’énumérateur COM où les éléments qui sont énumérés sont stockés dans C++ un conteneur compatible avec la bibliothèque standard. Cette classe est analogue à la classe [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) , qui fournit une implémentation pour une interface d’énumérateur basée sur un tableau.

> [!NOTE]
>  Pour plus d’informations sur les différences entre `CComEnumImpl` et, `IEnumOnSTLImpl`consultez [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init) .

En règle générale, vous n’aurez *pas* besoin de créer votre propre classe d’énumérateur en dérivant de cette implémentation d’interface. Si vous souhaitez utiliser un énumérateur fourni par ATL basé sur un C++ conteneur de bibliothèque standard, il est plus courant de créer une instance de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), ou de créer une classe de collection qui retourne un énumérateur en dérivant de [ICollectionOnSTLImpl ](../../atl/reference/icollectiononstlimpl-class.md).

Toutefois, si vous avez besoin de fournir un énumérateur personnalisé (par exemple, un énumérateur qui expose des interfaces en plus de l’interface d’énumérateur), vous pouvez dériver de cette classe. Dans ce cas, il est probable que vous devrez remplacer la méthode [clone](#clone) pour fournir votre propre implémentation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="init"></a>  IEnumOnSTLImpl::Init

Initialise l'énumérateur.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Paramètres

*pUnkForRelease*<br/>
dans `IUnknown` Pointeur d’un objet qui doit être gardé actif pendant la durée de vie de l’énumérateur. Transmettez la valeur NULL si aucun objet de ce type n’existe.

*collection*<br/>
Référence au conteneur de C++ bibliothèque standard qui contient les éléments à énumérer.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si vous transmettez `Init` une référence à une collection contenue dans un autre objet, vous pouvez utiliser le paramètre *pUnkForRelease* pour vous assurer que l’objet et la collection qu’il contient sont disponibles aussi longtemps que l’énumérateur en a besoin.

Vous devez appeler cette méthode avant de passer un pointeur vers l’interface de l’énumérateur à n’importe quel client.

##  <a name="clone"></a>  IEnumOnSTLImpl::Clone

Cette méthode fournit l’implémentation de la méthode Clone en créant un objet de `CComEnumOnSTL`type, en l’initialisant avec la même collection et l’itérateur utilisés par l’objet actuel, et en retournant l’interface sur l’objet nouvellement créé.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Paramètres

*ppEnum*<br/>
à Interface d’énumérateur sur un objet nouvellement créé cloné à partir de l’énumérateur actuel.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk

`IUnknown` Pointeur de l’objet qui fournit la collection.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Notes

Ce pointeur intelligent gère une référence sur l’objet passé à [IEnumOnSTLImpl:: init](#init), en veillant à ce qu’il reste actif pendant la durée de vie de l’énumérateur.

##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection

Ce membre pointe vers la collection qui fournit les données pilotant l’implémentation de l’interface de l’énumérateur.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Notes

Ce membre est initialisé par un appel à [IEnumOnSTLImpl:: init](#init).

##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter

Ce membre contient l’itérateur utilisé pour marquer la position actuelle dans la collection et accéder aux éléments suivants.

```
CollType::iterator m_iter;
```

##  <a name="next"></a>  IEnumOnSTLImpl::Next

Cette méthode fournit l’implémentation de la méthode **suivante** .

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
dans Nombre d’éléments demandés.

*rgelt*<br/>
à Tableau à remplir avec les éléments.

*pceltFetched*<br/>
à Nombre d’éléments réellement retournés dans *rgelt*. Cela peut être inférieur à *celt* si moins de *celt* Elements restent dans la liste.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="reset"></a>  IEnumOnSTLImpl::Reset

Cette méthode fournit l’implémentation de la méthode de réinitialisation.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="skip"></a>  IEnumOnSTLImpl::Skip

Cette méthode fournit l’implémentation de la méthode **Skip** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
dans Nombre d’éléments à ignorer.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
