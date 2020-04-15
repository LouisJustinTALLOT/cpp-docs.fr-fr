---
title: Classe CComEnumImpl
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
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327864"
---
# <a name="ccomenumimpl-class"></a>Classe CComEnumImpl

Cette classe fournit la mise en œuvre d’une interface d’enumérateur COM où les éléments énumérés sont stockés dans un tableau.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Une interface d’enumérateur COM. Voir [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) pour un exemple.

*piid*<br/>
Un pointeur à l’interface ID de l’interface d’enumérateur.

*T*<br/>
Le type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Une classe de politique de [copie](../../atl/atl-copy-policy-classes.md)homogène .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Constructeur.|
|[CComEnumImpl::CComEnumImpl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|La mise en œuvre de la méthode d’interface d’énumération **Clone.**|
|[CComEnumImpl::Init](#init)|Initialise l'énumérateur.|
|[CComEnumImpl::Suivant](#next)|La mise en œuvre de **Next**.|
|[CComEnumImpl::Reset](#reset)|La mise en œuvre de **Reset**.|
|[CComEnumImpl::Skip](#skip)|La mise en œuvre de **Skip**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Un pointeur au premier élément du tableau.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Copier les `Init`drapeaux passés par .|
|[CComEnumImpl::m_end](#m_end)|Un pointeur à l’emplacement juste au-delà du dernier élément dans le tableau.|
|[CComEnumImpl::m_iter](#m_iter)|Un pointeur à l’élément actuel dans le tableau.|
|[CComEnumImpl::m_spUnk](#m_spunk)|Le `IUnknown` pointeur de l’objet fournissant la collection en cours d’énumération.|

## <a name="remarks"></a>Notes

Voir [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) pour un exemple de mise en œuvre de la méthode. `CComEnumImpl`fournit la mise en œuvre d’une interface d’enumérateur COM où les éléments énumérés sont stockés dans un tableau. Cette classe est analogue `IEnumOnSTLImpl` à la classe, qui fournit une mise en œuvre d’une interface d’enumérateur basée sur un conteneur de bibliothèque standard C.

> [!NOTE]
> Pour plus de détails `CComEnumImpl` `IEnumOnSTLImpl`sur d’autres différences entre et , voir [CComEnumImpl::Init](#init).

Typiquement, vous *n’aurez pas* besoin de créer votre propre classe d’énumérateur en tirant de cette implémentation d’interface. Si vous souhaitez utiliser un enumérateur fourni par ATL basé sur un tableau, il est plus fréquent de créer une instance de [CComEnum](../../atl/reference/ccomenum-class.md).

Toutefois, si vous avez besoin de fournir un enumérateur personnalisé (par exemple, celui qui expose les interfaces en plus de l’interface d’enumérateur), vous pouvez tirer de cette classe. Dans cette situation, il est probable que vous aurez besoin de remplacer le [CComEnumImpl::Clone](#clone) méthode pour fournir votre propre implémentation.

Pour plus d’informations, voir [ATL Collections et Enumerators](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Constructeur.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl::CComEnumImpl

Destructeur.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl::Init

Vous devez appeler cette méthode avant de passer un pointeur à l’interface d’enumérateur de retour à tous les clients.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Paramètres

*Commencer*<br/>
Un pointeur sur le premier élément de la gamme contenant les éléments à énumérer.

*Fin*<br/>
Un pointeur à l’emplacement juste au-delà du dernier élément de la gamme contenant les éléments à énumérer.

*Punk*<br/>
[dans] Le `IUnknown` pointeur d’un objet qui doit être maintenu en vie pendant toute la durée de vie de l’énumérateur. Passer NULL si aucun objet de ce genre n’existe.

*Drapeaux*<br/>
Drapeaux précisant si l’enumérateur doit ou non prendre possession du tableau ou en faire une copie. Les valeurs possibles sont décrites ci-dessous.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

N’appelez cette méthode qu’une seule fois — initialiser l’énumérateur, l’utiliser, puis la jeter.

Si vous passez des indications sur des éléments d’un tableau tenu dans un autre objet (et vous ne demandez pas à l’enumérateur de copier les données), vous pouvez utiliser le *paramètre pUnk* pour vous assurer que l’objet et le tableau qu’il détient sont disponibles aussi longtemps que l’enumérateur en a besoin. L’enumérateur détient simplement une référence COM sur l’objet pour le maintenir en vie. La référence COM est automatiquement libérée lorsque l’enumérateur est détruit.

Le paramètre *des drapeaux* vous permet de spécifier comment l’énumérateur doit traiter les éléments du tableau qui lui sont transmis. *les drapeaux* peuvent prendre l’une des valeurs de l’énumération `CComEnumFlags` indiquée ci-dessous :

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`signifie que la durée de vie du tableau n’est pas contrôlée par l’enumérateur. Dans ce cas, soit le tableau sera statique, soit l’objet identifié par *pUnk* sera responsable de la libération du tableau lorsqu’il n’est plus nécessaire.

`AtlFlagTakeOwnership`signifie que la destruction du tableau doit être contrôlée par l’énumérateur. Dans ce cas, le tableau doit avoir été alloué dynamiquement à l’aide **de nouveaux**. L’enumérateur supprimera le tableau dans son destructor. Typiquement, vous passeriez NULL pour *pUnk*, bien que vous puissiez toujours passer un pointeur valide si vous avez besoin d’être informé de la destruction de l’énumérateur pour une raison quelconque.

`AtlFlagCopy`signifie qu’un nouveau tableau doit être créé `Init`en copiant le tableau passé à . La durée de vie du nouveau tableau doit être contrôlée par l’enumérateur. L’enumérateur supprimera le tableau dans son destructor. Typiquement, vous passeriez NULL pour *pUnk*, bien que vous puissiez toujours passer un pointeur valide si vous avez besoin d’être informé de la destruction de l’énumérateur pour une raison quelconque.

> [!NOTE]
> Le prototype de cette méthode spécifie `T`les `T` éléments de tableau comme étant de type , où a été défini comme un paramètre de modèle à la classe. C’est le même type qui est exposé au moyen de la méthode d’interface COM [CComEnumImpl::Next](#next). L’implication de ceci est que, contrairement à [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), cette classe ne prend pas en charge différents types de stockage et de données exposées. Le type de données des éléments du tableau doit être le même que le type de données exposé au moyen de l’interface COM.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl::Clone

Cette méthode fournit la **Clone** mise en œuvre `CComEnum`de la méthode Clone en créant un objet de type, en l’initialisant avec le même tableau et l’itérateur utilisé par l’objet actuel, et en retournant l’interface sur l’objet nouvellement créé.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Paramètres

*ppEnum*<br/>
[out] L’interface d’enumérateur sur un objet nouvellement créé cloné à partir de l’enumérateur actuel.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Notez que lesumérateurs clonés ne font jamais leur propre copie (ou prennent possession) des données utilisées par l’enumérateur d’origine. Si nécessaire, les enumérateurs clonés garderont l’enumérateur d’origine en vie (à l’aide d’une référence COM) pour s’assurer que les données sont disponibles aussi longtemps qu’ils en ont besoin.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl::m_spUnk

Ce pointeur intelligent maintient une référence sur l’objet passé à [CComEnumImpl::Init](#init), s’assurant qu’il reste en vie pendant la durée de vie de l’énumérateur.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl::m_begin

Un pointeur à l’emplacement juste au-delà du dernier élément de la gamme contenant les éléments à énumérer.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl::m_end

Un pointeur sur le premier élément de la gamme contenant les éléments à énumérer.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl::m_iter

Un pointeur à l’élément actuel de la gamme contenant les éléments à énumérer.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl::m_dwFlags

Les drapeaux sont passés à [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl::Suivant

Cette méthode fournit la mise en œuvre de la méthode **Suivant.**

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
[dans] Le nombre d’éléments demandés.

*rgelt*<br/>
[out] Le tableau à remplir avec les éléments.

*pceltFetched*<br/>
[out] Le nombre d’éléments effectivement retournés dans *rgelt*. Cela peut être inférieur *au celt si* moins *d’éléments de celt* sont restés dans la liste.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl::Reset

Cette méthode fournit la mise en œuvre de la méthode **Reset.**

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl::Skip

Cette méthode fournit la mise en œuvre de la méthode **Skip.**

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
[dans] Le nombre d’éléments à sauter.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Les retours E_INVALIDARG si *le celt* est nul, les retours S_FALSE si moins *d’éléments de celt* sont retournés, les retours S_OK autrement.

## <a name="see-also"></a>Voir aussi

[Classe IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Classe CComEnum](../../atl/reference/ccomenum-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
