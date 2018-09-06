---
title: Iperpropertybrowsingimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs:
- C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb4b35d851858eaab5ba0df471cc2d0bd30f19bc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763079"
---
# <a name="iperpropertybrowsingimpl-class"></a>Iperpropertybrowsingimpl, classe

Cette classe implémente `IUnknown` et permet au client d’accéder aux informations dans les pages de propriétés d’un objet.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Paramètres

*T*  
Votre classe, dérivée de `IPerPropertyBrowsingImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Récupère une chaîne qui décrit une propriété donnée.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Récupère un tableau de chaînes correspondant aux valeurs qu’une propriété donnée peut accepter.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Récupère une valeur VARIANT contenant la valeur d’une propriété identifiée par un DISPID donné. Le DISPID est associé au nom de chaîne extrait `GetPredefinedStrings`. L’implémentation de ATL retourne E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Récupère le CLSID de la page de propriété associée à une propriété donnée.|

## <a name="remarks"></a>Notes

Le [IPerPropertyBrowsing](/windows/desktop/api/ocidl/nn-ocidl-iperpropertybrowsing) interface permet au client d’accéder aux informations dans les pages de propriétés d’un objet. Classe `IPerPropertyBrowsingImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

> [!NOTE]
>  Si vous utilisez Microsoft Access en tant que l’application de conteneur, vous devez dériver votre classe de `IPerPropertyBrowsingImpl`. Sinon, l’accès ne chargera pas votre contrôle.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString

Récupère une chaîne qui décrit une propriété donnée.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Notes

Consultez [IPerPropertyBrowsing::GetDisplayString](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) dans le Kit de développement logiciel Windows.

##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings

Remplit chaque tableau avec zéro élément.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Valeur de retour

Implémentation d’ATL de [GetPredefinedValue](#getpredefinedvalue) retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPerPropertyBrowsing::GetPredefinedStrings](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) dans le Kit de développement logiciel Windows.

##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue

Récupère une valeur VARIANT contenant la valeur d’une propriété identifiée par un DISPID donné. Le DISPID est associé au nom de chaîne extrait `GetPredefinedStrings`.

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Implémentation d’ATL de [GetPredefinedStrings](#getpredefinedstrings) ne récupère aucune chaîne correspondante.

Consultez [IPerPropertyBrowsing::GetPredefinedValue](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) dans le Kit de développement logiciel Windows.

##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage

Récupère le CLSID de la page de propriété associée à la propriété spécifiée.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour obtenir ces informations.

Consultez [IPerPropertyBrowsing::MapPropertyToPage](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[IPropertyPageImpl, classe](../../atl/reference/ipropertypageimpl-class.md)   
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
