---
title: Ioleobjectimpl, classe
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
ms.openlocfilehash: 5a815023d340839068873c32f1477d33053b13b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274930"
---
# <a name="ioleobjectimpl-class"></a>Ioleobjectimpl, classe

Cette classe implémente `IUnknown` et constitue l’interface principale par le biais duquel un conteneur communique avec un contrôle.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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

|Nom|Description|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|Établit une connexion de notifications avec le contrôle.|
|[IOleObjectImpl::Close](#close)|Modifie l’état du contrôle de l’exécution à charger.|
|[IOleObjectImpl::DoVerb](#doverb)|Indique au contrôle pour effectuer l’une de ses actions énumérées.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Indique au contrôle d’ignorer aucun il maintient l’état d’annulation.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Indique le contrôle à supprimer de son interface utilisateur à partir de la vue.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Exécute le contrôle et installe sa fenêtre, mais n’installe pas l’interface utilisateur du contrôle.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Force le contrôle à être modifié ouvrir dans une fenêtre distincte.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Exécute l’action spécifiée lorsque l’utilisateur double-clique sur le contrôle. Le contrôle définit l’action, généralement pour activer le contrôle sur place.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Illustre un contrôle qui vient d’être inséré à l’utilisateur.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Active le contrôle sur place et montre l’interface du contrôle utilisateur, notamment les menus et barres d’outils.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Énumère les connexions de notifications du contrôle.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Énumère les actions pour le contrôle.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Récupère le site du client du contrôle.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Récupère des données à partir du Presse-papiers. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Récupère l’étendue de la zone d’affichage du contrôle.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Récupère l’état du contrôle.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Récupère le moniker du contrôle. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Récupère l’identificateur de classe du contrôle.|
|[IOleObjectImpl::GetUserType](#getusertype)|Récupère le nom du contrôle utilisateur-type.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Initialise le contrôle à partir de données sélectionnée. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Vérifie si le contrôle est à jour. L’implémentation de ATL retourne S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) une fois que l’état d’annulation est ignorée.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Appelé par [DoVerbHide](#doverbhide) une fois que le contrôle est masqué.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) une fois que le contrôle est activé sur place.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Appelé par [DoVerbOpen](#doverbopen) une fois que le contrôle a été ouvert pour modification dans une fenêtre distincte.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Appelé par [DoVerbShow](#doverbshow) une fois que le contrôle a été rendu visible.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Appelé par [DoVerbUIActivate](#doverbuiactivate) après l’activation de l’interface du contrôle utilisateur.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) avant l’annulation état est ignoré.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Appelé par [DoVerbHide](#doverbhide) avant que le contrôle est masqué.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) avant que le contrôle est activé sur place.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Appelé par [DoVerbOpen](#doverbopen) avant que le contrôle a été ouvert pour modification dans une fenêtre distincte.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Appelé par [DoVerbShow](#doverbshow) avant que le contrôle a été rendu visible.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Appelé par [DoVerbUIActivate](#doverbuiactivate) avant l’activation de l’interface du contrôle utilisateur.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indique au contrôle sur son site client dans le conteneur.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recommande un jeu de couleurs de l’application du contrôle, le cas échéant. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Définit l’étendue de la zone d’affichage du contrôle.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indique au contrôle les noms de l’application de conteneur et d’un document conteneur.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indique au contrôle son moniker What ' s. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Supprime une connexion de notifications avec le contrôle.|
|[IOleObjectImpl::Update](#update)|Met à jour le contrôle. L’implémentation de ATL retourne S_OK.|

## <a name="remarks"></a>Notes

Le [IOleObject](/windows/desktop/api/oleidl/nn-oleidl-ioleobject) interface est l’interface principale par le biais duquel un conteneur communique avec un contrôle. Classe `IOleObjectImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="advise"></a>  IOleObjectImpl::Advise

Établit une connexion de notifications avec le contrôle.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) dans le Kit de développement logiciel Windows.

##  <a name="close"></a>  IOleObjectImpl::Close

Modifie l’état du contrôle de l’exécution à charger.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Notes

Désactive le contrôle et détruit la fenêtre de contrôle s’il existe. Si le contrôle le membre de données de classe [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) a la valeur TRUE et le *dwSaveOption* paramètre est OLECLOSE_SAVEIFDIRTY ou OLECLOSE_PROMPTSAVE, sont les propriétés du contrôle enregistré avant sa fermeture.

Les pointeurs contenues dans les données membres de classe de contrôle [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) et [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) sont publiées et les membres de données [CComControlBase :: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), et [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) sont définies sur FALSE.

Consultez [IOleObject::Close](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-close) dans le Kit de développement logiciel Windows.

##  <a name="doverb"></a>  IOleObjectImpl::DoVerb

Indique au contrôle pour effectuer l’une de ses actions énumérées.

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

Selon la valeur de `iVerb`, un de la bibliothèque ATL `DoVerb` fonctions d’assistance est appelée comme suit :

|*iVerb* valeur|Fonction d’assistance de DoVerb appelée|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Consultez [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) dans le Kit de développement logiciel Windows.

##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo

Indique au contrôle d’ignorer aucun il maintient l’état d’annulation.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide

Désactive et supprime l’interface du contrôle utilisateur et masque le contrôle.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle. Pas utilisé dans l’implémentation de ATL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate

Exécute le contrôle et installe sa fenêtre, mais n’installe pas l’interface utilisateur du contrôle.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle. Pas utilisé dans l’implémentation de ATL.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Active le contrôle en place en appelant [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). À moins que membre de données de la classe de contrôle `m_bWindowOnly` a la valeur TRUE, `DoVerbInPlaceActivate` tente d’abord activer le contrôle comme un contrôle sans fenêtre (possible uniquement si le conteneur prend en charge [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Si cette tentative échoue, la fonction tente d’activer le contrôle avec des fonctionnalités étendues (possible uniquement si le conteneur prend en charge [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)). Si cette tentative échoue, la fonction tente d’activer le contrôle sans fonctionnalités étendues (possible uniquement si le conteneur prend en charge [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)). Si l’activation réussit, la fonction informe le conteneur pour que le contrôle a été activé.

##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen

Force le contrôle à être modifié ouvrir dans une fenêtre distincte.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary

Définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Par défaut, configuré pour afficher les pages de propriétés. Vous pouvez le remplacer dans votre classe de contrôle pour appeler un comportement différent sur le double-clic ; par exemple, lire une vidéo ou accédez actif en place.

##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow

Indique au conteneur pour rendre le contrôle visible.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle. Pas utilisé dans l’implémentation de ATL.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate

Active l’interface du contrôle utilisateur et informe le conteneur que ses menus sont remplacés par les menus composites.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
[in] Pointeur vers le rectangle le conteneur souhaite que le contrôle à dessiner dans.

*hwndParent*<br/>
[in] Handle de la fenêtre qui contient le contrôle. Pas utilisé dans l’implémentation de ATL.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise

Fournit une énumération des connexions de notifications enregistrées pour ce contrôle.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject::EnumAdvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumadvise) dans le Kit de développement logiciel Windows.

##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs

Fournit une énumération des actions inscrites (verbes) pour ce contrôle en appelant `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Notes

Vous pouvez ajouter des verbes pour le fichier .rgs du projet. Par exemple, consultez CIRCCTL. RGS dans le [CERC](../../overview/visual-cpp-samples.md) exemple.

Consultez [IOleObject::EnumVerbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs) dans le Kit de développement logiciel Windows.

##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite

Place le pointeur dans le membre de données de classe de contrôle [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) dans *ppClientSite* et incrémente le décompte de références sur le pointeur.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject::GetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclientsite) dans le Kit de développement logiciel Windows.

##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData

Récupère des données à partir du Presse-papiers.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject::GetClipboardData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) dans le Kit de développement logiciel Windows.

##  <a name="getextent"></a>  IOleObjectImpl::GetExtent

Récupère la taille d’affichage d’un contrôle en cours d’exécution en unités HIMETRIC (0,01 millimètre par unité).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Notes

La taille est stockée dans le membre de données de classe de contrôle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Consultez [IOleObject::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getextent) dans le Kit de développement logiciel Windows.

##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus

Retourne un pointeur vers des informations de statut d’inscription pour le contrôle en appelant `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Notes

Les informations d’état incluent des comportements pris en charge par les données de contrôle et de présentation. Vous pouvez ajouter des informations d’état pour le fichier .rgs du projet.

Consultez [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) dans le Kit de développement logiciel Windows.

##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker

Récupère le moniker du contrôle.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject::GetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmoniker) dans le Kit de développement logiciel Windows.

##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID

Retourne l’identificateur de classe du contrôle.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject::GetUserClassID](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getuserclassid) dans le Kit de développement logiciel Windows.

##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType

Retourne le nom du type d’utilisateur du contrôle en appelant `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Notes

Le nom du type d’utilisateur est utilisé pour l’affichage dans les éléments des interfaces utilisateur comme les menus et boîtes de dialogue. Vous pouvez modifier le nom de type d’utilisateur dans le fichier .rgs du projet.

Consultez [IOleObject::GetUserType](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getusertype) dans le Kit de développement logiciel Windows.

##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData

Initialise le contrôle à partir de données sélectionnée.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) dans le Kit de développement logiciel Windows.

##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate

Vérifie si le contrôle est à jour.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleObject::IsUpToDate](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-isuptodate) dans le Kit de développement logiciel Windows.

