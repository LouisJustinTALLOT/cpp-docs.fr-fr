---
description: 'En savoir plus sur : classe IPerPropertyBrowsingImpl'
title: IPerPropertyBrowsingImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: eba17c0011343f50f586b13086dc76229f08ba3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139345"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl, classe

Cette classe implémente `IUnknown` et permet à un client d’accéder aux informations contenues dans les pages de propriétés d’un objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPerPropertyBrowsingImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Récupère une chaîne décrivant une propriété donnée.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Récupère un tableau de chaînes correspondant aux valeurs qu’une propriété donnée peut accepter.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Récupère un VARIANT contenant la valeur d’une propriété identifiée par un DISPID donné. Le DISPID est associé au nom de chaîne récupéré à partir de `GetPredefinedStrings` . L’implémentation ATL retourne E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Récupère le CLSID de la page de propriétés associée à une propriété donnée.|

## <a name="remarks"></a>Notes

L’interface [IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) permet à un client d’accéder aux informations contenues dans les pages de propriétés d’un objet. `IPerPropertyBrowsingImpl`La classe fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

> [!NOTE]
> Si vous utilisez Microsoft Access comme application conteneur, vous devez dériver votre classe de `IPerPropertyBrowsingImpl` . Dans le cas contraire, Access ne chargera pas votre contrôle.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a> IPerPropertyBrowsingImpl::GetDisplayString

Récupère une chaîne décrivant une propriété donnée.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Notes

Consultez [IPerPropertyBrowsing :: GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) dans le SDK Windows.

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a> IPerPropertyBrowsingImpl::GetPredefinedStrings

Remplit chaque tableau avec zéro élément.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de [GetPredefinedValue](#getpredefinedvalue) par ATL retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPerPropertyBrowsing :: GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) dans le SDK Windows.

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a> IPerPropertyBrowsingImpl::GetPredefinedValue

Récupère un VARIANT contenant la valeur d’une propriété identifiée par un DISPID donné. Le DISPID est associé au nom de chaîne récupéré à partir de `GetPredefinedStrings` .

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

L’implémentation de [GetPredefinedStrings](#getpredefinedstrings) par ATL ne récupère aucune chaîne correspondante.

Consultez [IPerPropertyBrowsing :: GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) dans le SDK Windows.

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a> IPerPropertyBrowsingImpl::MapPropertyToPage

Récupère le CLSID de la page de propriétés associée à la propriété spécifiée.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour obtenir ces informations.

Consultez [IPerPropertyBrowsing :: MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IPropertyPageImpl, classe](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
