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
ms.openlocfilehash: 517a4e90ca21e22dcf161aefcff61a40437eabe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226605"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl, classe

Cette classe fournit l’implémentation pour une interface d’énumérateur COM où les éléments qui sont énumérés sont stockés dans un tableau.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Interface d’énumérateur COM. Pour obtenir un exemple, consultez [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Classe de [stratégie de copie](../../atl/atl-copy-policy-classes.md)homogène.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Constructeur.|
|[CComEnumImpl :: ~ CComEnumImpl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl :: Clone](#clone)|Implémentation de la méthode d’interface d’énumération **clone** .|
|[CComEnumImpl :: init](#init)|Initialise l'énumérateur.|
|[CComEnumImpl :: suivant](#next)|Implémentation de **Next**.|
|[CComEnumImpl :: Reset](#reset)|Implémentation de **Reset**.|
|[CComEnumImpl :: Skip](#skip)|L’implémentation de **Skip**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComEnumImpl :: m_begin](#m_begin)|Pointeur vers le premier élément du tableau.|
|[CComEnumImpl :: m_dwFlags](#m_dwflags)|Indicateurs de copie transmis `Init` .|
|[CComEnumImpl :: m_end](#m_end)|Pointeur vers l’emplacement situé juste après le dernier élément du tableau.|
|[CComEnumImpl :: m_iter](#m_iter)|Pointeur vers l’élément actuel dans le tableau.|
|[CComEnumImpl :: m_spUnk](#m_spunk)|`IUnknown`Pointeur de l’objet qui fournit la collection qui est énumérée.|

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’implémentations de méthode, consultez [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) . `CComEnumImpl`fournit l’implémentation pour une interface d’énumérateur COM où les éléments qui sont énumérés sont stockés dans un tableau. Cette classe est analogue à la `IEnumOnSTLImpl` classe, qui fournit une implémentation d’une interface d’énumérateur basée sur un conteneur de bibliothèque standard C++.

> [!NOTE]
> Pour plus d’informations sur les autres différences entre `CComEnumImpl` et `IEnumOnSTLImpl` , consultez [CComEnumImpl :: init](#init).

En règle générale, vous n’aurez *pas* besoin de créer votre propre classe d’énumérateur en dérivant de cette implémentation d’interface. Si vous souhaitez utiliser un énumérateur fourni par ATL basé sur un tableau, il est plus courant de créer une instance de [CComEnum](../../atl/reference/ccomenum-class.md).

Toutefois, si vous avez besoin de fournir un énumérateur personnalisé (par exemple, un énumérateur qui expose des interfaces en plus de l’interface d’énumérateur), vous pouvez dériver de cette classe. Dans ce cas, il est probable que vous devez substituer la méthode [CComEnumImpl :: Clone](#clone) pour fournir votre propre implémentation.

Pour plus d’informations, consultez [collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Constructeur.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl :: ~ CComEnumImpl

Destructeur.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl :: init

Vous devez appeler cette méthode avant de passer un pointeur vers l’interface de l’énumérateur à n’importe quel client.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Paramètres

*commencer*<br/>
Pointeur vers le premier élément du tableau contenant les éléments à énumérer.

*end*<br/>
Pointeur vers l’emplacement situé juste après le dernier élément du tableau contenant les éléments à énumérer.

*pUnk*<br/>
dans `IUnknown`Pointeur d’un objet qui doit être gardé actif pendant la durée de vie de l’énumérateur. Transmettez la valeur NULL si aucun objet de ce type n’existe.

*flags*<br/>
Indicateurs spécifiant si l’énumérateur doit prendre possession du tableau ou en faire une copie. Les valeurs possibles sont décrites ci-dessous.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

N’appelez cette méthode qu’une seule fois : initialisez l’énumérateur, utilisez-le, puis levez-le.

Si vous transmettez des pointeurs vers des éléments d’un tableau stocké dans un autre objet (et que vous ne demandez pas à l’énumérateur de copier les données), vous pouvez utiliser le paramètre *punk* pour vous assurer que l’objet et le tableau qu’il contient sont disponibles aussi longtemps que l’énumérateur en a besoin. L’énumérateur contient simplement une référence COM sur l’objet pour rester actif. La référence COM est automatiquement libérée lorsque l’énumérateur est détruit.

Le paramètre *Flags* vous permet de spécifier comment l’énumérateur doit traiter les éléments de tableau qui lui sont passés. les *indicateurs* peuvent prendre l’une des valeurs de l' `CComEnumFlags` énumération illustrée ci-dessous :

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`signifie que la durée de vie du tableau n’est pas contrôlée par l’énumérateur. Dans ce cas, soit le tableau est statique, soit l’objet identifié par *punk* est chargé de libérer le tableau lorsqu’il n’est plus nécessaire.

`AtlFlagTakeOwnership`signifie que la destruction du tableau doit être contrôlée par l’énumérateur. Dans ce cas, le tableau doit avoir été alloué de manière dynamique à l’aide de **`new`** . L’énumérateur supprime le tableau dans son destructeur. En général, vous pouvez passer NULL pour *punk*, bien que vous puissiez toujours passer un pointeur valide si vous devez être notifié de la destruction de l’énumérateur pour une raison quelconque.

`AtlFlagCopy`signifie qu’un nouveau tableau doit être créé en copiant le tableau passé à `Init` . La durée de vie du nouveau tableau doit être contrôlée par l’énumérateur. L’énumérateur supprime le tableau dans son destructeur. En général, vous pouvez passer NULL pour *punk*, bien que vous puissiez toujours passer un pointeur valide si vous devez être notifié de la destruction de l’énumérateur pour une raison quelconque.

> [!NOTE]
> Le prototype de cette méthode spécifie que les éléments du tableau sont de type `T` , où `T` a été défini comme paramètre de modèle pour la classe. Il s’agit du même type exposé à l’aide de la méthode d’interface COM [CComEnumImpl :: Next](#next). En revanche, contrairement à [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), cette classe ne prend pas en charge les types de données de stockage et exposés différents. Le type de données des éléments du tableau doit être le même que le type de données exposé par le biais de l’interface COM.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl :: Clone

Cette méthode fournit l’implémentation de la méthode **clone** en créant un objet de type, en l' `CComEnum` initialisant avec le même tableau et itérateur utilisé par l’objet actuel, et en retournant l’interface sur l’objet nouvellement créé.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Paramètres

*ppEnum*<br/>
à Interface d’énumérateur sur un objet nouvellement créé cloné à partir de l’énumérateur actuel.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Notez que les énumérateurs clonés ne font jamais leur propre copie (ou appropriation) des données utilisées par l’énumérateur d’origine. Si nécessaire, les énumérateurs clonés conservent l’énumérateur d’origine actif (à l’aide d’une référence COM) pour garantir que les données sont disponibles aussi longtemps qu’elles en ont besoin.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl :: m_spUnk

Ce pointeur intelligent gère une référence sur l’objet passé à [CComEnumImpl :: init](#init), en veillant à ce qu’il reste actif pendant la durée de vie de l’énumérateur.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl :: m_begin

Pointeur vers l’emplacement situé juste après le dernier élément du tableau contenant les éléments à énumérer.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl :: m_end

Pointeur vers le premier élément du tableau contenant les éléments à énumérer.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl :: m_iter

Pointeur vers l’élément actuel du tableau contenant les éléments à énumérer.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl :: m_dwFlags

Indicateurs passés à [CComEnumImpl :: init](#init).

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl :: suivant

Cette méthode fournit l’implémentation de la méthode **suivante** .

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
dans Nombre d’éléments demandés.

*rgelt*<br/>
à Tableau à remplir avec les éléments.

*pceltFetched*<br/>
à Nombre d’éléments réellement retournés dans *rgelt*. Cela peut être inférieur à *celt* si moins de *celt* Elements sont restés dans la liste.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl :: Reset

Cette méthode fournit l’implémentation de la méthode de **réinitialisation** .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl :: Skip

Cette méthode fournit l’implémentation de la méthode **Skip** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Paramètres

*celt*<br/>
dans Nombre d’éléments à ignorer.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Retourne E_INVALIDARG si *celt* est égal à zéro, retourne S_FALSE si moins de *celt* Elements sont retournés, retourne S_OK dans le cas contraire.

## <a name="see-also"></a>Voir aussi

[IEnumOnSTLImpl, classe](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum, classe](../../atl/reference/ccomenum-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
