---
title: Classe IPerPropertyBrowsingImpl
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
ms.openlocfilehash: f8fb80cc38e775b9b26afa033647faac694e968a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326512"
---
# <a name="iperpropertybrowsingimpl-class"></a>Classe IPerPropertyBrowsingImpl

Cette classe `IUnknown` implémente et permet à un client d’accéder à l’information dans les pages de propriété d’un objet.

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
Votre classe, `IPerPropertyBrowsingImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Récupère une chaîne décrivant une propriété donnée.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings IPerPropertyBrowsingImpl::GetPredefinedStrings IPerPropertyBrowsingImpl::GetPredefinedStrings IPer](#getpredefinedstrings)|Récupère un tableau de chaînes correspondant aux valeurs qu’une propriété donnée peut accepter.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Récupère un VARIANT contenant la valeur d’une propriété identifiée par un DISPID donné. Le DISPID est associé au nom `GetPredefinedStrings`de chaîne récupéré de . La mise en œuvre d’ATL E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Récupère le CLSID de la page de propriété associée à une propriété donnée.|

## <a name="remarks"></a>Notes

[L’interface IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) permet à un client d’accéder à l’information dans les pages de propriété d’un objet. La `IPerPropertyBrowsingImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

> [!NOTE]
> Si vous utilisez Microsoft Access comme application de conteneur, vous devez tirer votre classe de `IPerPropertyBrowsingImpl`. Dans le cas contraire, Access ne chargera pas votre contrôle.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString IPerPropertyBrowsingImpl::GetDisplayString

Récupère une chaîne décrivant une propriété donnée.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Notes

Voir [IPerPropertyBrowsing::GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) in the Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings IPerPropertyBrowsingImpl::GetPredefinedStrings IPerPropertyBrowsingImpl::GetPredefinedStrings IPer

Remplit chaque tableau de zéro élément.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de [GetPredefinedValue](#getpredefinedvalue) d’ATL revient E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IPerPropertyBrowsing::GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) in the Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue

Récupère un VARIANT contenant la valeur d’une propriété identifiée par un DISPID donné. Le DISPID est associé au nom `GetPredefinedStrings`de chaîne récupéré de .

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

La mise en œuvre de [GetPredefinedStrings par](#getpredefinedstrings) ATL ne récupère pas de chaînes correspondantes.

Voir [IPerPropertyBrowsing::GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) in the Windows SDK.

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage

Récupère le CLSID de la page de propriété associée à la propriété spécifiée.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Notes

ATL utilise la carte des biens de l’objet pour obtenir ces informations.

Voir [IPerPropertyBrowsing::MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
