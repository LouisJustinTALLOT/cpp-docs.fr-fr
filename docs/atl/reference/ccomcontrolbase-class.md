---
title: CComControlBase, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497371"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase, classe

Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Remplacez si votre `m_nAppearance` propriété stock n’est pas de type **short**.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Constructeur.|
|[CComControlBase:: ~ CComControlBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Vérifie que le paramètre *iVerb* utilisé par `IOleObjectImpl::DoVerb` active l’interface utilisateur du contrôle (*iVerb* est égal à OLEIVERB_UIACTIVATE), définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle (*iVerb* est égal à OLEIVERB_ PRINCIPAL), affiche le contrôle (*iVerb* est égal à OLEIVERB_SHOW) ou active le contrôle (*iVerb* est égal à OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Vérifie que le paramètre *iVerb* utilisé par `IOleObjectImpl::DoVerb` provoque l’activation de l’interface utilisateur du contrôle et retourne la valeur true.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Affiche les pages de propriétés du contrôle.|
|[CComControlBase::FireViewChange](#fireviewchange)|Appelez cette méthode pour indiquer au conteneur de redessiner le contrôle, ou informez les récepteurs de notification inscrits que la vue du contrôle a changé.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Récupère DISPID_AMBIENT_APPEARANCE, le paramètre d’apparence actuel pour le contrôle: 0 pour plat et 1 pour 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Récupère DISPID_AMBIENT_AUTOCLIP, un indicateur qui spécifie si le conteneur prend en charge le découpage automatique de la zone d’affichage du contrôle.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Récupère DISPID_AMBIENT_BACKCOLOR, la couleur d’arrière-plan ambiante pour tous les contrôles, définie par le conteneur.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Récupère DISPID_AMBIENT_CHARSET, le jeu de caractères ambiants pour tous les contrôles, défini par le conteneur.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Récupère DISPID_AMBIENT_CODEPAGE, le jeu de caractères ambiants pour tous les contrôles, défini par le conteneur.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Récupère DISPID_AMBIENT_DISPLAYASDEFAULT, un indicateur qui a la valeur TRUE si le conteneur a marqué le contrôle dans ce site comme un bouton par défaut. par conséquent, un contrôle bouton doit se dessiner lui-même avec un cadre plus épais.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Récupère DISPID_AMBIENT_DISPLAYNAME, le nom que le conteneur a fourni au contrôle.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Récupère un pointeur vers l’interface ambiante `IFont` du conteneur.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Récupère un pointeur vers l’interface de dispatch ambiante `IFontDisp` du conteneur.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Récupère DISPID_AMBIENT_FORECOLOR, la couleur de premier plan ambiante pour tous les contrôles, définie par le conteneur.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Récupère DISPID_AMBIENT_LOCALEID, l’identificateur de la langue utilisée par le conteneur.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Récupère DISPID_AMBIENT_MESSAGEREFLECT, un indicateur qui spécifie si le conteneur souhaite recevoir des messages de fenêtre (tels que WM_DRAWITEM) en tant qu’événements.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Récupère DISPID_AMBIENT_PALETTE, utilisé pour accéder au HPALETTE du conteneur.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Récupère la propriété de conteneur spécifiée par l' *ID*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Récupère DISPID_AMBIENT_RIGHTTOLEFT, la direction dans laquelle le contenu est affiché par le conteneur.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Récupère les DISPID_AMBIENT_SCALEUNITS, les unités ambiantes du conteneur (par exemple, des pouces ou des centimètres) pour l’étiquetage des affichages.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Récupère DISPID_AMBIENT_SHOWGRABHANDLES, un indicateur qui spécifie si le conteneur permet au contrôle d’afficher des handles de manipulation pour lui-même lorsqu’il est actif.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Récupère DISPID_AMBIENT_SHOWHATCHING, un indicateur qui spécifie si le conteneur permet au contrôle de s’afficher avec un modèle hachuré lorsque l’interface utilisateur est active.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Récupère DISPID_AMBIENT_SUPPORTSMNEMONICS, un indicateur qui spécifie si le conteneur prend en charge les mnémoniques du clavier.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Récupère DISPID_AMBIENT_TEXTALIGN, l’alignement de texte préféré par le conteneur: 0 pour l’alignement général (nombres à droite, texte à gauche), 1 pour l’alignement à gauche, 2 pour l’alignement au centre et 3 pour l’alignement à droite.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Récupère DISPID_AMBIENT_TOPTOBOTTOM, la direction dans laquelle le contenu est affiché par le conteneur.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Récupère DISPID_AMBIENT_UIDEAD, un indicateur qui spécifie si le conteneur souhaite que le contrôle réponde aux actions de l’interface utilisateur.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Récupère DISPID_AMBIENT_USERMODE, un indicateur qui spécifie si le conteneur est en mode exécution (TRUE) ou en mode Design (FALSe).|
|[CComControlBase::GetDirty](#getdirty)|Retourne la valeur du membre `m_bRequiresSave`de données.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Récupère les valeurs x et y du numérateur et du dénominateur du facteur de zoom pour un contrôle activé pour la modification sur place.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Fait passer le contrôle de l’état inactif à l’état que le verbe dans *iVerb* indique.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Appelez cette méthode pour interroger le site de contrôle pour obtenir un pointeur vers l’interface identifiée.|
|[CComControlBase::OnDraw](#ondraw)|Substituez cette méthode pour dessiner votre contrôle.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|La valeur `OnDrawAdvanced` par défaut prépare un contexte de périphérique normalisé pour le dessin, puis appelle la méthode `OnDraw` de votre classe de contrôle.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Vérifie que le contrôle est en place actif et qu’il dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu le focus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Vérifie que l’interface utilisateur est en mode utilisateur, puis active le contrôle.|
|[CComControlBase:: OnPaint](#onpaint)|Prépare le conteneur pour la peinture, obtient la zone cliente du contrôle, puis appelle la méthode de `OnDraw` la classe de contrôle.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Vérifie que le contrôle est en place actif et qu’il dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a obtenu le focus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Substituez cette méthode pour fournir vos propres gestionnaires d’accélérateurs de clavier.|
|[CComControlBase::SendOnClose](#sendonclose)|Avertit tous les récepteurs de notifications inscrits auprès du détenteur de la notification que le contrôle a été fermé.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Avertit tous les récepteurs de notifications inscrits auprès du titulaire de la notification que les données de contrôle ont changé.|
|[CComControlBase::SendOnRename](#sendonrename)|Avertit tous les récepteurs de notifications inscrits auprès du détenteur de la notification que le contrôle a un nouveau moniker.|
|[CComControlBase::SendOnSave](#sendonsave)|Avertit tous les récepteurs de notifications inscrits auprès du détenteur de la notification que le contrôle a été enregistré.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Avertit tous les récepteurs de notifications enregistrés que l’affichage du contrôle a changé.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Définit ou supprime le focus clavier du contrôle.|
|[CComControlBase::SetDirty](#setdirty)|Définit le membre `m_bRequiresSave` de données sur la valeur dans *bDirty*.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Indicateur qui spécifie que le contrôle ne peut pas être d’une autre taille.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Indicateur qui spécifie `CComControlBase::GetZoomInfo` que `IDataObjectImpl::GetData` et doit définir la taille `m_sizeNatural` du contrôle à `m_sizeExtent`partir de plutôt que de.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Indicateur spécifiant `IDataObjectImpl::GetData` que doit utiliser des unités HIMETRIC et non des pixels lors du dessin.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Indicateur qui spécifie que le contrôle est actif sur place.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Indicateur qui spécifie que le `IOleInPlaceSiteEx` conteneur prend en charge les fonctionnalités de contrôle interface et OCX96, telles que les contrôles sans fenêtre et sans scintillement.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Indicateur qui spécifie si le contrôle a négocié avec le conteneur à propos de la prise en charge des fonctionnalités de contrôle OCX96 (telles que les contrôles sans scintillement et sans fenêtre) et si le contrôle est fenêtre ou sans fenêtre.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Indicateur spécifiant que le contrôle souhaite recomposer sa présentation lorsque le conteneur modifie la taille d’affichage du contrôle.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Indicateur qui spécifie que le contrôle a été modifié depuis son dernier enregistrement.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Indicateur spécifiant que le contrôle souhaite redimensionner son étendue naturelle (sa taille physique non mise à l’échelle) quand le conteneur modifie la taille d’affichage du contrôle.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Indicateur qui spécifie que l’interface utilisateur du contrôle, telle que les menus et les barres d’outils, est active.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Indicateur qui spécifie que le contrôle utilise la région de fenêtre fournie par le conteneur.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Indicateur qui spécifie que le contrôle n’a pas de fenêtre, mais peut ou ne peut pas être sans fenêtre maintenant.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Indicateur qui spécifie que le contrôle doit être fenêtre, même si le conteneur prend en charge les contrôles sans fenêtre.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Indicateur qui spécifie que le contrôle n’a pas de fenêtre.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contient une référence au handle de fenêtre associé au contrôle.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Nombre de fois où le conteneur a des événements figés (refusés d’accepter des événements) sans un dégel d’événements intermédiaire (acceptation d’événements).|
|[CComControlBase::m_rcPos](#m_rcpos)|Position, en pixels, du contrôle, exprimée en coordonnées du conteneur.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|L’étendue du contrôle en unités HIMETRIC (chaque unité est de 0,01 millimètres) pour un affichage particulier.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Taille physique du contrôle en unités HIMETRIC (chaque unité est de 0,01 millimètres).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Pointeur direct vers la connexion consultative sur le conteneur (le [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)du conteneur).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Objet qui vous permet de récupérer et de définir les propriétés du conteneur par `IDispatch` le biais d’un pointeur. `CComDispatchDriver`|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Pointeur vers le site client du contrôle dans le conteneur.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Fournit un moyen standard de conserver les connexions de notifications entre les objets de données et les récepteurs de notifications.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Pointeur vers le pointeur d’interface [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) du conteneur.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Fournit une implémentation standard d’un moyen de stocker des connexions de notifications.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer des contrôles ATL. La [classe CComControl](../../atl/reference/ccomcontrol-class.md) dérive `CComControlBase`de. Lorsque vous créez un contrôle standard ou un contrôle DHTML à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre classe de `CComControlBase`.

Pour plus d’informations sur la création d’un contrôle, consultez le [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

Remplacez si votre `m_nAppearance` propriété stock n’est pas de type **short**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Notes

L’Assistant contrôle ATL ajoute `m_nAppearance` la propriété stock de type short. Substituez `AppearanceType` si vous utilisez un type de données différent.

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

Constructeur.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle de la fenêtre associée au contrôle.

### <a name="remarks"></a>Notes

Initialise la taille du contrôle à 5080X5080 unités HIMETRIC (2 «x2») et initialise les valeurs `CComControlBase` des membres de données avec la valeur null ou false.

##  <a name="dtor"></a>  CComControlBase::~CComControlBase

Destructeur.

```
~CComControlBase();
```

### <a name="remarks"></a>Notes

Si le contrôle est fenêtre, `~CComControlBase` le détruit en appelant [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

Récupère un pointeur vers l'interface demandée.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
GUID de l’interface demandée.

*ppv*<br/>
Pointeur vers le pointeur d’interface identifié par *IID*, ou null si l’interface est introuvable.

### <a name="remarks"></a>Notes

Gère uniquement les interfaces dans la table de mappage COM.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

Vérifie que le paramètre *iVerb* utilisé par `IOleObjectImpl::DoVerb` active l’interface utilisateur du contrôle (*iVerb* est égal à OLEIVERB_UIACTIVATE), définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle (*iVerb* est égal à OLEIVERB_ PRINCIPAL), affiche le contrôle (*iVerb* est égal à OLEIVERB_SHOW) ou active le contrôle (*iVerb* est égal à OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Valeur indiquant l’action à effectuer par `DoVerb`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si *iVerb* est égal à OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW ou OLEIVERB_INPLACEACTIVATE; Sinon, retourne FALSe.

### <a name="remarks"></a>Notes

Vous pouvez substituer cette méthode pour définir votre propre verbe d’activation.

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

Vérifie que le paramètre *iVerb* utilisé par `IOleObjectImpl::DoVerb` provoque l’activation de l’interface utilisateur du contrôle et retourne la valeur true.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Valeur indiquant l’action à effectuer par `DoVerb`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si *iVerb* est égal à OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW ou OLEIVERB_INPLACEACTIVATE. Sinon, la méthode retourne FALSe.

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

Affiche les pages de propriétés du contrôle.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
Réservé.

*hwndParent*<br/>
Handle de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

Appelez cette méthode pour indiquer au conteneur de redessiner le contrôle, ou informez les récepteurs de notification inscrits que la vue du contrôle a changé.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si le contrôle est actif (la classe de contrôle Data Member [CComControlBase:: m_bInPlaceActive](#m_binplaceactive) a la valeur true), notifie le conteneur que vous souhaitez redessiner l’intégralité du contrôle. Si le contrôle est inactif, notifie les récepteurs de notifications enregistrés du contrôle (via la classe de contrôle Data Member [CComControlBase:: m_spAdviseSink](#m_spadvisesink)) que la vue du contrôle a changé.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

Récupère DISPID_AMBIENT_APPEARANCE, le paramètre d’apparence actuel pour le contrôle: 0 pour plat et 1 pour 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Paramètres

*nAppearance*<br/>
Propriété DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

Récupère DISPID_AMBIENT_AUTOCLIP, un indicateur qui spécifie si le conteneur prend en charge le découpage automatique de la zone d’affichage du contrôle.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Paramètres

*bAutoClip*<br/>
Propriété DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

Récupère DISPID_AMBIENT_BACKCOLOR, la couleur d’arrière-plan ambiante pour tous les contrôles, définie par le conteneur.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Paramètres

*BackColor*<br/>
Propriété DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

Récupère DISPID_AMBIENT_CHARSET, le jeu de caractères ambiants pour tous les contrôles, défini par le conteneur.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Paramètres

*bstrCharSet*<br/>
Propriété DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

Récupère DISPID_AMBIENT_CODEPAGE, la page de codes ambiante pour tous les contrôles, définie par le conteneur.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Paramètres

*ulCodePage*<br/>
Propriété DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

Récupère DISPID_AMBIENT_DISPLAYASDEFAULT, un indicateur qui a la valeur TRUE si le conteneur a marqué le contrôle dans ce site comme un bouton par défaut. par conséquent, un contrôle bouton doit se dessiner lui-même avec un cadre plus épais.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
Propriété DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

Récupère DISPID_AMBIENT_DISPLAYNAME, le nom que le conteneur a fourni au contrôle.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Paramètres

*bstrDisplayName*<br/>
Propriété DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

Récupère un pointeur vers l’interface ambiante `IFont` du conteneur.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Pointeur vers l’interface [IFont](/windows/win32/api/ocidl/nn-ocidl-ifont) ambiante du conteneur.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si la propriété a la valeur NULL, le pointeur a la valeur NULL. Si le pointeur n’a pas la valeur NULL, l’appelant doit libérer le pointeur.

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

Récupère un pointeur vers l’interface de dispatch ambiante `IFontDisp` du conteneur.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Pointeur vers l’interface de distribution [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) ambiante du conteneur.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété a la valeur NULL, le pointeur a la valeur NULL. Si le pointeur n’a pas la valeur NULL, l’appelant doit libérer le pointeur.

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

Récupère DISPID_AMBIENT_FORECOLOR, la couleur de premier plan ambiante pour tous les contrôles, définie par le conteneur.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Paramètres

*ForeColor*<br/>
Propriété DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

Récupère DISPID_AMBIENT_LOCALEID, l’identificateur de la langue utilisée par le conteneur.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
Propriété DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Le contrôle peut utiliser cet identificateur pour adapter son interface utilisateur dans différentes langues.

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

Récupère DISPID_AMBIENT_MESSAGEREFLECT, un indicateur qui spécifie si le conteneur souhaite recevoir des messages de fenêtre ( `WM_DRAWITEM`tels que) en tant qu’événements.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
Propriété DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

Récupère DISPID_AMBIENT_PALETTE, utilisé pour accéder au HPALETTE du conteneur.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Paramètres

*hPalette*<br/>
Propriété DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

Récupère la propriété de conteneur spécifiée par *DISPID*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
Identificateur de la propriété de conteneur à récupérer.

*var*<br/>
Variable qui doit recevoir la propriété.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

ATL a fourni un ensemble de fonctions d’assistance pour récupérer des propriétés spécifiques, par exemple, [CComControlBase:: GetAmbientBackColor](#getambientbackcolor). Si aucune méthode appropriée n’est disponible, utilisez `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

Récupère DISPID_AMBIENT_RIGHTTOLEFT, la direction dans laquelle le contenu est affiché par le conteneur.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Paramètres

*bRightToLeft*<br/>
Propriété DISPID_AMBIENT_RIGHTTOLEFT. A la valeur TRUE si le contenu est affiché de droite à gauche, FALSe s’il est affiché de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

Récupère les DISPID_AMBIENT_SCALEUNITS, les unités ambiantes du conteneur (par exemple, des pouces ou des centimètres) pour l’étiquetage des affichages.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Paramètres

*bstrScaleUnits*<br/>
Propriété DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

Récupère DISPID_AMBIENT_SHOWGRABHANDLES, un indicateur qui spécifie si le conteneur permet au contrôle d’afficher des handles de manipulation pour lui-même lorsqu’il est actif.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*bShowGrabHandles*<br/>
Propriété DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

Récupère DISPID_AMBIENT_SHOWHATCHING, un indicateur qui spécifie si le conteneur permet au contrôle de s’afficher avec un modèle hachuré lorsque l’interface utilisateur du contrôle est active.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Paramètres

*bShowHatching*<br/>
Propriété DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

Récupère DISPID_AMBIENT_SUPPORTSMNEMONICS, un indicateur qui spécifie si le conteneur prend en charge les mnémoniques du clavier.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Paramètres

*bSupportsMnemonics*<br/>
Propriété DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

Récupère DISPID_AMBIENT_TEXTALIGN, l’alignement de texte préféré par le conteneur: 0 pour l’alignement général (nombres à droite, texte à gauche), 1 pour l’alignement à gauche, 2 pour l’alignement au centre et 3 pour l’alignement à droite.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Paramètres

*nTextAlign*<br/>
Propriété DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

Récupère DISPID_AMBIENT_TOPTOBOTTOM, la direction dans laquelle le contenu est affiché par le conteneur.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Paramètres

*bTopToBottom*<br/>
Propriété DISPID_AMBIENT_TOPTOBOTTOM. A la valeur TRUE si le texte est affiché de haut en bas, FALSe s’il est affiché de bas en haut.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

Récupère DISPID_AMBIENT_UIDEAD, un indicateur qui spécifie si le conteneur souhaite que le contrôle réponde aux actions de l’interface utilisateur.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Paramètres

*bUIDead*<br/>
Propriété DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si la valeur est TRUE, le contrôle ne doit pas répondre. Cet indicateur s’applique indépendamment de l’indicateur DISPID_AMBIENT_USERMODE. Consultez [CComControlBase:: GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

Récupère DISPID_AMBIENT_USERMODE, un indicateur qui spécifie si le conteneur est en mode exécution (TRUE) ou en mode Design (FALSe).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
Propriété DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

##  <a name="getdirty"></a>  CComControlBase::GetDirty

Retourne la valeur du membre `m_bRequiresSave`de données.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du membre de données [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Notes

Cette valeur est définie à l’aide de [CComControlBase:: SetDirty](#setdirty).

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

Récupère les valeurs x et y du numérateur et du dénominateur du facteur de zoom pour un contrôle activé pour la modification sur place.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*di*<br/>
Structure qui contiendra le numérateur et le dénominateur du facteur de zoom. Pour plus d’informations, consultez [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Notes

Le facteur de zoom correspond à la proportion de la taille naturelle du contrôle par rapport à son étendue actuelle.

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

Fait passer le contrôle de l’état inactif à l’état que le verbe dans *iVerb* indique.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Valeur indiquant l’action à effectuer par [IOleObjectImpl::D overb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Pointeur vers la position du contrôle sur place.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Avant l’activation, cette méthode vérifie que le contrôle dispose d’un site client, vérifie la quantité de contrôle visible et obtient l’emplacement du contrôle dans la fenêtre parente. Une fois le contrôle activé, cette méthode active l’interface utilisateur du contrôle et indique au conteneur de rendre le contrôle visible.

Cette méthode récupère également un `IOleInPlaceSite`pointeur d’interface, `IOleInPlaceSiteWindowless` `IOleInPlaceSiteEx`ou pour le contrôle et le stocke dans le membre de données de la classe de contrôle [CComControlBase:: m_spInPlaceSite](#m_spinplacesite). Les données membres de la classe de contrôle [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase:: m_bWndLess](#m_bwndless), [CComControlBase:: M_bWasOnceWindowless](#m_bwasoncewindowless)et [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) ont la valeur true, le cas échéant.

##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite

Appelez cette méthode pour interroger le site de contrôle pour obtenir un pointeur vers l’interface identifiée.

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

Si le site prend en charge l’interface demandée dans *riid*, le pointeur est retourné au moyen de *ppUnkSite*. Sinon, *ppUnkSite* a la valeur null.

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

Indicateur qui spécifie que le contrôle ne peut pas être d’une autre taille.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Notes

Cet indicateur est vérifié par `IOleObjectImpl::SetExtent` et, si la valeur est true, la fonction retourne E_FAIL.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Si vous ajoutez l’option **taille automatique** dans l’onglet [Propriétés des actions](../../atl/reference/stock-properties-atl-control-wizard.md) de l’Assistant contrôle ATL, l’Assistant crée automatiquement ce membre de données dans votre classe de contrôle, crée les méthodes put et obtenir pour la propriété et prend en charge [IPropertyNotifySink ](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)pour notifier automatiquement le conteneur lorsque la propriété change.

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

Indicateur qui spécifie `CComControlBase::GetZoomInfo` que `IDataObjectImpl::GetData` et doit définir la taille `m_sizeNatural` du contrôle à `m_sizeExtent`partir de plutôt que de.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

Indicateur spécifiant `IDataObjectImpl::GetData` que doit utiliser des unités HIMETRIC et non des pixels lors du dessin.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Notes

Chaque unité logique HIMETRIC est 0,01 millimètre.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

Indicateur qui spécifie que le contrôle est actif sur place.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Notes

Cela signifie que le contrôle est visible et que sa fenêtre, le cas échéant, est visible, mais ses menus et barres d’outils ne sont peut-être pas actifs. L' `m_bUIActive` indicateur indique que l’interface utilisateur du contrôle, telle que menus, est également active.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

Indicateur qui spécifie que le `IOleInPlaceSiteEx` conteneur prend en charge les fonctionnalités de contrôle interface et OCX96, telles que les contrôles sans fenêtre et sans scintillement.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Le membre `m_spInPlaceSite` de données pointe vers une interface [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess` , en fonction de la valeur des indicateurs et `m_bInPlaceSiteEx` . (Le membre `m_bNegotiatedWnd` de données doit avoir la valeur `m_spInPlaceSite` true pour que le pointeur soit valide.)

Si `m_bWndLess` a la valeur `m_bInPlaceSiteEx` false et `m_spInPlaceSite` que a `IOleInPlaceSiteEx` la valeur true, est un pointeur d’interface. Consultez [m_spInPlaceSite](#m_spinplacesite) pour obtenir un tableau présentant la relation entre ces trois membres de données.

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

Indicateur qui spécifie si le contrôle a négocié avec le conteneur à propos de la prise en charge des fonctionnalités de contrôle OCX96 (telles que les contrôles sans scintillement et sans fenêtre) et si le contrôle est fenêtre ou sans fenêtre.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

L' `m_bNegotiatedWnd` indicateur doit avoir la valeur true `m_spInPlaceSite` pour que le pointeur soit valide.

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

Indicateur spécifiant que le contrôle souhaite recomposer sa présentation lorsque le conteneur modifie la taille d’affichage du contrôle.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Cet indicateur est vérifié par [IOleObjectImpl::](../../atl/reference/ioleobjectimpl-class.md#setextent) severse et, si `SetExtent` la valeur est true, notifie le conteneur de modifications d’affichage. Si cet indicateur est défini, le bit OLEMISC_RECOMPOSEONRESIZE dans l’énumération [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) doit également être défini.

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

Indicateur qui spécifie que le contrôle a été modifié depuis son dernier enregistrement.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Notes

La valeur de `m_bRequiresSave` peut être définie avec [CComControlBase:: SetDirty](#setdirty) et récupérée avec [CComControlBase:: GetDirty](#getdirty).

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

Indicateur spécifiant que le contrôle souhaite redimensionner son étendue naturelle (sa taille physique non mise à l’échelle) quand le conteneur modifie la taille d’affichage du contrôle.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Notes

Cet indicateur est vérifié par `IOleObjectImpl::SetExtent` et, si la valeur `SetExtent` est true, la taille passée à `m_sizeNatural`est assignée à.

La taille passée `SetExtent` à est toujours assignée à `m_sizeExtent`, quelle que soit `m_bResizeNatural`la valeur de.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

Indicateur qui spécifie que l’interface utilisateur du contrôle, telle que les menus et les barres d’outils, est active.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Notes

L' `m_bInPlaceActive` indicateur indique que le contrôle est actif, mais pas que son interface utilisateur est active.

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

Indicateur qui spécifie que le contrôle utilise la région de fenêtre fournie par le conteneur.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

Indicateur qui spécifie que le contrôle n’a pas de fenêtre, mais peut ou ne peut pas être sans fenêtre maintenant.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

Indicateur qui spécifie que le contrôle doit être fenêtre, même si le conteneur prend en charge les contrôles sans fenêtre.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess

Indicateur qui spécifie que le contrôle n’a pas de fenêtre.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Le `m_spInPlaceSite` membre de données pointe vers une interface [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess` , en fonction de la valeur des indicateurs et [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex) . (Le membre de données [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) doit avoir la valeur true pour que le pointeur [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) soit valide.)

Si `m_bWndLess` a la valeur `m_spInPlaceSite` true, `IOleInPlaceSiteWindowless` est un pointeur d’interface. Consultez [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) pour une table qui affiche la relation complète entre ces membres de données.

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

Contient une référence au handle de fenêtre associé au contrôle.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

Nombre de fois où le conteneur a des événements figés (refusés d’accepter des événements) sans un dégel d’événements intermédiaire (acceptation d’événements).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

Position, en pixels, du contrôle, exprimée en coordonnées du conteneur.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

L’étendue du contrôle en unités HIMETRIC (chaque unité est de 0,01 millimètres) pour un affichage particulier.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Cette taille est mise à l’échelle par l’affichage. La taille physique du contrôle est spécifiée dans la `m_sizeNatural` donnée membre et est fixe.

Vous pouvez convertir la taille en pixels avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

Taille physique du contrôle en unités HIMETRIC (chaque unité est de 0,01 millimètres).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Cette taille est fixe, tandis que la `m_sizeExtent` taille dans est mise à l’échelle par l’affichage.

Vous pouvez convertir la taille en pixels avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

Pointeur direct vers la connexion consultative sur le conteneur (le [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)du conteneur).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

Objet qui vous permet de récupérer et de définir les propriétés d’un objet `IDispatch` par le biais d’un pointeur. `CComDispatchDriver`

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite

Pointeur vers le site client du contrôle dans le conteneur.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

Fournit un moyen standard de conserver les connexions de notifications entre les objets de données et les récepteurs de notifications.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Un objet de données est un contrôle qui peut transférer des données et implémente [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), dont les méthodes spécifient le format et le support de transfert des données.

L’interface `m_spDataAdviseHolder` implémente les méthodes [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) et [IDataObject::D](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) Unadvise pour établir et supprimer des connexions de notifications au conteneur. Le conteneur du contrôle doit implémenter un récepteur de notifications en prenant en charge l’interface [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

Pointeur vers le pointeur d’interface [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) du conteneur.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

Le `m_spInPlaceSite` pointeur est valide uniquement si l’indicateur [m_bNegotiatedWnd](#m_bnegotiatedwnd) a la valeur true.

Le tableau suivant montre comment le `m_spInPlaceSite` type pointeur dépend des indicateurs de données membres [m_bWndLess](#m_bwndless) et [m_bInPlaceSiteEx](#m_binplacesiteex) :

|Type m_spInPlaceSite|Valeur m_bWndLess|Valeur m_bInPlaceSiteEx|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|TRUE ou FALSe|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

Fournit une implémentation standard d’un moyen de stocker des connexions de notifications.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez le déclarer en tant que membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de cette donnée membre de la classe de base, car elle est déclarée dans une Union de la classe de base.

L’interface `m_spOleAdviseHolder` implémente les méthodes [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) et [IOleObject::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) Unadvise pour établir et supprimer des connexions de notifications au conteneur. Le conteneur du contrôle doit implémenter un récepteur de notifications en prenant en charge l’interface [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="ondraw"></a>  CComControlBase::OnDraw

Substituez cette méthode pour dessiner votre contrôle.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*di*<br/>
Référence à la structure [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) qui contient des informations de dessin telles que l’aspect de dessin, les limites de contrôle et si le dessin est optimisé ou non.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

La valeur `OnDraw` par défaut supprime ou restaure le contexte de périphérique ou ne fait rien, selon les indicateurs définis dans [CComControlBase:: OnDrawAdvanced](#ondrawadvanced).

Une `OnDraw` méthode est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle à l’aide de l’Assistant contrôle ATL. La valeur par défaut `OnDraw` de l’Assistant dessine un rectangle avec l’étiquette «ATL 8,0».

### <a name="example"></a>Exemple

Consultez l’exemple de [CComControlBase:: GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

La valeur `OnDrawAdvanced` par défaut prépare un contexte de périphérique normalisé pour le dessin, puis appelle la méthode `OnDraw` de votre classe de contrôle.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*di*<br/>
Référence à la structure [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) qui contient des informations de dessin telles que l’aspect de dessin, les limites de contrôle et si le dessin est optimisé ou non.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Substituez cette méthode si vous souhaitez accepter le contexte de périphérique passé par le conteneur sans le normaliser.

Pour plus d’informations, consultez [CComControlBase:: OnDraw](#ondraw) .

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

Vérifie que le contrôle est en place actif et qu’il dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu le focus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg*<br/>
Réservé.

*wParam*<br/>
Réservé.

*lParam*<br/>
Réservé.

*bHandled*<br/>
Indicateur qui signale si le message de fenêtre a été correctement géré. La valeur par défaut est FALSe.

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

*nMsg*<br/>
Réservé.

*wParam*<br/>
Réservé.

*lParam*<br/>
Réservé.

*bHandled*<br/>
Indicateur qui signale si le message de fenêtre a été correctement géré. La valeur par défaut est FALSe.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

##  <a name="onpaint"></a>  CComControlBase::OnPaint

Prépare le conteneur pour la peinture, obtient la zone cliente du contrôle, puis appelle la méthode de `OnDrawAdvanced` la classe de contrôle.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Paramètres

*nMsg*<br/>
Réservé.

*wParam*<br/>
Une HDC existante.

*lParam*<br/>
Réservé.

*lResult*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne toujours zéro.

### <a name="remarks"></a>Notes

Si *wParam* n’a pas la `OnPaint` valeur null, suppose qu’il contient un HDC valide et l’utilise à la place de [CComControlBase:: m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

Vérifie que le contrôle est en place actif et qu’il dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a obtenu le focus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Paramètres

*nMsg*<br/>
Réservé.

*wParam*<br/>
Réservé.

*lParam*<br/>
Réservé.

*bHandled*<br/>
Indicateur qui signale si le message de fenêtre a été correctement géré. La valeur par défaut est FALSe.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Envoie une notification au conteneur que le contrôle a reçu le focus.

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

Substituez cette méthode pour fournir vos propres gestionnaires d’accélérateurs de clavier.

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

Par défaut, retourne FALSe.

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

Avertit tous les récepteurs de notifications inscrits auprès du détenteur de la notification que le contrôle a été fermé.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Envoie une notification indiquant que le contrôle a fermé ses récepteurs de notifications.

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

Avertit tous les récepteurs de notifications inscrits auprès du titulaire de la notification que les données de contrôle ont changé.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Paramètres

*advf*<br/>
Indicateurs de notification qui spécifient la façon dont l’appel à [IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) est effectué. Les valeurs proviennent de l’énumération [ADVF](/windows/win32/api/objidl/ne-objidl-advf) .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

Avertit tous les récepteurs de notifications inscrits auprès du détenteur de la notification que le contrôle a un nouveau moniker.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Paramètres

*pmk*<br/>
Pointeur vers le nouveau moniker du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Envoie une notification indiquant que le moniker du contrôle a été modifié.

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

Avertit tous les récepteurs de notifications inscrits auprès du détenteur de la notification que le contrôle a été enregistré.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Envoie une notification indiquant que le contrôle vient d’enregistrer ses données.

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

Avertit tous les récepteurs de notifications enregistrés que l’affichage du contrôle a changé.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Paramètres

*dwAspect*<br/>
Aspect ou affichage du contrôle.

*lindex*<br/>
Partie de la vue qui a changé. Seul-1 est valide.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`SendOnViewChange`appelle [IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). La seule valeur de *Lindex* actuellement prise en charge est-1, ce qui indique que l’intégralité de la vue est intéressante.

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

Définit ou supprime le focus clavier du contrôle.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Paramètres

*bGrab*<br/>
Si la valeur est TRUE, définit le focus clavier sur le contrôle appelant. Si la valeur est FALSe, supprime le focus clavier du contrôle appelant, à condition qu’il ait le focus.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le contrôle reçoit le focus. Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour un contrôle avec fenêtres, la fonction d’API Windows [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) est appelée. Pour un contrôle sans fenêtre, [IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) est appelé. À l’aide de cet appel, un contrôle sans fenêtre obtient le focus clavier et peut répondre aux messages de fenêtre.

##  <a name="setdirty"></a>  CComControlBase::SetDirty

Définit le membre `m_bRequiresSave` de données sur la valeur dans *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*bDirty*<br/>
Valeur du membre de données [CComControlBase:: m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Notes

`SetDirty(TRUE)`doit être appelé pour signaler que le contrôle a été modifié depuis son dernier enregistrement. La valeur de `m_bRequiresSave` est récupérée avec [CComControlBase:: GetDirty](#getdirty).

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
