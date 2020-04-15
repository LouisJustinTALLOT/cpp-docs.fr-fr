---
title: Classe IOleObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326526"
---
# <a name="ioleobjectimpl-class"></a>Classe IOleObjectImpl

Cette classe `IUnknown` implémente et est l’interface principale par laquelle un conteneur communique avec un contrôle.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IOleObjectImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleObjectImpl::Conseiller](#advise)|Établit un lien consultatif avec le contrôle.|
|[IOleObjectImpl::Fermer](#close)|Change l’état de commande de l’exécution à chargé.|
|[IOleObjectImpl::DoVerb](#doverb)|Indique au contrôle d’effectuer l’une de ses actions énumérées.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Indique au contrôle de jeter tout état de défaire qu’il maintient.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Indique au contrôle de supprimer son interface utilisateur de la vue.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Exécute le contrôle et installe sa fenêtre, mais n’installe pas l’interface utilisateur du contrôle.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Le contrôle est ouvert dans une fenêtre séparée.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Exécute l’action spécifiée lorsque l’utilisateur double-clics le contrôle. Le contrôle définit l’action, généralement pour activer le contrôle sur place.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Affiche un contrôle nouvellement inséré à l’utilisateur.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Active le contrôle sur place et affiche l’interface utilisateur du contrôle, tels que les menus et les barres d’outils.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Énumère les connexions consultatives du contrôle.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Énumère les actions pour le contrôle.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Récupère le site client du contrôle.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Récupère les données du Clipboard. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Récupère l’étendue de la zone d’affichage du contrôle.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Récupère l’état du contrôle.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Récupère le surnom du contrôle. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Récupère l’identifiant de classe du contrôle.|
|[IOleObjectImpl::GetUserType](#getusertype)|Récupère le nom d’utilisateur du contrôle.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Initialise le contrôle à partir de données sélectionnées. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Vérifie si le contrôle est à jour. La mise en œuvre d’ATL S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) après l’état défait est jeté.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Appelé par [DoVerbHide](#doverbhide) après le contrôle est caché.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) après que le contrôle est activé en place.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Appelé par [DoVerbOpen](#doverbopen) après le contrôle a été ouvert pour l’édition dans une fenêtre séparée.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Appelé par [DoVerbShow](#doverbshow) après que le contrôle a été rendu visible.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Appelé par [DoVerbUIActivate](#doverbuiactivate) après l’interface utilisateur du contrôle a été activé.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) avant que l’état défait est jeté.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Appelé par [DoVerbHide](#doverbhide) avant que le contrôle soit caché.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) avant que le contrôle est activé en place.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Appelé par [DoVerbOpen](#doverbopen) avant que le contrôle a été ouvert pour l’édition dans une fenêtre séparée.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Appelé par [DoVerbShow](#doverbshow) avant que le contrôle n’ait été rendu visible.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Appelé par [DoVerbUIActivate](#doverbuiactivate) avant que l’interface utilisateur du contrôle n’ait été activée.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informe le contrôle de son site client dans le conteneur.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recommande un schéma de couleurs à l’application du contrôle, le cas échéant. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Définit l’étendue de la zone d’affichage du contrôle.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indique au contrôle les noms de l’application du conteneur et du document de conteneur.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indique au contrôle ce que son surnom est. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Supprime une connexion consultative avec le contrôle.|
|[IOleObjectImpl::Mise à jour](#update)|Mise à jour du contrôle. La mise en œuvre d’ATL S_OK.|

## <a name="remarks"></a>Notes

[L’interface IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) est l’interface principale par laquelle un conteneur communique avec un contrôle. La `IOleObjectImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectImpl::Conseiller

Établit un lien consultatif avec le contrôle.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Voir [IOleObject::Conseiller](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) dans le SDK Windows.

## <a name="ioleobjectimplclose"></a><a name="close"></a>IOleObjectImpl::Fermer

Change l’état de commande de l’exécution à chargé.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Notes

Désactive le contrôle et détruit la fenêtre de contrôle si elle existe. Si le membre des données de la classe de contrôle [CComControlBase: :m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) est VRAI et le paramètre *dwSaveOption* est soit OLECLOSE_SAVEIFDIRTY ou OLECLOSE_PROMPTSAVE, les propriétés de contrôle sont enregistrées avant la fermeture.

Les pointeurs détenus dans les membres de données de classe de contrôle [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) et [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) sont libérés, et les membres de données [CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), et [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) sont fixés à FALSE.

Voir [IOleObject:Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) in the Windows SDK.

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectImpl::DoVerb

Indique au contrôle d’effectuer l’une de ses actions énumérées.

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>Notes

Selon la valeur `iVerb`de , l’une des fonctions d’assistance ATL `DoVerb` est appelé comme suit:

|*iVerb (en)* Valeur|Fonction d’aide DoVerb appelée|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide (en)](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimaire](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow (en)](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate (en)](#doverbuiactivate)|

Voir [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo

Indique au contrôle de jeter tout état de défaire qu’il maintient.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectImpl::DoVerbHide

Désactive et supprime l’interface utilisateur du contrôle et cache le contrôle.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle. Non utilisé dans la mise en œuvre ATL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate

Exécute le contrôle et installe sa fenêtre, mais n’installe pas l’interface utilisateur du contrôle.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle. Non utilisé dans la mise en œuvre ATL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Active le contrôle en place en appelant [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Sauf si le membre `m_bWindowOnly` des données `DoVerbInPlaceActivate` de la classe de contrôle est VRAI, tente d’abord d’activer le contrôle comme un contrôle sans fenêtre (possible que si le conteneur prend en charge [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Si cela échoue, la fonction tente d’activer le contrôle avec des fonctionnalités étendues (possible que si le conteneur prend en charge [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). Si cela échoue, la fonction tente d’activer le contrôle sans fonctionnalités étendues (possible que si le conteneur prend en charge [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). Si l’activation réussit, la fonction informe le conteneur que le contrôle a été activé.

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen

Le contrôle est ouvert dans une fenêtre séparée.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary

Définit l’action prise lorsque l’utilisateur double-clics le contrôle.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Par défaut, défini pour afficher les pages de propriété. Vous pouvez l’emporter dans votre classe de contrôle pour invoquer un comportement différent en double clic; par exemple, lire une vidéo ou aller sur place active.

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectImpl::DoVerbShow

Indique au conteneur de rendre le contrôle visible.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle. Non utilisé dans la mise en œuvre ATL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate

Active l’interface utilisateur du contrôle et informe le conteneur que ses menus sont remplacés par des menus composites.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[dans] Pointer vers le rectangle dans lequel le récipient veut que le contrôle attire.

*hwndParent*<br/>
[dans] Poignée de la fenêtre contenant le contrôle. Non utilisé dans la mise en œuvre ATL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Fournit un recensement des connexions consultatives enregistrées pour ce contrôle.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Notes

Voir [IOleObject:EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) dans le Windows SDK.

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Fournit un recensement des actions enregistrées (verbes) `OleRegEnumVerbs`pour ce contrôle en appelant .

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Notes

Vous pouvez ajouter des verbes au fichier .rgs de votre projet. Par exemple, voir CIRCCTL. RGS dans l’échantillon [CIRC.](../../overview/visual-cpp-samples.md)

Voir [IOleObject:EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) dans le Windows SDK.

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Met le pointeur dans le membre de données de classe de contrôle [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) en *ppClientSite* et incréments le compte de référence sur le pointeur.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Notes

Voir [IOleObject:GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) dans le Windows SDK.

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Récupère les données du Clipboard.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleObject:GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) dans le Windows SDK.

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectImpl::GetExtent

Récupère la taille d’affichage d’un contrôle en cours d’exécution en unités HIMETRIC (0,01 millimètre par unité).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Notes

La taille est stockée dans le membre des données de la classe de contrôle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Voir [IOleObject:GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) dans le Windows SDK.

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Renvoie un pointeur aux informations `OleRegGetMiscStatus`d’état enregistrées pour le contrôle en appelant .

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Notes

Les informations d’état incluent les comportements pris en charge par les données de contrôle et de présentation. Vous pouvez ajouter des informations d’état au fichier .rgs de votre projet.

Voir [IOleObject:GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) dans le Windows SDK.

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectImpl::GetMoniker

Récupère le surnom du contrôle.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleObject:GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) dans le Windows SDK.

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Retourne l’identifiant de classe du contrôle.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Notes

Voir [IOleObject:GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) dans le SDK Windows.

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectImpl::GetUserType

Retourne le nom d’utilisateur du `OleRegGetUserType`contrôle en appelant .

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Notes

Le nom de type utilisateur est utilisé pour l’affichage dans les éléments d’interface utilisateur tels que les menus et les boîtes de dialogue. Vous pouvez modifier le nom de type utilisateur dans le fichier .rgs de votre projet.

Voir [IOleObject:GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) dans le Windows SDK.

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectImpl::InitFromData

Initialise le contrôle à partir de données sélectionnées.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) in the Windows SDK.

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Vérifie si le contrôle est à jour.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleObject:IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) dans le SDK Windows.

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) après l’état défait est jeté.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode avec le code que vous souhaitez exécuter après que l’état d’annulation est jeté.

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Appelé par [DoVerbHide](#doverbhide) après le contrôle est caché.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode avec du code que vous souhaitez exécuter après que le contrôle est caché.

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) après que le contrôle est activé en place.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode avec le code que vous souhaitez exécuter après que le contrôle est activé en place.

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Appelé par [DoVerbOpen](#doverbopen) après le contrôle a été ouvert pour l’édition dans une fenêtre séparée.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacer cette méthode avec le code que vous souhaitez exécuter après que le contrôle a été ouvert pour l’édition dans une fenêtre séparée.

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Appelé par [DoVerbShow](#doverbshow) après que le contrôle a été rendu visible.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode avec le code que vous souhaitez exécuter après que le contrôle a été rendu visible.

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Appelé par [DoVerbUIActivate](#doverbuiactivate) après l’interface utilisateur du contrôle a été activé.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode avec le code que vous souhaitez exécuter après l’activation de l’interface utilisateur du contrôle.

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) avant que l’état défait est jeté.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que l’état défait ne soit jeté, remplacez cette méthode pour retourner une erreur HRESULT.

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Appelé par [DoVerbHide](#doverbhide) avant que le contrôle soit caché.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que le contrôle ne soit caché, remplacez cette méthode pour retourner une erreur HRESULT.

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) avant que le contrôle est activé en place.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que le contrôle ne soit activé, remplacez cette méthode pour renvoyer une erreur HRESULT.

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Appelé par [DoVerbOpen](#doverbopen) avant que le contrôle a été ouvert pour l’édition dans une fenêtre séparée.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que le contrôle ne soit ouvert pour l’édition dans une fenêtre séparée, remplacez cette méthode pour retourner une erreur HRESULT.

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Appelé par [DoVerbShow](#doverbshow) avant que le contrôle n’ait été rendu visible.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que le contrôle ne soit rendu visible, remplacez cette méthode pour retourner une erreur HRESULT.

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Appelé par [DoVerbUIActivate](#doverbuiactivate) avant que l’interface utilisateur du contrôle n’ait été activée.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que l’interface utilisateur du contrôle ne soit activée, remplacez cette méthode pour retourner une erreur HRESULT.

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Informe le contrôle de son site client dans le conteneur.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Notes

La méthode revient alors S_OK.

Voir [IOleObject:SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) dans le Windows SDK.

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Recommande un schéma de couleurs à l’application du contrôle, le cas échéant.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleObject:SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) dans le Windows SDK.

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectImpl::SetExtent

Définit l’étendue de la zone d’affichage du contrôle.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Notes

Sinon, `SetExtent` stocke la `psizel` valeur indiquée par dans le membre des données de la classe de contrôle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Cette valeur est en unités HIMETRIC (0,01 millimètre par unité).

Si le membre des données de la classe de contrôle `SetExtent` [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) est VRAI, stocke également la valeur indiquée par `psizel` dans le membre des données de classe de contrôle [CComControlBase:m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Si le membre des données de la classe de contrôle [CComControlBase: :m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) est VRAI, `SetExtent` appelle `SendOnDataChange` et `SendOnViewChange` d’aviser tous les éviers consultatifs enregistrés auprès du titulaire du conseil que la taille du contrôle a changé.

Voir [IOleObject:SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) dans le Windows SDK.

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Indique au contrôle les noms de l’application du conteneur et du document de conteneur.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleObject:SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) dans le Windows SDK.

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Indique au contrôle ce que son surnom est.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleObject:SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) dans le Windows SDK.

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectImpl::Unadvise

Supprime la connexion consultative stockée dans `m_spOleAdviseHolder` le membre des données de la classe de contrôle.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Notes

Voir [IOleObject:Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) in the Windows SDK.

## <a name="ioleobjectimplupdate"></a><a name="update"></a>IOleObjectImpl::Mise à jour

Mise à jour du contrôle.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleObject::Mise à jour](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX contrôle les interfaces](/windows/win32/com/activex-controls-interfaces)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
