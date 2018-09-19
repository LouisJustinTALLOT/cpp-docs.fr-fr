---
title: CComControlBase, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
dev_langs:
- C++
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18666cc619796bc7ee0216eb9cdf020bd8d8a6f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035745"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase, classe

Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Remplacer si votre `m_nAppearance` propriétés stock n’est pas de type **court**.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Constructeur.|
|[CComControlBase :: ~ CComControlBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Vérifie que le *iVerb* paramètre utilisé par `IOleObjectImpl::DoVerb` soit active l’interface du contrôle utilisateur (*iVerb* est égal à OLEIVERB_UIACTIVATE), définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle (*iVerb* est égal à OLEIVERB_PRIMARY), affiche le contrôle (*iVerb* est égal à OLEIVERB_SHOW), ou l’activation du contrôle (*iVerb* est égal à OLEIVERB _INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Vérifie que le *iVerb* paramètre utilisé par `IOleObjectImpl::DoVerb` provoque l’interface du contrôle utilisateur à activer et retourne la valeur TRUE.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Affiche les pages de propriétés du contrôle.|
|[CComControlBase::FireViewChange](#fireviewchange)|Appelez cette méthode pour indiquer au conteneur doit redessiner le contrôle, ou informer les récepteurs de notifications enregistrés l’affichage du contrôle a changé.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Récupère les DISPID_AMBIENT_APPEARANCE, l’apparence actuelle définition du contrôle : 0 pour plat et 1 pour 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Récupère les DISPID_AMBIENT_AUTOCLIP, un indicateur qui spécifie si le conteneur prend en charge le découpage automatique de la zone d’affichage de contrôle.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Récupère les DISPID_AMBIENT_BACKCOLOR, la couleur d’arrière-plan ambiante pour tous les contrôles, définis par le conteneur.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Récupère les DISPID_AMBIENT_CHARSET, ambiante jeu de caractères pour tous les contrôles, définis par le conteneur.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Récupère les DISPID_AMBIENT_CODEPAGE, ambiante jeu de caractères pour tous les contrôles, définis par le conteneur.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Récupère les DISPID_AMBIENT_DISPLAYASDEFAULT, un indicateur qui a la valeur TRUE si le conteneur a marqué le contrôle de ce site pour être un bouton par défaut, et par conséquent un contrôle button doit se dessiner lui-même avec une image épaisse.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Récupère le DISPID_AMBIENT_DISPLAYNAME, le nom du conteneur a fourni au contrôle.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Récupère un pointeur vers le conteneur d’ambiant `IFont` interface.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Récupère un pointeur vers le conteneur d’ambiant `IFontDisp` interface de dispatch.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Récupère les DISPID_AMBIENT_FORECOLOR, la couleur de premier plan ambiante pour tous les contrôles, définis par le conteneur.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Récupère le DISPID_AMBIENT_LOCALEID, l’identificateur de la langue utilisée par le conteneur.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Récupère les DISPID_AMBIENT_MESSAGEREFLECT, un indicateur qui spécifie si le conteneur souhaite recevoir des messages de fenêtre (par exemple, WM_DRAWITEM) en tant qu’événements.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Récupère DISPID_AMBIENT_PALETTE, permettant d’accéder aux HPALETTE du conteneur.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Récupère la propriété de conteneur spécifiée par *id*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Récupère les DISPID_AMBIENT_RIGHTTOLEFT, la direction dans laquelle le contenu est affiché par le conteneur.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Récupère les DISPID_AMBIENT_SCALEUNITS, unités d’ambiante du conteneur (telles que des pouces ou centimètres) pour l’étiquetage affiche.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Récupère les DISPID_AMBIENT_SHOWGRABHANDLES, un indicateur qui spécifie si le conteneur autorise le contrôle afficher les poignées de manipulation pour lui-même lorsqu’il est actif.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Récupère les DISPID_AMBIENT_SHOWHATCHING, un indicateur qui spécifie si le conteneur autorise le contrôle lui-même affiche un motif hachuré lors de l’interface utilisateur est active.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Récupère les DISPID_AMBIENT_SUPPORTSMNEMONICS, un indicateur qui spécifie si le conteneur prend en charge les mnémoniques clavier.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Récupère les DISPID_AMBIENT_TEXTALIGN, l’alignement de texte préféré par le conteneur : 0 pour l’alignement général (texte de droite, de chiffres à gauche), 1 pour l’alignement à gauche, 2 pour l’alignement au centre et 3 pour l’alignement à droite.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Récupère les DISPID_AMBIENT_TOPTOBOTTOM, la direction dans laquelle le contenu est affiché par le conteneur.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Récupère les DISPID_AMBIENT_UIDEAD, un indicateur qui spécifie si le conteneur puisse exiger le contrôle de répondre aux actions de l’interface utilisateur.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Récupère les DISPID_AMBIENT_USERMODE, un indicateur indiquant si le conteneur est en mode exécution (TRUE) ou en mode design (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Retourne la valeur du membre de données `m_bRequiresSave`.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Récupère les coordonnées x et y valeurs de numérateur et dénominateur du facteur de zoom pour un contrôle est activé pour la modification sur place.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Provoque la transition de l’état inactif à l’état le verbe dans le contrôle *iVerb* indique.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Appelez cette méthode pour interroger le site de contrôle pour un pointeur vers l’interface identifiée.|
|[CComControlBase::OnDraw](#ondraw)|Substituez cette méthode pour dessiner votre contrôle.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|La valeur par défaut `OnDrawAdvanced` prépare un contexte de périphérique normalisé pour le dessin, puis appelle la classe de votre contrôle `OnDraw` (méthode).|
|[CComControlBase::OnKillFocus](#onkillfocus)|Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu le focus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Vérifie que l’interface utilisateur est en mode utilisateur, puis active le contrôle.|
|[CComControlBase::OnPaint](#onpaint)|Prépare le conteneur pour la peinture, obtient la zone cliente du contrôle, puis appelle la classe de contrôle `OnDraw` (méthode).|
|[CComControlBase::OnSetFocus](#onsetfocus)|Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur du contrôle a obtenu le focus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Substituez cette méthode pour fournir votre propre clavier gestionnaires d’accélérateur.|
|[CComControlBase::SendOnClose](#sendonclose)|Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été fermé.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que les données de contrôle a changé.|
|[CComControlBase::SendOnRename](#sendonrename)|Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a un nouveau moniker.|
|[CComControlBase::SendOnSave](#sendonsave)|Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été enregistré.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Avertit que tous les enregistrés des récepteurs de notifications que l’affichage du contrôle a changé.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Définit ou supprime le focus clavier vers ou depuis le contrôle.|
|[CComControlBase::SetDirty](#setdirty)|Définit le membre de données `m_bRequiresSave` à la valeur de *bDirty*.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Indicateur précisant que le contrôle ne peut pas être une autre taille.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Indicateur qui spécifie si `IDataObjectImpl::GetData` et `CComControlBase::GetZoomInfo` doit définir la taille du contrôle à partir de `m_sizeNatural` plutôt qu’à partir `m_sizeExtent`.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Indicateur qui spécifie si `IDataObjectImpl::GetData` doit utiliser des unités HIMETRIC et pas des pixels lors du dessin.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Indicateur qui spécifie que le contrôle est actif en place.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Indicateur précisant s’il le prend en charge du conteneur le `IOleInPlaceSiteEx` interface et OCX96 contrôlent les fonctionnalités, tels que les contrôles sans fenêtre et sans scintillement.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Indicateur déterminant si le contrôle a négocié avec le conteneur sur la prise en charge des fonctionnalités de contrôle OCX96 (tels que les contrôles sans fenêtre et sans scintillement), et si le contrôle est fenêtrées ou sans fenêtre.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Indicateur précisant que le contrôle souhaite Recomposer sa présentation lorsque le conteneur change de taille d’affichage du contrôle.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Indicateur précisant que le contrôle a changé depuis son dernier enregistrement.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Indicateur qui spécifie le contrôle souhaite redimensionner son extension naturelle (sa taille physique non ajustée) lorsque le conteneur change la taille d’affichage du contrôle.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Indicateur qui spécifie l’interface du contrôle utilisateur, notamment les menus et barres d’outils, est actif.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Indicateur précisant que le contrôle à l’aide de la région de la fenêtre du conteneur.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Indicateur précisant le contrôle a été sans fenêtre, mais ne peut pas forcément sans fenêtre maintenant.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Indicateur précisant que le contrôle doit être fenêtré, même si le conteneur prend en charge les contrôles sans fenêtre.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Indicateur qui spécifie que le contrôle est sans fenêtre.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contient une référence vers le handle de fenêtre associé au contrôle.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Le nombre de fois où le conteneur a figé événements (refusés d’accepter les événements) sans un libérer les intervenant des événements (acceptation d’événements).|
|[CComControlBase::m_rcPos](#m_rcpos)|La position en pixels du contrôle, exprimée dans les coordonnées du conteneur.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|L’étendue du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres) pour un affichage particulier.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|La taille physique du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Un pointeur direct vers la connexion de notifications sur le conteneur (le conteneur [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Un `CComDispatchDriver` objet qui vous permet de récupérer et définir les propriétés du conteneur via une `IDispatch` pointeur.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Pointeur vers le site du client du contrôle au sein du conteneur.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Fournit qu'une norme signifie pour maintenir les connexions de notifications entre les objets de données et de récepteurs de notifications.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Un pointeur vers le conteneur [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) pointeur d’interface.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Fournit une implémentation standard d’un moyen de contenir des connexions de notifications.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer des contrôles ATL. [CComControl, classe](../../atl/reference/ccomcontrol-class.md) dérive `CComControlBase`. Lorsque vous créez un contrôle DHTML Edit ou de contrôle Standard à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre classe à partir de `CComControlBase`.

Pour plus d’informations sur la création d’un contrôle, consultez le [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

Remplacer si votre `m_nAppearance` propriétés stock n’est pas de type **court**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Notes

L’Assistant contrôle ATL ajoute `m_nAppearance` boursiers de propriété de type short. Substituer `AppearanceType` si vous utilisez un autre type de données.

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

Constructeur.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Le handle vers la fenêtre associé au contrôle.

### <a name="remarks"></a>Notes

Initialise la taille de contrôle aux unités HIMETRIC de 5080 X 5080 (2 « X 2 ») et initialise le `CComControlBase` des valeurs de membres de données à NULL ou à FALSE.

##  <a name="dtor"></a>  CComControlBase :: ~ CComControlBase

Destructeur.

```
~CComControlBase();
```

### <a name="remarks"></a>Notes

Si le contrôle est fenêtré, `~CComControlBase` il détruit en appelant [DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

Récupère un pointeur vers l'interface demandée.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Paramètres

*IID*<br/>
Le GUID de l’interface demandée.

*PPV*<br/>
Un pointeur vers le pointeur d’interface identifié par *iid*, ou NULL si l’interface est introuvable.

### <a name="remarks"></a>Notes

gère seulement des interfaces dans la table de mappage COM.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

Vérifie que le *iVerb* paramètre utilisé par `IOleObjectImpl::DoVerb` soit active l’interface du contrôle utilisateur (*iVerb* est égal à OLEIVERB_UIACTIVATE), définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle (*iVerb* est égal à OLEIVERB_PRIMARY), affiche le contrôle (*iVerb* est égal à OLEIVERB_SHOW), ou l’activation du contrôle (*iVerb* est égal à OLEIVERB _INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Valeur qui indique l’action à effectuer par `DoVerb`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si *iVerb* est égal à OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW ou OLEIVERB_INPLACEACTIVATE ; sinon, retourne FALSE.

### <a name="remarks"></a>Notes

Vous pouvez remplacer cette méthode pour définir votre propre verbe d’activation.

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

Vérifie que le *iVerb* paramètre utilisé par `IOleObjectImpl::DoVerb` provoque l’interface du contrôle utilisateur à activer et retourne la valeur TRUE.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Valeur qui indique l’action à effectuer par `DoVerb`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si *iVerb* est égal à OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW ou OLEIVERB_INPLACEACTIVATE. Sinon, la méthode retourne FALSE.

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

Affiche les pages de propriétés du contrôle.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
Réservé.

*hwndParent*<br/>
Handle de la fenêtre qui contient le contrôle.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

Appelez cette méthode pour indiquer au conteneur doit redessiner le contrôle, ou informer les récepteurs de notifications enregistrés l’affichage du contrôle a changé.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Si le contrôle est actif (le membre de données de classe de contrôle [CComControlBase::m_bInPlaceActive](#m_binplaceactive) a la valeur TRUE), informe le conteneur que vous souhaitez redessiner l’ensemble du contrôle. Si le contrôle est inactif, avertit le contrôle de l’inscrit récepteurs de notifications (via le membre de données de classe de contrôle [CComControlBase::m_spAdviseSink](#m_spadvisesink)) que l’affichage du contrôle a changé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

Récupère les DISPID_AMBIENT_APPEARANCE, l’apparence actuelle définition du contrôle : 0 pour plat et 1 pour 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Paramètres

*nAppearance*<br/>
La propriété DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

Récupère les DISPID_AMBIENT_AUTOCLIP, un indicateur qui spécifie si le conteneur prend en charge le découpage automatique de la zone d’affichage de contrôle.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Paramètres

*bAutoClip*<br/>
La propriété DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

Récupère les DISPID_AMBIENT_BACKCOLOR, la couleur d’arrière-plan ambiante pour tous les contrôles, définis par le conteneur.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Paramètres

*BackColor*<br/>
La propriété DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

Récupère les DISPID_AMBIENT_CHARSET, ambiante jeu de caractères pour tous les contrôles, définis par le conteneur.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Paramètres

*bstrCharSet*<br/>
La propriété DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

Récupère les DISPID_AMBIENT_CODEPAGE, la page de codes ambiante pour tous les contrôles, définis par le conteneur.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Paramètres

*ulCodePage*<br/>
La propriété DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

Récupère les DISPID_AMBIENT_DISPLAYASDEFAULT, un indicateur qui a la valeur TRUE si le conteneur a marqué le contrôle de ce site pour être un bouton par défaut, et par conséquent un contrôle button doit se dessiner lui-même avec une image épaisse.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
La propriété DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

Récupère le DISPID_AMBIENT_DISPLAYNAME, le nom du conteneur a fourni au contrôle.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Paramètres

*bstrDisplayName*<br/>
La propriété DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

Récupère un pointeur vers le conteneur d’ambiant `IFont` interface.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Un pointeur vers le conteneur d’ambiant [IFont](/windows/desktop/api/ocidl/nn-ocidl-ifont) interface.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Si la propriété est NULL, le pointeur est NULL. Si le pointeur n’est pas NULL, l’appelant doit libérer le pointeur.

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

Récupère un pointeur vers le conteneur d’ambiant `IFontDisp` interface de dispatch.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Un pointeur vers le conteneur d’ambiant [IFontDisp](https://msdn.microsoft.com/library/windows/desktop/ms692695) interface de dispatch.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété est NULL, le pointeur est NULL. Si le pointeur n’est pas NULL, l’appelant doit libérer le pointeur.

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

Récupère les DISPID_AMBIENT_FORECOLOR, la couleur de premier plan ambiante pour tous les contrôles, définis par le conteneur.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Paramètres

*Couleur de premier plan*<br/>
La propriété DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

Récupère le DISPID_AMBIENT_LOCALEID, l’identificateur de la langue utilisée par le conteneur.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
La propriété DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Le contrôle peut utiliser cet identificateur pour adapter son interface utilisateur pour différentes langues.

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

Récupère les DISPID_AMBIENT_MESSAGEREFLECT, un indicateur qui spécifie si le conteneur souhaite recevoir des messages de fenêtre (tel que `WM_DRAWITEM`) en tant qu’événements.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
La propriété DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

Récupère DISPID_AMBIENT_PALETTE, permettant d’accéder aux HPALETTE du conteneur.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Paramètres

*hPalette*<br/>
La propriété DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

Récupère la propriété de conteneur spécifiée par *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Paramètres

*DISPID*<br/>
Identificateur de la propriété de conteneur à récupérer.

*var*<br/>
Variable devant recevoir la propriété.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

ATL fournit un ensemble de fonctions d’assistance pour récupérer des propriétés spécifiques, par exemple, [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Si aucune méthode appropriée n’est disponible, utilisez `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

Récupère les DISPID_AMBIENT_RIGHTTOLEFT, la direction dans laquelle le contenu est affiché par le conteneur.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Paramètres

*bRightToLeft*<br/>
La propriété DISPID_AMBIENT_RIGHTTOLEFT. La valeur TRUE si le contenu est affiché de droite à gauche, FALSE s’il est affiché de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

Récupère les DISPID_AMBIENT_SCALEUNITS, unités d’ambiante du conteneur (telles que des pouces ou centimètres) pour l’étiquetage affiche.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Paramètres

*bstrScaleUnits*<br/>
La propriété DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

Récupère les DISPID_AMBIENT_SHOWGRABHANDLES, un indicateur qui spécifie si le conteneur autorise le contrôle afficher les poignées de manipulation pour lui-même lorsqu’il est actif.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*bShowGrabHandles*<br/>
La propriété DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

Récupère les DISPID_AMBIENT_SHOWHATCHING, un indicateur qui spécifie si le conteneur autorise le contrôle lui-même affiche un motif hachuré lors de l’interface utilisateur du contrôle est actif.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Paramètres

*bShowHatching*<br/>
La propriété DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

Récupère les DISPID_AMBIENT_SUPPORTSMNEMONICS, un indicateur qui spécifie si le conteneur prend en charge les mnémoniques clavier.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Paramètres

*bSupportsMnemonics*<br/>
La propriété DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

Récupère les DISPID_AMBIENT_TEXTALIGN, l’alignement de texte préféré par le conteneur : 0 pour l’alignement général (texte de droite, de chiffres à gauche), 1 pour l’alignement à gauche, 2 pour l’alignement au centre et 3 pour l’alignement à droite.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Paramètres

*nTextAlign*<br/>
La propriété DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

Récupère les DISPID_AMBIENT_TOPTOBOTTOM, la direction dans laquelle le contenu est affiché par le conteneur.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Paramètres

*bTopToBottom*<br/>
La propriété DISPID_AMBIENT_TOPTOBOTTOM. La valeur TRUE si le texte est affiché de haut en bas, FALSE si elle est affichée en bas vers le haut.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

Récupère les DISPID_AMBIENT_UIDEAD, un indicateur qui spécifie si le conteneur puisse exiger le contrôle de répondre aux actions de l’interface utilisateur.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Paramètres

*bUIDead*<br/>
La propriété DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Si la valeur est TRUE, le contrôle ne doit pas répondre. Cet indicateur s’applique quel que soit l’indicateur DISPID_AMBIENT_USERMODE. Consultez [CComControlBase::GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

Récupère les DISPID_AMBIENT_USERMODE, un indicateur indiquant si le conteneur est en mode exécution (TRUE) ou en mode design (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
La propriété DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

##  <a name="getdirty"></a>  CComControlBase::GetDirty

Retourne la valeur du membre de données `m_bRequiresSave`.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du membre de données [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Notes

Cette valeur est définie à l’aide de [CComControlBase::SetDirty](#setdirty).

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

Récupère les coordonnées x et y valeurs de numérateur et dénominateur du facteur de zoom pour un contrôle est activé pour la modification sur place.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*injection de dépendances*<br/>
La structure qui contiendra le facteur de zoom numérateur et dénominateur. Pour plus d’informations, consultez [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Notes

Le facteur de zoom est la proportion de la taille du contrôle naturelle à son étendue actuelle.

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

Provoque la transition de l’état inactif à l’état le verbe dans le contrôle *iVerb* indique.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Valeur qui indique l’action à effectuer par [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Pointeur vers la position du contrôle sur place.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Avant l’activation, cette méthode vérifie que le contrôle a un site client, vérifie la quantité du contrôle est visible et obtient l’emplacement du contrôle dans la fenêtre parente. Une fois que le contrôle est activé, cette méthode active l’interface du contrôle utilisateur et indique au conteneur pour rendre le contrôle visible.

Cette méthode récupère également une `IOleInPlaceSite`, `IOleInPlaceSiteEx`, ou `IOleInPlaceSiteWindowless` pointeur d’interface pour le contrôle et le stocke dans le membre de données de la classe de contrôle [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Les membres de données de classe de contrôle [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)et [ CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) sont la valeur true si nécessaire.

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

Appelez cette méthode pour interroger le site de contrôle pour un pointeur vers l’interface identifiée.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
IID du pointeur d’interface qui doit être retourné dans *ppUnkSite*.

*ppUnkSite*<br/>
Adresse de la variable pointeur qui reçoit le pointeur d’interface demandé dans *riid*.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Si le site prend en charge l’interface demandée dans *riid*, le pointeur est retourné par le biais de *ppUnkSite*. Sinon, *ppUnkSite* est définie sur NULL.

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

Indicateur précisant que le contrôle ne peut pas être une autre taille.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Notes

Cet indicateur est vérifié par `IOleObjectImpl::SetExtent` et, si la valeur est TRUE, la fonction retourne E_FAIL.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Si vous ajoutez le **taille automatique** option sur le [Propriétés Stock](../../atl/reference/stock-properties-atl-control-wizard.md) onglet de l’Assistant contrôle ATL, l’Assistant crée automatiquement ce membre de données dans votre classe de contrôle, crée put et méthodes pour la propriété get et prend en charge [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) qui vous informent automatiquement le conteneur lorsque la propriété change.

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

Indicateur qui spécifie si `IDataObjectImpl::GetData` et `CComControlBase::GetZoomInfo` doit définir la taille du contrôle à partir de `m_sizeNatural` plutôt qu’à partir `m_sizeExtent`.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

Indicateur qui spécifie si `IDataObjectImpl::GetData` doit utiliser des unités HIMETRIC et pas des pixels lors du dessin.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Notes

Chaque unité HIMETRIC logique est 0,01 millimètre.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

Indicateur qui spécifie que le contrôle est actif en place.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Notes

Cela signifie que le contrôle est visible et sa fenêtre, le cas échéant, est visible, mais ses menus et les barres d’outils ne peuvent pas être actifs. Le `m_bUIActive` indicateur indique l’interface du contrôle utilisateur, tels que des menus, est également actif.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

Indicateur précisant s’il le prend en charge du conteneur le `IOleInPlaceSiteEx` interface et OCX96 contrôlent les fonctionnalités, tels que les contrôles sans fenêtre et sans scintillement.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Le membre de données `m_spInPlaceSite` pointe vers un [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interface, selon la valeur de la `m_bWndLess` et `m_bInPlaceSiteEx` indicateurs. (Le membre de données `m_bNegotiatedWnd` doit être vrai pour le `m_spInPlaceSite` pointeur soit valide.)

Si `m_bWndLess` a la valeur FALSE et `m_bInPlaceSiteEx` a la valeur TRUE, `m_spInPlaceSite` est un `IOleInPlaceSiteEx` pointeur d’interface. Consultez [m_spInPlaceSite](#m_spinplacesite) pour une table montrant les relations entre ces données de trois membres.

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

Indicateur déterminant si le contrôle a négocié avec le conteneur sur la prise en charge des fonctionnalités de contrôle OCX96 (tels que les contrôles sans fenêtre et sans scintillement), et si le contrôle est fenêtrées ou sans fenêtre.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Le `m_bNegotiatedWnd` indicateur doit être vrai pour le `m_spInPlaceSite` pointeur soit valide.

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

Indicateur précisant que le contrôle souhaite Recomposer sa présentation lorsque le conteneur change de taille d’affichage du contrôle.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Cet indicateur est vérifié par [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) et, si la valeur est TRUE, `SetExtent` informe le conteneur d’afficher les modifications. Si cet indicateur est défini, le OLEMISC_RECOMPOSEONRESIZE bit dans le [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) énumération doit également être définie.

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

Indicateur précisant que le contrôle a changé depuis son dernier enregistrement.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Notes

La valeur de `m_bRequiresSave` peut être défini avec [CComControlBase::SetDirty](#setdirty) et récupérées avec [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

Indicateur qui spécifie le contrôle souhaite redimensionner son extension naturelle (sa taille physique non ajustée) lorsque le conteneur change la taille d’affichage du contrôle.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Notes

Cet indicateur est vérifié par `IOleObjectImpl::SetExtent` et, si la valeur est TRUE, la taille passé dans `SetExtent` est affectée à `m_sizeNatural`.

La taille passé dans `SetExtent` est toujours affecté au `m_sizeExtent`, quelle que soit la valeur de `m_bResizeNatural`.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

Indicateur qui spécifie l’interface du contrôle utilisateur, notamment les menus et barres d’outils, est actif.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Notes

Le `m_bInPlaceActive` indicateur indique que le contrôle est actif, mais pas si son interface utilisateur est active.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

Indicateur précisant que le contrôle à l’aide de la région de la fenêtre du conteneur.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

Indicateur précisant le contrôle a été sans fenêtre, mais ne peut pas forcément sans fenêtre maintenant.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

Indicateur précisant que le contrôle doit être fenêtré, même si le conteneur prend en charge les contrôles sans fenêtre.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

Indicateur qui spécifie que le contrôle est sans fenêtre.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Le membre de données `m_spInPlaceSite` pointe vers un [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interface, selon la valeur de la `m_bWndLess` et [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) indicateurs. (Le membre de données [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) doit être vrai pour le [CComControlBase::m_spInPlaceSite](#m_spinplacesite) pointeur soit valide.)

Si `m_bWndLess` a la valeur TRUE, `m_spInPlaceSite` est un `IOleInPlaceSiteWindowless` pointeur d’interface. Consultez [CComControlBase::m_spInPlaceSite](#m_spinplacesite) pour une table montrant la relation complète entre ces membres de données.

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

Contient une référence vers le handle de fenêtre associé au contrôle.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

Le nombre de fois où le conteneur a figé événements (refusés d’accepter les événements) sans un libérer les intervenant des événements (acceptation d’événements).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

La position en pixels du contrôle, exprimée dans les coordonnées du conteneur.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

L’étendue du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres) pour un affichage particulier.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Cette taille est mis à l’échelle par l’affichage. La taille du contrôle physique est spécifiée dans le `m_sizeNatural` membre de données et est fixe.

Vous pouvez convertir la taille en pixels avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

La taille physique du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Cette taille est fixe, lors de la taille en `m_sizeExtent` est mis à l’échelle par l’affichage.

Vous pouvez convertir la taille en pixels avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

Un pointeur direct vers la connexion de notifications sur le conteneur (le conteneur [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

Un `CComDispatchDriver` objet qui vous permet de récupérer et définir les propriétés d’un objet via un `IDispatch` pointeur.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

Pointeur vers le site du client du contrôle au sein du conteneur.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

Fournit qu'une norme signifie pour maintenir les connexions de notifications entre les objets de données et de récepteurs de notifications.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Un objet de données est un contrôle qui peut transférer des données et qui met en œuvre [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject), dont les méthodes spécifient le support de format et le transfert des données.

L’interface `m_spDataAdviseHolder` implémente le [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) et [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) méthodes pour établir et supprimer des connexions de notifications au conteneur. Le conteneur du contrôle doit implémenter un récepteur de notifications en prenant en charge la [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interface.

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

Un pointeur vers le conteneur [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) pointeur d’interface.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

Le `m_spInPlaceSite` pointeur est valide uniquement si le [m_bNegotiatedWnd](#m_bnegotiatedwnd) indicateur a la valeur TRUE.

Le tableau suivant indique comment la `m_spInPlaceSite` type pointeur varie selon le [m_bWndLess](#m_bwndless) et [m_bInPlaceSiteEx](#m_binplacesiteex) indicateurs de membres de données :

|m_spInPlaceSite Type|m_bWndLess valeur|m_bInPlaceSiteEx valeur|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|true|TRUE ou FALSE|
|`IOleInPlaceSiteEx`|false|true|
|`IOleInPlaceSite`|false|false|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

Fournit une implémentation standard d’un moyen de contenir des connexions de notifications.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez les déclarer en tant qu’un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.

L’interface `m_spOleAdviseHolder` implémente le [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) et [IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) méthodes pour établir et supprimer des connexions de notifications au conteneur. Le conteneur du contrôle doit implémenter un récepteur de notifications en prenant en charge la [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interface.

##  <a name="ondraw"></a>  CComControlBase::OnDraw

Substituez cette méthode pour dessiner votre contrôle.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*injection de dépendances*<br/>
Une référence à la [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) structure qui contient des informations de dessin de l’aspect de dessin, les limites du contrôle, et indique si le dessin est optimisé ou non.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La valeur par défaut `OnDraw` supprime, restaure le contexte de périphérique ou ne fait rien, selon les indicateurs définis dans [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

Un `OnDraw` méthode est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle avec l’Assistant contrôle ATL. Par défaut de l’Assistant `OnDraw` Dessine un rectangle avec l’étiquette « ATL 8.0 ».

### <a name="example"></a>Exemple

Consultez l’exemple de [CComControlBase::GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

La valeur par défaut `OnDrawAdvanced` prépare un contexte de périphérique normalisé pour le dessin, puis appelle la classe de votre contrôle `OnDraw` (méthode).

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*injection de dépendances*<br/>
Une référence à la [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) structure qui contient des informations de dessin de l’aspect de dessin, les limites du contrôle, et indique si le dessin est optimisé ou non.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Substituez cette méthode si vous souhaitez accepter le contexte de périphérique passé par le conteneur, sans le normaliser.

Consultez [CComControlBase::OnDraw](#ondraw) pour plus d’informations.

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu le focus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg indique*<br/>
Réservé.

*wParam*<br/>
Réservé.

*lParam*<br/>
Réservé.

*bHandled*<br/>
Indicateur qui indique si le message de fenêtre a été géré correctement. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

Vérifie que l’interface utilisateur est en mode utilisateur, puis active le contrôle.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg indique*<br/>
Réservé.

*wParam*<br/>
Réservé.

*lParam*<br/>
Réservé.

*bHandled*<br/>
Indicateur qui indique si le message de fenêtre a été géré correctement. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

##  <a name="onpaint"></a>  CComControlBase::OnPaint

Prépare le conteneur pour la peinture, obtient la zone cliente du contrôle, puis appelle la classe de contrôle `OnDrawAdvanced` (méthode).

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Paramètres

*nMsg indique*<br/>
Réservé.

*wParam*<br/>
HDC existant.

*lParam*<br/>
Réservé.

*lResult*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne toujours zéro.

### <a name="remarks"></a>Notes

Si *wParam* n’est pas NULL, `OnPaint` part du principe qu’il contient un HDC valide et utilise à la place de [CComControlBase::m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur du contrôle a obtenu le focus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg indique*<br/>
Réservé.

*wParam*<br/>
Réservé.

*lParam*<br/>
Réservé.

*bHandled*<br/>
Indicateur qui indique si le message de fenêtre a été géré correctement. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Envoie une notification au conteneur que le contrôle a reçu le focus.

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

Substituez cette méthode pour fournir votre propre clavier gestionnaires d’accélérateur.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Réservé.

*hRet*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Par défaut, retourne FALSE.

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été fermé.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Envoie une notification que le contrôle a fermé ses récepteurs de notifications.

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que les données de contrôle a changé.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Paramètres

*ADVF*<br/>
Informez les indicateurs qui spécifient comment l’appel à [IAdviseSink::OnDataChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-ondatachange) est effectuée. Les valeurs vont de la [ADVF](/windows/desktop/api/objidl/ne-objidl-tagadvf) énumération.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a un nouveau moniker.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Paramètres

*PMK*<br/>
Pointeur vers le nouveau moniker du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Envoie une notification indiquant que le moniker pour le contrôle a changé.

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

Avertit les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été enregistré.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Envoie une notification que le contrôle vient de ses données.

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

Avertit que tous les enregistrés des récepteurs de notifications que l’affichage du contrôle a changé.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Paramètres

*dwAspect*<br/>
La hauteur ou la vue du contrôle.

*lindex*<br/>
La partie de la vue qui a changé. Uniquement -1 est valide.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`SendOnViewChange` appels [IAdviseSink::OnViewChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-onviewchange). La seule valeur de *lIndex Valeur de type* actuellement pris en charge est -1, ce qui indique que la vue d’ensemble présente un intérêt.

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

Définit ou supprime le focus clavier vers ou depuis le contrôle.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Paramètres

*bGrab*<br/>
Si la valeur est TRUE, définit le focus clavier au contrôle appelant. Si la valeur est FALSE, supprime le focus clavier du contrôle appelant, sous réserve qu’il a le focus.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le contrôle reçoit correctement le focus ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Pour un contrôle avec fenêtres, la fonction Windows API [SetFocus](https://msdn.microsoft.com/library/windows/desktop/ms646312) est appelée. Pour un contrôle sans fenêtre, [IOleInPlaceSiteWindowless::SetFocus](/windows/desktop/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) est appelée. Via cet appel, un contrôle sans fenêtre Obtient le focus clavier et peut répondre aux messages de fenêtre.

##  <a name="setdirty"></a>  CComControlBase::SetDirty

Définit le membre de données `m_bRequiresSave` à la valeur de *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*bDirty*<br/>
Valeur du membre de données [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Notes

`SetDirty(TRUE)` doit être appelée pour signaler que le contrôle a changé depuis son dernier enregistrement. La valeur de `m_bRequiresSave` est récupérée avec [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
