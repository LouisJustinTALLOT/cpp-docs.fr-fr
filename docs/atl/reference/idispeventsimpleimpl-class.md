---
description: 'En savoir plus sur : IDispEventSimpleImpl, classe'
title: IDispEventSimpleImpl, classe
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
ms.openlocfilehash: 4b581f4e5714f595a29fb27bd6dbd45c7d5e401c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139501"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl, classe

Cette classe fournit des implémentations des `IDispatch` méthodes, sans obtenir les informations de type d’une bibliothèque de types.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur unique de l’objet source. Quand `IDispEventSimpleImpl` est la classe de base d’un contrôle composite, utilisez l’ID de ressource du contrôle contenu de votre choix pour ce paramètre. Dans d’autres cas, utilisez un entier positif arbitraire.

*T*<br/>
Classe de l’utilisateur, dérivée de `IDispEventSimpleImpl` .

*pdiid*<br/>
Pointeur vers l’IID de l’dispinterface d’événement implémentée par cette classe.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispEventSimpleImpl :: Advise](#advise)|Établit une connexion avec la source d’événements par défaut.|
|[IDispEventSimpleImpl ::D ispEventAdvise](#dispeventadvise)|Établit une connexion avec la source de l’événement.|
|[IDispEventSimpleImpl ::D ispEventUnadvise](#dispeventunadvise)|Interrompt la connexion avec la source de l’événement.|
|[IDispEventSimpleImpl :: GetIDsOfNames](#getidsofnames)|Retourne E_NOTIMPL.|
|[IDispEventSimpleImpl :: GetTypeInfo](#gettypeinfo)|Retourne E_NOTIMPL.|
|[IDispEventSimpleImpl :: GetTypeInfoCount](#gettypeinfocount)|Retourne E_NOTIMPL.|
|[IDispEventSimpleImpl :: Invoke](#invoke)|Appelle les gestionnaires d’événements listés dans la table de récepteurs d’événements.|
|[IDispEventSimpleImpl :: Unadvise](#unadvise)|Interrompt la connexion avec la source d’événements par défaut.|

## <a name="remarks"></a>Notes

`IDispEventSimpleImpl` fournit un moyen d’implémenter une dispinterface d’événement sans vous obliger à fournir le code d’implémentation pour chaque méthode/événement sur cette interface. `IDispEventSimpleImpl` fournit des implémentations des `IDispatch` méthodes. Il vous suffit de fournir des implémentations pour les événements que vous souhaitez gérer.

`IDispEventSimpleImpl` fonctionne conjointement avec le mappage de récepteur d’événements dans votre classe pour acheminer les événements vers la fonction de gestionnaire appropriée. Pour utiliser cette classe :

- Ajoutez une macro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) à la table de récepteurs d’événements pour chaque événement de chaque objet que vous souhaitez gérer.

- Fournissez des informations de type pour chaque événement en passant un pointeur vers une structure [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) en tant que paramètre à chaque entrée. Sur la plateforme x86, la `_ATL_FUNC_INFO.cc` valeur doit être CC_CDECL avec la fonction de rappel appelant la méthode de __stdcall.

- Appelez [DispEventAdvise](#dispeventadvise) pour établir la connexion entre l’objet source et la classe de base.

- Appelez [DispEventUnadvise](#dispeventunadvise) pour rompre la connexion.

Vous devez dériver de `IDispEventSimpleImpl` (à l’aide d’une valeur unique pour *nid*) pour chaque objet pour lequel vous devez gérer des événements. Vous pouvez réutiliser la classe de base en désexaminant un objet source, puis en vous avertissant par rapport à un objet source différent, mais le nombre maximal d’objets sources qui peuvent être gérés par un seul objet à la fois est limité par le nombre de `IDispEventSimpleImpl` classes de base.

`IDispEventSimplImpl` fournit les mêmes fonctionnalités que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), sauf qu’il n’obtient pas d’informations de type sur l’interface à partir d’une bibliothèque de types. Les Assistants génèrent du code basé uniquement sur `IDispEventImpl` , mais vous pouvez utiliser `IDispEventSimpleImpl` en ajoutant le code manuellement. Utilisez `IDispEventSimpleImpl` si vous n’avez pas de bibliothèque de types décrivant l’interface d’événement ou si vous souhaitez éviter la surcharge associée à l’utilisation de la bibliothèque de types.

> [!NOTE]
> `IDispEventImpl` et `IDispEventSimpleImpl` fournissent leur propre implémentation de `IUnknown::QueryInterface` permettant `IDispEventImpl` à chaque `IDispEventSimpleImpl` classe de base ou à d’agir en tant qu’identité com distincte tout en autorisant l’accès direct aux membres de classe dans votre objet com principal.

L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

Pour plus d’informations, consultez [prise en charge de IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a> IDispEventSimpleImpl :: Advise

Appelez cette méthode pour établir une connexion avec la source d’événements représentée par *punk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers l' `IUnknown` interface de l’objet source de l’événement.

### <a name="return-value"></a>Valeur renvoyée

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Une fois la connexion établie, les événements déclenchés à partir de *punk* sont acheminés vers les gestionnaires de votre classe par le biais du mappage de récepteurs d’événements.

> [!NOTE]
> Si votre classe dérive de plusieurs `IDispEventSimpleImpl` classes, vous devrez lever l’ambiguïté entre les appels à cette méthode en utilisant la portée de l’appel avec la classe de base particulière qui vous intéresse.

`Advise` établit une connexion avec la source d’événements par défaut, il obtient l’IID de la source d’événements par défaut de l’objet tel que déterminé par [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a> IDispEventSimpleImpl ::D ispEventAdvise

Appelez cette méthode pour établir une connexion avec la source d’événements représentée par *punk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers l' `IUnknown` interface de l’objet source de l’événement.

*piid*<br/>
Pointeur vers l’IID de l’objet source de l’événement.

### <a name="return-value"></a>Valeur renvoyée

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Par la suite, les événements déclenchés à partir de *punk* sont acheminés vers les gestionnaires de votre classe par le biais du mappage de récepteurs d’événements.

> [!NOTE]
> Si votre classe dérive de plusieurs `IDispEventSimpleImpl` classes, vous devrez lever l’ambiguïté entre les appels à cette méthode en utilisant la portée de l’appel avec la classe de base particulière qui vous intéresse.

`DispEventAdvise` établit une connexion avec la source d’événements spécifiée dans `pdiid` .

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a> IDispEventSimpleImpl ::D ispEventUnadvise

Interrompt la connexion avec la source d’événements représentée par *punk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers l' `IUnknown` interface de l’objet source de l’événement.

*piid*<br/>
Pointeur vers l’IID de l’objet source de l’événement.

### <a name="return-value"></a>Valeur renvoyée

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Une fois la connexion interrompue, les événements ne sont plus acheminés vers les fonctions de gestionnaire listées dans le mappage de récepteur d’événements.

> [!NOTE]
> Si votre classe dérive de plusieurs `IDispEventSimpleImpl` classes, vous devrez lever l’ambiguïté entre les appels à cette méthode en utilisant la portée de l’appel avec la classe de base particulière qui vous intéresse.

`DispEventAdvise` interrompt une connexion établie avec la source d’événements spécifiée dans `pdiid` .

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a> IDispEventSimpleImpl :: GetIDsOfNames

Cette implémentation de `IDispatch::GetIDsOfNames` retourne E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch :: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le SDK Windows.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a> IDispEventSimpleImpl :: GetTypeInfo

Cette implémentation de `IDispatch::GetTypeInfo` retourne E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch :: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) dans la SDK Windows.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a> IDispEventSimpleImpl :: GetTypeInfoCount

Cette implémentation de `IDispatch::GetTypeInfoCount` retourne E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch :: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) dans la SDK Windows.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a> IDispEventSimpleImpl :: Invoke

Cette implémentation d' `IDispatch::Invoke` appelle les gestionnaires d’événements listés dans le mappage de récepteurs d’événements.

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

Consultez [IDispatch :: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a> IDispEventSimpleImpl :: Unadvise

Interrompt la connexion avec la source d’événements représentée par *punk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers l' `IUnknown` interface de l’objet source de l’événement.

### <a name="return-value"></a>Valeur renvoyée

S_OK ou toute valeur HRESULT d’échec.

### <a name="remarks"></a>Notes

Une fois la connexion interrompue, les événements ne sont plus acheminés vers les fonctions de gestionnaire listées dans le mappage de récepteur d’événements.

> [!NOTE]
> Si votre classe dérive de plusieurs `IDispEventSimpleImpl` classes, vous devrez lever l’ambiguïté entre les appels à cette méthode en utilisant la portée de l’appel avec la classe de base particulière qui vous intéresse.

`Unadvise` interrompt une connexion établie avec la source d’événements par défaut spécifiée dans `pdiid` .

`Unavise` interrompt une connexion avec la source d’événement par défaut, il obtient l’IID de la source d’événements par défaut de l’objet tel que déterminé par [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Voir aussi

[Structure _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Classe IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl (classe)](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
