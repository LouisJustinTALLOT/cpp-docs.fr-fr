---
title: Classe IDispEventSimpleImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329737"
---
# <a name="idispeventsimpleimpl-class"></a>Classe IDispEventSimpleImpl

Cette classe fournit des `IDispatch` implémentations des méthodes, sans obtenir d’informations de type à partir d’une bibliothèque de type.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Paramètres

*nID*<br/>
Un identifiant unique pour l’objet source. Quand `IDispEventSimpleImpl` est la classe de base pour un contrôle composite, utilisez l’ID de ressource du contrôle contenu souhaité pour ce paramètre. Dans d’autres cas, utilisez un integer positif arbitraire.

*T*<br/>
La classe de l’utilisateur, `IDispEventSimpleImpl`qui est dérivé de .

*pdiid pdiid*<br/>
Le pointeur de l’IID de l’événement dispinterface mis en œuvre par cette classe.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispEventSimpleImpl::Conseiller](#advise)|Établit une connexion avec la source d’événement par défaut.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Établit un lien avec la source de l’événement.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Casse la connexion avec la source de l’événement.|
|[IDispEventSimpleImpl::GetIDsOfNames IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Retourne E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Retourne E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Retourne E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoquer](#invoke)|Appelle les gestionnaires d’événements énumérés dans la carte de l’évier de l’événement.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Casse la connexion avec la source d’événement par défaut.|

## <a name="remarks"></a>Notes

`IDispEventSimpleImpl`fournit un moyen de mettre en œuvre une dispinterface d’événement sans vous obliger à fournir le code d’implémentation pour chaque méthode/événement sur cette interface. `IDispEventSimpleImpl`fournit des implémentations des `IDispatch` méthodes. Vous n’avez qu’à fournir des implémentations pour les événements que vous êtes intéressé à gérer.

`IDispEventSimpleImpl`fonctionne en conjonction avec la carte de l’évier de l’événement dans votre classe pour acheminer les événements à la fonction de gestionnaire approprié. Pour utiliser cette classe :

- Ajoutez une [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro à la carte de l’évier de l’événement pour chaque événement sur chaque objet que vous souhaitez manipuler.

- Fournir des informations de type pour chaque événement en passant un pointeur à une structure [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) comme paramètre à chaque entrée. Sur la plate-forme `_ATL_FUNC_INFO.cc` x86, la valeur doit être CC_CDECL avec la méthode d’appel de fonction de rappel de __stdcall.

- Appelez [DispEventAdvise](#dispeventadvise) pour établir le lien entre l’objet source et la classe de base.

- Appelez [DispEventUnadvise](#dispeventunadvise) pour briser la connexion.

Vous devez `IDispEventSimpleImpl` dériver (en utilisant une valeur unique pour *nID*) pour chaque objet pour lequel vous avez besoin pour gérer les événements. Vous pouvez réutiliser la classe de base en déconseillant un objet source puis en vous conseillant contre un objet source différent, `IDispEventSimpleImpl` mais le nombre maximum d’objets sources qui peuvent être manipulés par un seul objet en même temps est limité par le nombre de classes de base.

`IDispEventSimplImpl`fournit la même fonctionnalité que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), sauf qu’il n’obtiend pas d’informations de type sur l’interface à partir d’une bibliothèque de type. Les assistants génèrent du `IDispEventImpl`code basé uniquement `IDispEventSimpleImpl` sur , mais vous pouvez utiliser en ajoutant le code à la main. Utilisez `IDispEventSimpleImpl` lorsque vous n’avez pas de bibliothèque type décrivant l’interface de l’événement ou que vous voulez éviter les frais généraux associés à l’utilisation de la bibliothèque de type.

> [!NOTE]
> `IDispEventImpl`et `IDispEventSimpleImpl` fournir leur `IUnknown::QueryInterface` propre `IDispEventImpl` mise `IDispEventSimpleImpl` en œuvre de permettre à chaque classe ou à la classe de base d’agir comme une identité COM distincte tout en permettant un accès direct aux membres de la classe dans votre objet COM principal.

La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

Pour plus d’informations, voir [Supporting IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Conseiller

Appelez cette méthode pour établir un lien avec la source de l’événement représentée par *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet source d’événement.

### <a name="return-value"></a>Valeur de retour

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Une fois la connexion établie, les événements tirés de *pUnk* seront acheminés vers les gestionnaires de votre classe par le chemin de la carte de l’évier de l’événement.

> [!NOTE]
> Si votre classe dérive `IDispEventSimpleImpl` de plusieurs classes, vous devrez désambiguer les appels à cette méthode en réduisant l’appel avec la classe de base particulière qui vous intéresse.

`Advise`établit une connexion avec la source d’événement par défaut, il obtient l’IID de la source d’événement par défaut de l’objet tel que déterminé par [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise

Appelez cette méthode pour établir un lien avec la source de l’événement représentée par *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet source d’événement.

*piid*<br/>
Un pointeur à l’IID de l’objet source de l’événement.

### <a name="return-value"></a>Valeur de retour

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Par la suite, les événements tirés de *pUnk* seront acheminés vers les gestionnaires de votre classe par le chemin de la carte de l’évier de l’événement.

> [!NOTE]
> Si votre classe dérive `IDispEventSimpleImpl` de plusieurs classes, vous devrez désambiguer les appels à cette méthode en réduisant l’appel avec la classe de base particulière qui vous intéresse.

`DispEventAdvise`établit un lien avec la `pdiid`source de l’événement spécifiée dans .

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise

Casse la connexion avec la source de l’événement représentée par *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet source d’événement.

*piid*<br/>
Un pointeur à l’IID de l’objet source de l’événement.

### <a name="return-value"></a>Valeur de retour

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Une fois la connexion rompue, les événements ne seront plus acheminés vers les fonctions de gestionnaire énumérées dans la carte de l’évier de l’événement.

> [!NOTE]
> Si votre classe dérive `IDispEventSimpleImpl` de plusieurs classes, vous devrez désambiguer les appels à cette méthode en réduisant l’appel avec la classe de base particulière qui vous intéresse.

`DispEventAdvise`rompt une connexion qui a été `pdiid`établie avec la source de l’événement spécifiée dans .

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames IDispEventSimpleImpl::GetIDsOfNames

Cette mise `IDispatch::GetIDsOfNames` en œuvre des retours E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le SDK Windows.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo

Cette mise `IDispatch::GetTypeInfo` en œuvre des retours E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) dans le Windows SDK.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount

Cette mise `IDispatch::GetTypeInfoCount` en œuvre des retours E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) in the Windows SDK.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Invoquer

Cette mise `IDispatch::Invoke` en œuvre des appels les gestionnaires d’événements énumérés dans la carte de l’évier de l’événement.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Unadvise

Casse la connexion avec la source de l’événement représentée par *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet source d’événement.

### <a name="return-value"></a>Valeur de retour

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Une fois la connexion rompue, les événements ne seront plus acheminés vers les fonctions de gestionnaire énumérées dans la carte de l’évier de l’événement.

> [!NOTE]
> Si votre classe dérive `IDispEventSimpleImpl` de plusieurs classes, vous devrez désambiguer les appels à cette méthode en réduisant l’appel avec la classe de base particulière qui vous intéresse.

`Unadvise`rompt une connexion qui a été `pdiid`établie avec la source d’événement par défaut spécifiée dans .

`Unavise`rompt une connexion avec la source d’événement par défaut, il obtient l’IID de la source d’événement par défaut de l’objet tel que déterminé par [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Voir aussi

[Structure _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Classe IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Classe IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
