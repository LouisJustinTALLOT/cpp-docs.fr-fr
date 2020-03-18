---
title: IOleObjectImpl, classe
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
ms.openlocfilehash: ded158b0ec862de5b0d0b23dd4b9edb50ad577ef
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417620"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl, classe

Cette classe implémente `IUnknown` et est l’interface principale par le biais de laquelle un conteneur communique avec un contrôle.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IOleObjectImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IOleObjectImpl :: Advise](#advise)|Établit une connexion de notifications avec le contrôle.|
|[IOleObjectImpl :: Close](#close)|Modifie l’état du contrôle de en cours d’exécution en chargé.|
|[IOleObjectImpl ::D oVerb](#doverb)|Indique au contrôle d’exécuter l’une de ses actions énumérées.|
|[IOleObjectImpl ::D oVerbDiscardUndo](#doverbdiscardundo)|Indique au contrôle d’ignorer tout état d’annulation qu’il gère.|
|[IOleObjectImpl ::D oVerbHide](#doverbhide)|Indique au contrôle de supprimer son interface utilisateur de l’affichage.|
|[IOleObjectImpl ::D oVerbInPlaceActivate](#doverbinplaceactivate)|Exécute le contrôle et installe sa fenêtre, mais n’installe pas l’interface utilisateur du contrôle.|
|[IOleObjectImpl ::D oVerbOpen](#doverbopen)|Fait en sorte que le contrôle soit ouvert et modifié dans une fenêtre séparée.|
|[IOleObjectImpl ::D oVerbPrimary](#doverbprimary)|Exécute l’action spécifiée lorsque l’utilisateur double-clique sur le contrôle. Le contrôle définit l’action, généralement pour activer le contrôle sur place.|
|[IOleObjectImpl ::D oVerbShow](#doverbshow)|Affiche un contrôle récemment inséré à l’utilisateur.|
|[IOleObjectImpl ::D oVerbUIActivate](#doverbuiactivate)|Active le contrôle sur place et affiche l’interface utilisateur du contrôle, telle que les menus et les barres d’outils.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Énumère les connexions de notifications du contrôle.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Énumère des actions pour le contrôle.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Récupère le site client du contrôle.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Récupère des données du presse-papiers. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Récupère l’étendue de la zone d’affichage du contrôle.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Récupère l’état du contrôle.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Récupère le moniker du contrôle. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Récupère l’identificateur de classe du contrôle.|
|[IOleObjectImpl::GetUserType](#getusertype)|Récupère le nom de type utilisateur du contrôle.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Initialise le contrôle à partir des données sélectionnées. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Vérifie si le contrôle est à jour. L’implémentation ATL retourne S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Appelée par [DoVerbDiscardUndo](#doverbdiscardundo) après que l’état d’annulation a été ignoré.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Appelée par [DoVerbHide](#doverbhide) une fois que le contrôle est masqué.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Appelée par [DoVerbInPlaceActivate](#doverbinplaceactivate) une fois que le contrôle est activé sur place.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Appelée par [DoVerbOpen](#doverbopen) une fois que le contrôle a été ouvert pour modification dans une fenêtre séparée.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Appelée par [DoVerbShow](#doverbshow) une fois que le contrôle a été rendu visible.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Appelée par [DoVerbUIActivate](#doverbuiactivate) après l’activation de l’interface utilisateur du contrôle.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Appelée par [DoVerbDiscardUndo](#doverbdiscardundo) avant que l’état d’annulation soit ignoré.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Appelée par [DoVerbHide](#doverbhide) avant que le contrôle soit masqué.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Appelée par [DoVerbInPlaceActivate](#doverbinplaceactivate) avant que le contrôle soit activé sur place.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Appelée par [DoVerbOpen](#doverbopen) avant que le contrôle ne soit ouvert pour être modifié dans une fenêtre séparée.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Appelée par [DoVerbShow](#doverbshow) avant que le contrôle soit rendu visible.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Appelée par [DoVerbUIActivate](#doverbuiactivate) avant l’activation de l’interface utilisateur du contrôle.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indique au contrôle à propos de son site client dans le conteneur.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recommande un modèle de couleurs à l’application du contrôle, le cas échéant. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleObjectImpl :: setraverste](#setextent)|Définit l’étendue de la zone d’affichage du contrôle.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indique au contrôle les noms de l’application conteneur et du document conteneur.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indique au contrôle le nom de son moniker. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleObjectImpl :: Unadvise](#unadvise)|Supprime une connexion de notifications avec le contrôle.|
|[IOleObjectImpl :: Update](#update)|Met à jour le contrôle. L’implémentation ATL retourne S_OK.|

## <a name="remarks"></a>Notes

L’interface [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) est l’interface principale par le biais de laquelle un conteneur communique avec un contrôle. La classe `IOleObjectImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

##  <a name="advise"></a>IOleObjectImpl :: Advise

Établit une connexion de notifications avec le contrôle.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject :: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) dans le SDK Windows.

##  <a name="close"></a>IOleObjectImpl :: Close

Modifie l’état du contrôle de en cours d’exécution en chargé.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Notes

Désactive le contrôle et détruit la fenêtre de contrôle, le cas échéant. Si le membre de données de la classe de contrôle [CComControlBase :: m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) a la valeur true et que le paramètre *dwSaveOption* est OLECLOSE_SAVEIFDIRTY ou OLECLOSE_PROMPTSAVE, les propriétés du contrôle sont enregistrées avant la fermeture.

Les pointeurs détenus dans la classe de contrôle membres de données [CComControlBase :: m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) et [CComControlBase :: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) sont libérés, et les membres de données [CComControlBase :: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase :: m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)et [CComControlBase :: m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) ont la valeur false.

Consultez [IOleObject :: Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) dans la SDK Windows.

##  <a name="doverb"></a>IOleObjectImpl ::D oVerb

Indique au contrôle d’exécuter l’une de ses actions énumérées.

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

Selon la valeur de `iVerb`, l’une des fonctions d’assistance ATL `DoVerb` est appelée comme suit :

|*iVerb* Ajoutée|Fonction d’assistance DoVerb appelée|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase ::D oVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Consultez [IOleObject ::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

##  <a name="doverbdiscardundo"></a>IOleObjectImpl ::D oVerbDiscardUndo

Indique au contrôle d’ignorer tout état d’annulation qu’il gère.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="doverbhide"></a>IOleObjectImpl ::D oVerbHide

Désactive et supprime l’interface utilisateur du contrôle et masque le contrôle.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle. Non utilisé dans l’implémentation ATL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="doverbinplaceactivate"></a>IOleObjectImpl ::D oVerbInPlaceActivate

Exécute le contrôle et installe sa fenêtre, mais n’installe pas l’interface utilisateur du contrôle.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle. Non utilisé dans l’implémentation ATL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Active le contrôle en place en appelant [CComControlBase :: InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). À moins que le membre de données de la classe de contrôle `m_bWindowOnly` ait la valeur TRUE, `DoVerbInPlaceActivate` tente d’abord d’activer le contrôle en tant que contrôle sans fenêtre (possible uniquement si le conteneur prend en charge [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). En cas d’échec, la fonction tente d’activer le contrôle avec des fonctionnalités étendues (possible uniquement si le conteneur prend en charge [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). En cas d’échec, la fonction tente d’activer le contrôle sans fonctionnalités étendues (possible uniquement si le conteneur prend en charge [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). Si l’activation réussit, la fonction notifie le conteneur que le contrôle a été activé.

##  <a name="doverbopen"></a>IOleObjectImpl ::D oVerbOpen

Fait en sorte que le contrôle soit ouvert et modifié dans une fenêtre séparée.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="doverbprimary"></a>IOleObjectImpl ::D oVerbPrimary

Définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Par défaut, définissez pour afficher les pages de propriétés. Vous pouvez substituer cette méthode dans votre classe de contrôle pour appeler un comportement différent en cas de double-clic ; par exemple, lisez une vidéo ou passez à l’actif sur place.

##  <a name="doverbshow"></a>IOleObjectImpl ::D oVerbShow

Indique au conteneur que le contrôle doit être visible.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle. Non utilisé dans l’implémentation ATL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="doverbuiactivate"></a>IOleObjectImpl ::D oVerbUIActivate

Active l’interface utilisateur du contrôle et notifie le conteneur que ses menus sont remplacés par des menus composites.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
dans Pointeur vers le rectangle dans lequel le conteneur souhaite que le contrôle dessine.

*hwndParent*<br/>
dans Handle de la fenêtre contenant le contrôle. Non utilisé dans l’implémentation ATL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Fournit une énumération des connexions de notifications inscrites pour ce contrôle.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject :: EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) dans le SDK Windows.

##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Fournit une énumération des actions inscrites (verbes) pour ce contrôle en appelant `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Notes

Vous pouvez ajouter des verbes au fichier. RGS de votre projet. Par exemple, consultez CIRCCTL. RGS dans l’exemple [CIRC](../../overview/visual-cpp-samples.md) .

Consultez [IOleObject :: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) dans le SDK Windows.

##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Place le pointeur dans la classe de contrôle Data Member [CComControlBase :: m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) dans *ppClientSite* et incrémente le décompte de références sur le pointeur.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject :: GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) dans le SDK Windows.

##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Récupère des données du presse-papiers.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) dans le SDK Windows.

##  <a name="getextent"></a>IOleObjectImpl::GetExtent

Récupère la taille d’affichage d’un contrôle en cours d’exécution en unités HIMETRIC (0,01 millimètres par unité).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Notes

La taille est stockée dans le membre de données de la classe de contrôle [CComControlBase :: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Consultez [IOleObject :: GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) dans le SDK Windows.

##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Retourne un pointeur désignant les informations d’État inscrites pour le contrôle en appelant `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Notes

Les informations d’État incluent les comportements pris en charge par les données de contrôle et de présentation. Vous pouvez ajouter des informations d’État au fichier. RGS de votre projet.

Consultez [IOleObject :: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) dans le SDK Windows.

##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker

Récupère le moniker du contrôle.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) dans le SDK Windows.

##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Retourne l’identificateur de classe du contrôle.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject :: GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) dans le SDK Windows.

##  <a name="getusertype"></a>IOleObjectImpl::GetUserType

Retourne le nom de type utilisateur du contrôle en appelant `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Notes

Le nom de type utilisateur est utilisé pour l’affichage dans les éléments d’interface utilisateur, tels que les menus et les boîtes de dialogue. Vous pouvez modifier le nom du type d’utilisateur dans le fichier. RGS de votre projet.

Consultez [IOleObject :: GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) dans le SDK Windows.

##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData

Initialise le contrôle à partir des données sélectionnées.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) dans le SDK Windows.

##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Vérifie si le contrôle est à jour.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) dans le SDK Windows.

##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Appelée par [DoVerbDiscardUndo](#doverbdiscardundo) après que l’état d’annulation a été ignoré.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode par le code que vous souhaitez exécuter après que l’état d’annulation a été ignoré.

##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Appelée par [DoVerbHide](#doverbhide) une fois que le contrôle est masqué.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode par le code que vous souhaitez exécuter une fois que le contrôle est masqué.

##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Appelée par [DoVerbInPlaceActivate](#doverbinplaceactivate) une fois que le contrôle est activé sur place.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode par le code que vous souhaitez exécuter une fois que le contrôle est activé sur place.

##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Appelée par [DoVerbOpen](#doverbopen) une fois que le contrôle a été ouvert pour modification dans une fenêtre séparée.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode par le code que vous souhaitez exécuter une fois que le contrôle a été ouvert pour modification dans une fenêtre distincte.

##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Appelée par [DoVerbShow](#doverbshow) une fois que le contrôle a été rendu visible.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécuter une fois que le contrôle a été rendu visible.

##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Appelée par [DoVerbUIActivate](#doverbuiactivate) après l’activation de l’interface utilisateur du contrôle.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Remplacez cette méthode par le code que vous souhaitez exécuter après l’activation de l’interface utilisateur du contrôle.

##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Appelée par [DoVerbDiscardUndo](#doverbdiscardundo) avant que l’état d’annulation soit ignoré.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher l’état d’annulation d’être ignoré, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Appelée par [DoVerbHide](#doverbhide) avant que le contrôle soit masqué.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher le contrôle d’être masqué, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Appelée par [DoVerbInPlaceActivate](#doverbinplaceactivate) avant que le contrôle soit activé sur place.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher l’activation du contrôle sur place, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Appelée par [DoVerbOpen](#doverbopen) avant que le contrôle ne soit ouvert pour être modifié dans une fenêtre séparée.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher l’ouverture du contrôle en vue de sa modification dans une fenêtre distincte, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Appelée par [DoVerbShow](#doverbshow) avant que le contrôle soit rendu visible.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher le contrôle d’être rendu visible, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Appelée par [DoVerbUIActivate](#doverbuiactivate) avant l’activation de l’interface utilisateur du contrôle.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher l’activation de l’interface utilisateur du contrôle, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Indique au contrôle à propos de son site client dans le conteneur.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Notes

La méthode retourne ensuite S_OK.

Consultez [IOleObject :: SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) dans le SDK Windows.

##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Recommande un modèle de couleurs à l’application du contrôle, le cas échéant.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) dans le SDK Windows.

##  <a name="setextent"></a>IOleObjectImpl :: setraverste

Définit l’étendue de la zone d’affichage du contrôle.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Notes

Dans le cas contraire, `SetExtent` stocke la valeur désignée par `psizel` dans le membre de classe de contrôle [CComControlBase :: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Cette valeur est en unités HIMETRIC (0,01 millimètres par unité).

Si le membre de la classe de contrôle [CComControlBase :: m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) a la valeur TRUE, `SetExtent` stocke également la valeur vers laquelle pointe la `psizel` dans la classe de contrôle Data Member [CComControlBase :: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Si le membre de la classe de contrôle [CComControlBase :: m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) a la valeur TRUE, `SetExtent` appelle `SendOnDataChange` et `SendOnViewChange` pour notifier tous les récepteurs de notifications inscrits auprès du détenteur de la notification que la taille du contrôle a changé.

Consultez [IOleObject ::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) seversion dans la SDK Windows.

##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Indique au contrôle les noms de l’application conteneur et du document conteneur.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) dans le SDK Windows.

##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Indique au contrôle le nom de son moniker.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) dans le SDK Windows.

##  <a name="unadvise"></a>IOleObjectImpl :: Unadvise

Supprime la connexion de notifications stockée dans le membre de données de `m_spOleAdviseHolder` de la classe de contrôle.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject :: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) dans le SDK Windows.

##  <a name="update"></a>IOleObjectImpl :: Update

Met à jour le contrôle.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleObject :: Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
