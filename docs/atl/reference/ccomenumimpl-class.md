---
title: CComEnumImpl, classe
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: ccd083f3bfd9ae694c97e466fcb40b348fec0c27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273771"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl, classe

Cette classe fournit l’implémentation d’une interface d’énumérateur COM dans lequel les éléments énumérés sont stockés dans un tableau.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Une interface COM de l’énumérateur. Consultez [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) pour obtenir un exemple.

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Le type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Un homogènes [copier la classe de stratégie](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Constructeur.|
|[CComEnumImpl::~CComEnumImpl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|L’implémentation de la **Clone** méthode interface d’énumération.|
|[CComEnumImpl::Init](#init)|Initialise l'énumérateur.|
|[CComEnumImpl::Next](#next)|L’implémentation de **suivant**.|
|[CComEnumImpl::Reset](#reset)|L’implémentation de **réinitialiser**.|
|[CComEnumImpl::Skip](#skip)|L’implémentation de **Skip**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Pointeur vers le premier élément du tableau.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Copier les indicateurs passés via `Init`.|
|[CComEnumImpl::m_end](#m_end)|Pointeur vers l’emplacement juste après le dernier élément dans le tableau.|
|[CComEnumImpl::m_iter](#m_iter)|Pointeur vers l’élément actuel dans le tableau.|
|[CComEnumImpl::m_spUnk](#m_spunk)|Le `IUnknown` pointeur de l’objet qui fournit la collection énumérée.|

## <a name="remarks"></a>Notes

Consultez [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) pour obtenir un exemple d’implémentations de méthode. `CComEnumImpl` fournit l’implémentation d’une interface d’énumérateur COM dans lequel les éléments énumérés sont stockés dans un tableau. Cette classe est analogue à la `IEnumOnSTLImpl` classe, qui fournit une implémentation d’une interface d’énumérateur basé sur un conteneur de bibliothèque C++ Standard.

> [!NOTE]
>  Pour plus d’informations sur les autres différences entre `CComEnumImpl` et `IEnumOnSTLImpl`, consultez [CComEnumImpl::Init](#init).

En règle générale, vous allez *pas* devez créer votre propre classe de l’énumérateur en dérivant à partir de cette implémentation d’interface. Si vous souhaitez utiliser un énumérateur fournis par ATL basé sur un tableau, il est plus courant pour créer une instance de [CComEnum](../../atl/reference/ccomenum-class.md).

Toutefois, si vous n’avez pas besoin de fournir un énumérateur personnalisé (par exemple, un qui expose des interfaces en plus de l’interface de l’énumérateur), vous pouvez dériver de cette classe. Dans ce cas, il est probable que vous devrez remplacer le [CComEnumImpl::Clone](#clone) méthode pour fournir votre propre implémentation.

Pour plus d’informations, consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="ccomenumimpl"></a>  CComEnumImpl::CComEnumImpl

Constructeur.

```
CComEnumImpl();
```

##  <a name="dtor"></a>  CComEnumImpl::~CComEnumImpl

Destructeur.

```
~CComEnumImpl();
```

##  <a name="init"></a>  CComEnumImpl::Init

Vous devez appeler cette méthode avant de passer un pointeur vers l’interface de l’énumérateur à tous les clients.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Paramètres

*begin*<br/>
Pointeur vers le premier élément du tableau qui contient les éléments à énumérer.

*end*<br/>
Pointeur vers l’emplacement juste après le dernier élément du tableau qui contient les éléments à énumérer.

*pUnk*<br/>
[in] Le `IUnknown` pointeur d’un objet qui doit être maintenu actif pendant la durée de vie de l’énumérateur. Passez la valeur NULL si aucun objet n’existe.

*flags*<br/>
Indicateurs spécifiant si l’énumérateur doit prendre possession du tableau ou effectuer une copie de celle-ci. Les valeurs possibles sont décrits ci-dessous.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Appelez cette méthode uniquement une fois, initialiser l’énumérateur, l’utiliser, puis jeter.

Si vous passer des pointeurs aux éléments dans un tableau dans un autre objet (et vous ne me demander l’énumérateur pour copier les données), vous pouvez utiliser la *pUnk* paramètre pour vous assurer que l’objet et le tableau qu’il contient sont disponibles aussi longtemps que l’énumérateur en a besoin. L’énumérateur conserve simplement une référence COM sur l’objet pour conserver actif. La référence COM est automatiquement libérée lorsque l’énumérateur est détruit.

Le *indicateurs* paramètre vous permet de spécifier comment l’énumérateur doit traiter les éléments du tableau passés. *indicateurs* peut prendre une des valeurs à partir de la `CComEnumFlags` énumération indiquée ci-dessous :

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy` signifie que la durée de vie du tableau n’est pas contrôlée par l’énumérateur. Dans ce cas, soit le tableau sera statique ou l’objet identifié par *pUnk* sera chargé de libérer le tableau lorsqu’il n’est plus nécessaire.

`AtlFlagTakeOwnership` signifie que la destruction du tableau doit être contrôlé par l’énumérateur. Dans ce cas, le tableau doit avoir été alloué dynamiquement à l’aide de **nouveau**. L’énumérateur supprimera le tableau dans son destructeur. En règle générale, vous devez passer NULL pour *pUnk*, bien que vous pouvez toujours passer un pointeur valide si vous avez besoin être informé de la destruction de l’énumérateur pour une raison quelconque.

`AtlFlagCopy` signifie qu’un nouveau tableau doit être créée en copiant le tableau passé à `Init`. Durée de vie du nouveau tableau doit être contrôlé par l’énumérateur. L’énumérateur supprimera le tableau dans son destructeur. En règle générale, vous devez passer NULL pour *pUnk*, bien que vous pouvez toujours passer un pointeur valide si vous avez besoin être informé de la destruction de l’énumérateur pour une raison quelconque.

> [!NOTE]
>  Le prototype de cette méthode spécifie les éléments du tableau comme étant de type `T`, où `T` a été défini comme un paramètre de modèle à la classe. Il s’agit du même type qui est exposé au moyen de la méthode d’interface COM [CComEnumImpl::Next](#next). Cela est que, contrairement à [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), cette classe ne prend pas en charge le stockage différent et exposé des types de données. Le type de données d’éléments dans le tableau doit être le même que le type de données exposé au moyen de l’interface COM.

##  <a name="clone"></a>  CComEnumImpl::Clone

Cette méthode fournit l’implémentation de la **Clone** méthode en créant un objet de type `CComEnum`, l’initialisation avec le même tableau et itérateur utilisé par l’objet actuel et le renvoi de l’interface sur nouvellement créé objet.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Paramètres

*ppEnum*<br/>
[out] L’interface de l’énumérateur sur un objet nouvellement créé cloné à partir de l’énumérateur en cours.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Notez que les énumérateurs clonés jamais effectuer leurs propre copie (ou prendre possession) des données utilisées par l’énumérateur d’origine. Si nécessaire, les énumérateurs clonés conservera l’énumérateur d’origine actif (à l’aide d’une référence COM) pour s’assurer que les données de disponibilité tant qu’ils en ont besoin.

##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk

Ce pointeur intelligent conserve une référence sur l’objet passé à [CComEnumImpl::Init](#init), s’assurer qu’il reste actif pendant la durée de vie de l’énumérateur.

```
CComPtr<IUnknown> m_spUnk;
```

##  <a name="m_begin"></a>  CComEnumImpl::m_begin

Pointeur vers l’emplacement juste après le dernier élément du tableau qui contient les éléments à énumérer.

```
T* m_begin;
```

##  <a name="m_end"></a>  CComEnumImpl::m_end

Pointeur vers le premier élément du tableau qui contient les éléments à énumérer.

```
T* m_end;
```

##  <a name="m_iter"></a>  CComEnumImpl::m_iter

Pointeur vers l’élément actuel du tableau qui contient les éléments à énumérer.

```
T* m_iter;
```

##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags

Les indicateurs passés à [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

##  <a name="next"></a>  CComEnumImpl::Next

Cette méthode fournit l’implémentation de la **suivant** (méthode).

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
[in] Le nombre d’éléments demandés.

*rgelt*<br/>
[out] Tableau à remplir avec les éléments.

*pceltFetched*<br/>
[out] Le nombre d’éléments réellement retournés dans *rgelt*. Cela peut être inférieur à *celt* si moins de *celt* éléments est restée dans la liste.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="reset"></a>  CComEnumImpl::Reset

Cette méthode fournit l’implémentation de la **réinitialiser** (méthode).

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="skip"></a>  CComEnumImpl::Skip

Cette méthode fournit l’implémentation de la **Skip** (méthode).

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
[in] Le nombre d’éléments à ignorer.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Retourne E_INVALIDARG si *celt* est égal à zéro, retourne S_FALSE si moins de *celt* éléments sont retournés, sinon, retourne S_OK.

## <a name="see-also"></a>Voir aussi

[IEnumOnSTLImpl, classe](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum, classe](../../atl/reference/ccomenum-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