##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo

Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) une fois que l’état d’annulation est ignorée.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécutée après que l’état d’annulation est ignorée.

##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide

Appelé par [DoVerbHide](#doverbhide) une fois que le contrôle est masqué.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécutée après que le contrôle est masqué.

##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate

Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) une fois que le contrôle est activé sur place.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécuté une fois le contrôle est activé sur place.

##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen

Appelé par [DoVerbOpen](#doverbopen) une fois que le contrôle a été ouvert pour modification dans une fenêtre distincte.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécuter une fois le contrôle a été ouvert pour modification dans une fenêtre distincte.

##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow

Appelé par [DoVerbShow](#doverbshow) une fois que le contrôle a été rendu visible.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécutée après que le contrôle a été rendu visible.

##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate

Appelé par [DoVerbUIActivate](#doverbuiactivate) après l’activation de l’interface du contrôle utilisateur.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Substituez cette méthode avec le code que vous souhaitez exécutée après l’activation de l’interface du contrôle utilisateur.

##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo

Appelé par [DoVerbDiscardUndo](#doverbdiscardundo) avant l’annulation état est ignoré.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher l’état d’annulation de rejet, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide

Appelé par [DoVerbHide](#doverbhide) avant que le contrôle est masqué.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher le contrôle de masqué, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate

Appelé par [DoVerbInPlaceActivate](#doverbinplaceactivate) avant que le contrôle est activé sur place.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher le contrôle d’en cours d’activation en place, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen

Appelé par [DoVerbOpen](#doverbopen) avant que le contrôle a été ouvert pour modification dans une fenêtre distincte.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher le contrôle ne soit ouvert pour modification dans une fenêtre distincte, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow

Appelé par [DoVerbShow](#doverbshow) avant que le contrôle a été rendu visible.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour empêcher l’affichage du contrôle, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate

Appelé par [DoVerbUIActivate](#doverbuiactivate) avant l’activation de l’interface du contrôle utilisateur.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour éviter que l’interface du contrôle utilisateur en cours d’activation, substituez cette méthode pour retourner une erreur HRESULT.

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

Indique au contrôle sur son site client dans le conteneur.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Notes

Ensuite, la méthode retourne S_OK.

Consultez [l’IOleObject::SetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setclientsite) dans le Kit de développement logiciel Windows.

##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme

Recommande un jeu de couleurs de l’application du contrôle, le cas échéant.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) dans le Kit de développement logiciel Windows.

##  <a name="setextent"></a>  IOleObjectImpl::SetExtent

Définit l’étendue de la zone d’affichage du contrôle.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Notes

Sinon, `SetExtent` stocke la valeur vers laquelle pointée `psizel` dans le membre de données de classe de contrôle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Cette valeur est en unités HIMETRIC (0,01 millimètre par unité).

Si le contrôle le membre de données de classe [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) a la valeur TRUE, `SetExtent` stocke également la valeur vers laquelle pointée `psizel` dans le membre de données de classe de contrôle [CComControlBase::m_sizeNatural ](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Si le contrôle le membre de données de classe [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) a la valeur TRUE, `SetExtent` appels `SendOnDataChange` et `SendOnViewChange` pour notifier les récepteurs de toutes les notifications inscrits avec le détenteur de notifications qui a la taille de contrôle modifié.

Consultez [IOleObject::SetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setextent) dans le Kit de développement logiciel Windows.

##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames

Indique au contrôle les noms de l’application de conteneur et d’un document conteneur.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleObject::SetHostNames](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-sethostnames) dans le Kit de développement logiciel Windows.

##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker

Indique au contrôle son moniker What ' s.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleObject::SetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setmoniker) dans le Kit de développement logiciel Windows.

##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise

Supprime la connexion consultative stockée dans la classe de contrôle `m_spOleAdviseHolder` membre de données.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) dans le Kit de développement logiciel Windows.

##  <a name="update"></a>  IOleObjectImpl::Update

Met à jour le contrôle.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleObject::Update](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-update) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
