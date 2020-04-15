---
title: Classe CComControlBase
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
ms.openlocfilehash: 2420e1643444e6cbbf8edff90bbd3ecb1eac8534
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320775"
---
# <a name="ccomcontrolbase-class"></a>Classe CComControlBase

Cette classe fournit des méthodes pour créer et gérer les contrôles ATL.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Remplacer si `m_nAppearance` votre propriété stock n’est pas de type **court**.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Constructeur.|
|[CComControlBase::CComControlBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Vérifie que le paramètre `IOleObjectImpl::DoVerb` *iVerb* utilisé soit active l’interface utilisateur du contrôle *(iVerb* équivaut OLEIVERB_UIACTIVATE), définit l’action prise lorsque l’utilisateur double-clics le contrôle *(iVerb* égale OLEIVERB_PRIMARY), affiche le contrôle *(iVerb* équivaut OLEIVERB_SHOW), ou active le contrôle *(iVerb* égale OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Vérifie que le paramètre `IOleObjectImpl::DoVerb` *iVerb* utilisé par provoque l’activation et le retour de l’interface utilisateur du contrôle.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Affiche les pages de propriété du contrôle.|
|[CComControlBase::FireViewChange](#fireviewchange)|Appelez cette méthode pour dire au conteneur de redessiner le contrôle, ou d’aviser les éviers enregistrés avis que la vue du contrôle a changé.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Récupère DISPID_AMBIENT_APPEARANCE, le réglage d’apparence actuel pour le contrôle: 0 pour plat et 1 pour la 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Récupère DISPID_AMBIENT_AUTOCLIP, un drapeau indiquant si le conteneur prend en charge la coupure automatique de la zone d’affichage de commande.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Récupère DISPID_AMBIENT_BACKCOLOR, la couleur de fond ambiant pour tous les contrôles, défini par le conteneur.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Récupère DISPID_AMBIENT_CHARSET, l’ensemble de caractères ambiants pour tous les contrôles, défini par le conteneur.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Récupère DISPID_AMBIENT_CODEPAGE, l’ensemble de caractères ambiants pour tous les contrôles, défini par le conteneur.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Récupère DISPID_AMBIENT_DISPLAYASDEFAULT, un drapeau qui est VRAI si le conteneur a marqué le contrôle dans ce site pour être un bouton par défaut, et donc un contrôle de bouton doit se dessiner avec un cadre plus épais.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Récupère DISPID_AMBIENT_DISPLAYNAME, le nom que le conteneur a fourni au contrôle.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Récupère un pointeur sur l’interface ambiante `IFont` du conteneur.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Récupère un pointeur sur l’interface de répartition ambiante `IFontDisp` du conteneur.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Récupère DISPID_AMBIENT_FORECOLOR, la couleur ambiante au premier plan pour tous les contrôles, défini par le conteneur.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Récupère DISPID_AMBIENT_LOCALEID, l’identifiant de la langue utilisée par le conteneur.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Récupère DISPID_AMBIENT_MESSAGEREFLECT, un drapeau indiquant si le conteneur veut recevoir des messages de fenêtre (comme WM_DRAWITEM) comme événements.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Récupère DISPID_AMBIENT_PALETTE, utilisé pour accéder à la HPALETTE du conteneur.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Récupère la propriété du conteneur spécifiée par *id*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Récupère DISPID_AMBIENT_RIGHTTOLEFT, la direction dans laquelle le contenu est affiché par le conteneur.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Récupère DISPID_AMBIENT_SCALEUNITS, les unités ambiantes du conteneur (comme les pouces ou les centimètres) pour l’étiquetage des écrans.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Récupère DISPID_AMBIENT_SHOWGRABHANDLES, un drapeau indiquant si le conteneur permet au contrôle d’afficher des poignées de capture pour lui-même lorsqu’il est actif.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Récupère DISPID_AMBIENT_SHOWHATCHING, un drapeau indiquant si le conteneur permet au contrôle de s’afficher avec un motif éclos lorsque l’interface utilisateur est active.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Récupère DISPID_AMBIENT_SUPPORTSMNEMONICS, un drapeau indiquant si le conteneur prend en charge les mnémoniques du clavier.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Récupère DISPID_AMBIENT_TEXTALIGN, l’alignement du texte préféré par le conteneur : 0 pour l’alignement général (nombres à droite, texte gauche), 1 pour l’alignement gauche, 2 pour l’alignement central, et 3 pour l’alignement droit.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Récupère DISPID_AMBIENT_TOPTOBOTTOM, la direction dans laquelle le contenu est affiché par le conteneur.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Récupère DISPID_AMBIENT_UIDEAD, un drapeau indiquant si le conteneur veut que le contrôle réponde aux actions utilisateur-interface.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Récupère DISPID_AMBIENT_USERMODE, un drapeau indiquant si le conteneur est en mode run (TRUE) ou en mode design (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Retourne la valeur `m_bRequiresSave`du membre de la donnée .|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Récupère les valeurs x et y du numérateur et du dénominateur du facteur zoom pour un contrôle activé pour l’édition en place.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Provoque le contrôle à la transition de l’état inactif à n’importe quel état le verbe dans *iVerb* indique.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Appelez cette méthode pour interroger le site de contrôle pour un pointeur à l’interface identifiée.|
|[CComControlBase::OnDraw](#ondraw)|Remplacez cette méthode pour tirer votre contrôle.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|La `OnDrawAdvanced` valeur par défaut prépare un contexte d’appareil normalisé `OnDraw` pour le dessin, puis appelle la méthode de votre classe de contrôle.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Vérifie que le contrôle est actif sur place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu la mise au point.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Vérifie que l’interface utilisateur est en mode utilisateur, puis active le contrôle.|
|[CComControlBase::OnPaint](#onpaint)|Prépare le conteneur pour la peinture, obtient la zone cliente `OnDraw` du contrôle, puis appelle la méthode de la classe de contrôle.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Vérifie que le contrôle est actif sur place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a obtenu la mise au point.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Remplacez cette méthode pour fournir vos propres gestionnaires d’accélérateur de clavier.|
|[CComControlBase::SendOnClose](#sendonclose)|Informe tous les éviers consultatifs enregistrés auprès du titulaire de l’avis que le contrôle a été fermé.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Informe tous les puits de conseil enregistrés auprès du titulaire de l’avis que les données de contrôle ont changé.|
|[CComControlBase::SendOnRename](#sendonrename)|Informe tous les éviers consultatifs enregistrés auprès du titulaire du conseil que le contrôle a un nouveau surnom.|
|[CComControlBase::SendOnSave](#sendonsave)|Informe tous les éviers consultatifs enregistrés auprès du titulaire de l’avis que le contrôle a été enregistré.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Informe tous les avis enregistrés que l’opinion du contrôle a changé.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Définit ou supprime la mise au point du clavier vers ou à partir du contrôle.|
|[CComControlBase::SetDirty](#setdirty)|Définit le `m_bRequiresSave` membre des données à la valeur en *bDirty*.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Le drapeau indiquant le contrôle ne peut pas être n’importe quelle autre taille.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Indicateur indiquant `IDataObjectImpl::GetData` `CComControlBase::GetZoomInfo` que et doit `m_sizeNatural` définir la `m_sizeExtent`taille du contrôle à partir plutôt que de .|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Indicateur indiquant `IDataObjectImpl::GetData` que doit utiliser des unités HIMETRIC et non des pixels lors du dessin.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Le drapeau indiquant que le contrôle est actif sur place.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Le drapeau indiquant `IOleInPlaceSiteEx` le conteneur prend en charge l’interface et les fonctionnalités de contrôle OCX96, telles que les commandes sans fenêtre et sans scintillement.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Indicateur indiquant si le contrôle a négocié avec le conteneur sur le support pour les caractéristiques de contrôle OCX96 (tels que les commandes sans scintillement et sans fenêtre), et si le contrôle est fenêtre ou sans fenêtre.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Le drapeau indiquant le contrôle veut recomposer sa présentation lorsque le conteneur modifie la taille de l’affichage du contrôle.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Le drapeau indiquant que le contrôle a changé depuis sa dernière économie.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Le drapeau indiquant le contrôle veut redimensionner son étendue naturelle (sa taille physique non dimensionnalisée) lorsque le conteneur modifie la taille de l’écran du contrôle.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Le drapeau indiquant l’interface utilisateur du contrôle, tels que les menus et les barres d’outils, est actif.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Le drapeau indiquant le contrôle utilise la région de fenêtre fournie par conteneur.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Drapeau indiquant que le contrôle a été sans fenêtre, mais peut ou ne peut pas être sans fenêtre maintenant.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Le drapeau indiquant le contrôle doit être fenêtre, même si le conteneur prend en charge les commandes sans fenêtre.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Le drapeau indiquant le contrôle est sans fenêtre.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contient une référence à la poignée de fenêtre associée au contrôle.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Un décompte du nombre de fois où le conteneur a gelé des événements (refus d’accepter des événements) sans dégel intermédiaire des événements (acceptation des événements).|
|[CComControlBase::m_rcPos](#m_rcpos)|La position en pixels du contrôle, exprimée dans les coordonnées du conteneur.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|L’étendue du contrôle dans les unités HIMETRIC (chaque unité est de 0,01 millimètre) pour un affichage particulier.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|La taille physique du contrôle dans les unités HIMETRIC (chaque unité est de 0,01 millimètre).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Un pointeur direct à la connexion consultative sur le conteneur [(IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)du conteneur ).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Un `CComDispatchDriver` objet qui vous permet de récupérer et `IDispatch` de régler les propriétés du conteneur à travers un pointeur.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Un pointeur sur le site client du contrôle à l’intérieur du conteneur.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Fournit un moyen standard de tenir des connexions consultatives entre les objets de données et de conseiller les éviers.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Un pointeur sur [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)du conteneur , [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) pointeur d’interface.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Fournit une mise en œuvre standard d’un moyen d’avoir des connexions consultatives.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer les contrôles ATL. [CComControl Classe](../../atl/reference/ccomcontrol-class.md) dérive `CComControlBase`de . Lorsque vous créez un contrôle standard ou DHTML à l’aide de `CComControlBase`l’assistant de contrôle ATL, l’assistant dérive automatiquement votre classe de .

Pour plus d’informations sur la création d’un contrôle, voir le [tutoriel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur le assistant de projet ATL, voir l’article [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CComControlBase::AppearanceType

Remplacer si `m_nAppearance` votre propriété stock n’est pas de type **court**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Notes

Le assistant de `m_nAppearance` contrôle ATL ajoute la propriété stock de type court. Remplacer `AppearanceType` si vous utilisez un type de données différent.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

Constructeur.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
La poignée à la fenêtre associée au contrôle.

### <a name="remarks"></a>Notes

Initialise la taille du contrôle à 5080X5080 unités HIMETRIC (2"X2") et initialise les `CComControlBase` valeurs des membres de données à NULL ou FALSE.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CComControlBase::CComControlBase

Destructeur.

```
~CComControlBase();
```

### <a name="remarks"></a>Notes

Si le contrôle est `~CComControlBase` vitré, le détruit en appelant [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

Récupère un pointeur vers l'interface demandée.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
Le GUID de l’interface demandée.

*Ppv*<br/>
Un pointeur au pointeur d’interface identifié par *iid*, ou NULL si l’interface n’est pas trouvée.

### <a name="remarks"></a>Notes

Ne gère que les interfaces dans la table de carte COM.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate

Vérifie que le paramètre `IOleObjectImpl::DoVerb` *iVerb* utilisé soit active l’interface utilisateur du contrôle *(iVerb* équivaut OLEIVERB_UIACTIVATE), définit l’action prise lorsque l’utilisateur double-clics le contrôle *(iVerb* égale OLEIVERB_PRIMARY), affiche le contrôle *(iVerb* équivaut OLEIVERB_SHOW), ou active le contrôle *(iVerb* égale OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb (en)*<br/>
Valeur indiquant l’action `DoVerb`à effectuer par .

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si *iVerb* équivaut à OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW ou OLEIVERB_INPLACEACTIVATE; autrement, retourne FALSE.

### <a name="remarks"></a>Notes

Vous pouvez remplacer cette méthode pour définir votre propre verbe d’activation.

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate

Vérifie que le paramètre `IOleObjectImpl::DoVerb` *iVerb* utilisé par provoque l’activation et le retour de l’interface utilisateur du contrôle.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb (en)*<br/>
Valeur indiquant l’action `DoVerb`à effectuer par .

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si *iVerb* équivaut à OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW ou OLEIVERB_INPLACEACTIVATE. Sinon, la méthode renvoie FALSE.

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase::DoVerbProperties

Affiche les pages de propriété du contrôle.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Paramètres

*prcPosRec*<br/>
Réservé.

*hwndParent*<br/>
Poignée de la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>CComControlBase::FireViewChange

Appelez cette méthode pour dire au conteneur de redessiner le contrôle, ou d’aviser les éviers enregistrés avis que la vue du contrôle a changé.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si le contrôle est actif (le membre des données de la classe de contrôle [CComControlBase::m_bInPlaceActive](#m_binplaceactive) est VRAI), informe le conteneur que vous souhaitez redessiner l’ensemble du contrôle. Si le contrôle est inactif, informe les puits de conseil enregistrés du contrôle (par l’intermédiaire du membre des données de la classe de contrôle [CComControlBase::m_spAdviseSink](#m_spadvisesink)) que la vue du contrôle a changé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

Récupère DISPID_AMBIENT_APPEARANCE, le réglage d’apparence actuel pour le contrôle: 0 pour plat et 1 pour la 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Paramètres

*nAppearance*<br/>
La propriété DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

Récupère DISPID_AMBIENT_AUTOCLIP, un drapeau indiquant si le conteneur prend en charge la coupure automatique de la zone d’affichage de commande.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Paramètres

*bAutoClip*<br/>
La propriété DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

Récupère DISPID_AMBIENT_BACKCOLOR, la couleur de fond ambiant pour tous les contrôles, défini par le conteneur.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Paramètres

*CouleurFond*<br/>
La propriété DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

Récupère DISPID_AMBIENT_CHARSET, l’ensemble de caractères ambiants pour tous les contrôles, défini par le conteneur.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Paramètres

*bstrCharSet (en)*<br/>
La propriété DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

Récupère DISPID_AMBIENT_CODEPAGE, la page de code ambiant pour tous les contrôles, définie par le conteneur.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Paramètres

*ulCodePage*<br/>
La propriété DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

Récupère DISPID_AMBIENT_DISPLAYASDEFAULT, un drapeau qui est VRAI si le conteneur a marqué le contrôle dans ce site pour être un bouton par défaut, et donc un contrôle de bouton doit se dessiner avec un cadre plus épais.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
La propriété DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

Récupère DISPID_AMBIENT_DISPLAYNAME, le nom que le conteneur a fourni au contrôle.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Paramètres

*bstrDisplayName (en)*<br/>
La propriété DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CComControlBase::GetAmbientFont

Récupère un pointeur sur l’interface ambiante `IFont` du conteneur.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Un pointeur sur l’interface [IFont](/windows/win32/api/ocidl/nn-ocidl-ifont) ambiante du conteneur.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si la propriété est NULL, le pointeur est NULL. Si le pointeur n’est pas NULL, l’appelant doit libérer le pointeur.

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Récupère un pointeur sur l’interface de répartition ambiante `IFontDisp` du conteneur.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Un pointeur sur l’interface de répartition [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) ambiante du conteneur.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Si la propriété est NULL, le pointeur est NULL. Si le pointeur n’est pas NULL, l’appelant doit libérer le pointeur.

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Récupère DISPID_AMBIENT_FORECOLOR, la couleur ambiante au premier plan pour tous les contrôles, défini par le conteneur.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Paramètres

*Forecolor*<br/>
La propriété DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Récupère DISPID_AMBIENT_LOCALEID, l’identifiant de la langue utilisée par le conteneur.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
La propriété DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Le contrôle peut utiliser cet identifiant pour adapter son interface utilisateur à différentes langues.

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

Récupère DISPID_AMBIENT_MESSAGEREFLECT, un drapeau indiquant si le conteneur veut recevoir `WM_DRAWITEM`des messages de fenêtre (tels que ) comme des événements.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
La propriété DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

Récupère DISPID_AMBIENT_PALETTE, utilisé pour accéder à la HPALETTE du conteneur.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Paramètres

*hPalette (en)*<br/>
La propriété DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

Récupère la propriété du conteneur spécifiée par *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
Identification de la propriété du conteneur à récupérer.

*Var*<br/>
Variable pour recevoir la propriété.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

ATL a fourni un ensemble de fonctions d’aide pour récupérer des propriétés spécifiques, par exemple, [CComControlBase::GetAmbientBackColor](#getambientbackcolor). S’il n’existe pas `GetAmbientProperty`de méthode appropriée disponible, utilisez .

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

Récupère DISPID_AMBIENT_RIGHTTOLEFT, la direction dans laquelle le contenu est affiché par le conteneur.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Paramètres

*bRightToLeft (en)*<br/>
La propriété DISPID_AMBIENT_RIGHTTOLEFT. Définissez vers TRUE si le contenu est affiché de droite à gauche, FALSE s’il est affiché de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

Récupère DISPID_AMBIENT_SCALEUNITS, les unités ambiantes du conteneur (comme les pouces ou les centimètres) pour l’étiquetage des écrans.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Paramètres

*bstrScaleUnits (en)*<br/>
La propriété DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Récupère DISPID_AMBIENT_SHOWGRABHANDLES, un drapeau indiquant si le conteneur permet au contrôle d’afficher des poignées de capture pour lui-même lorsqu’il est actif.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*bShowGrabHandles (en)*<br/>
La propriété DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Récupère DISPID_AMBIENT_SHOWHATCHING, un drapeau indiquant si le conteneur permet au contrôle de s’afficher avec un motif éclos lorsque l’interface utilisateur du contrôle est active.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Paramètres

*bShowHatching (en)*<br/>
La propriété DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

Récupère DISPID_AMBIENT_SUPPORTSMNEMONICS, un drapeau indiquant si le conteneur prend en charge les mnémoniques du clavier.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Paramètres

*bSupportsMnemonics*<br/>
La propriété DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

Récupère DISPID_AMBIENT_TEXTALIGN, l’alignement du texte préféré par le conteneur : 0 pour l’alignement général (nombres à droite, texte gauche), 1 pour l’alignement gauche, 2 pour l’alignement central, et 3 pour l’alignement droit.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Paramètres

*nTextAlign*<br/>
La propriété DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

Récupère DISPID_AMBIENT_TOPTOBOTTOM, la direction dans laquelle le contenu est affiché par le conteneur.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Paramètres

*bTopToBottom (en)*<br/>
La propriété DISPID_AMBIENT_TOPTOBOTTOM. Définissez vers TRUE si le texte est affiché de haut en bas, FALSE s’il est affiché de bas en haut.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

Récupère DISPID_AMBIENT_UIDEAD, un drapeau indiquant si le conteneur veut que le contrôle réponde aux actions utilisateur-interface.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Paramètres

*bUIDead (en)*<br/>
La propriété DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si VRAI, le contrôle ne doit pas répondre. Ce drapeau s’applique quel que soit le drapeau DISPID_AMBIENT_USERMODE. Voir [CComControlBase::GetAmbientUserMode](#getambientusermode).

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

Récupère DISPID_AMBIENT_USERMODE, un drapeau indiquant si le conteneur est en mode run (TRUE) ou en mode design (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
La propriété DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>CComControlBase::GetDirty

Retourne la valeur `m_bRequiresSave`du membre de la donnée .

```
BOOL GetDirty();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur des [m_bRequiresSave des](#m_brequiressave)membres des données .

### <a name="remarks"></a>Notes

Cette valeur est définie à l’aide [de CComControlBase::SetDirty](#setdirty).

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>CComControlBase::GetZoomInfo

Récupère les valeurs x et y du numérateur et du dénominateur du facteur zoom pour un contrôle activé pour l’édition en place.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*di*<br/>
La structure qui tiendra le numérateur et le dénominateur du facteur de zoom. Pour plus d’informations, voir [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Notes

Le facteur zoom est la proportion de la taille naturelle du contrôle dans son étendue actuelle.

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>CComControlBase::InPlaceActivate

Provoque le contrôle à la transition de l’état inactif à n’importe quel état le verbe dans *iVerb* indique.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Paramètres

*iVerb (en)*<br/>
Valeur indiquant l’action à effectuer par [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Pointeur à la position du contrôle sur place.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Avant l’activation, cette méthode vérifie que le contrôle a un site client, vérifie la quantité de contrôle est visible, et obtient l’emplacement du contrôle dans la fenêtre parente. Une fois le contrôle activé, cette méthode active l’interface utilisateur du contrôle et indique au conteneur de rendre le contrôle visible.

Cette méthode récupère `IOleInPlaceSite`également `IOleInPlaceSiteEx`un `IOleInPlaceSiteWindowless` , , ou pointeur d’interface pour le contrôle et le stocke dans le membre de la classe de données de la classe de contrôle [CComControlBase:m_spInPlaceSite](#m_spinplacesite). Les membres de la classe de contrôle des données [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless), et [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) sont mis à vrai que nécessaire.

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase::InternalGetSite

Appelez cette méthode pour interroger le site de contrôle pour un pointeur à l’interface identifiée.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
L’IID du pointeur d’interface qui devrait être retourné en *ppUnkSite*.

*ppUnkSite*<br/>
Adresse de la variable pointeur qui reçoit le pointeur d’interface demandé en *riid*.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Si le site prend en charge l’interface demandée en *riid,* le pointeur est retourné au moyen de *ppUnkSite*. Sinon, *ppUnkSite* est réglé sur NULL.

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase::m_bAutoSize

Le drapeau indiquant le contrôle ne peut pas être n’importe quelle autre taille.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Notes

Ce drapeau est `IOleObjectImpl::SetExtent` vérifié et, si VRAI, provoque le retour de la fonction E_FAIL.

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Si vous ajoutez **l’option Taille automatique** sur [l’onglet Stock Properties](../../atl/reference/stock-properties-atl-control-wizard.md) de l’assistant de contrôle ATL, l’assistant crée automatiquement ce membre de données dans votre classe de contrôle, crée des méthodes de mise et d’obtenir pour la propriété, et prend en charge [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) pour informer automatiquement le conteneur lorsque la propriété change.

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

Indicateur indiquant `IDataObjectImpl::GetData` `CComControlBase::GetZoomInfo` que et doit `m_sizeNatural` définir la `m_sizeExtent`taille du contrôle à partir plutôt que de .

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

Indicateur indiquant `IDataObjectImpl::GetData` que doit utiliser des unités HIMETRIC et non des pixels lors du dessin.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Notes

Chaque unité HIMETRIC logique est de 0,01 millimètre.

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive

Le drapeau indiquant que le contrôle est actif sur place.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Notes

Cela signifie que le contrôle est visible et que sa fenêtre, le cas échéant, est visible, mais que ses menus et ses barres d’outils peuvent ne pas être actifs. Le `m_bUIActive` drapeau indique que l’interface utilisateur du contrôle, comme les menus, est également active.

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

Le drapeau indiquant `IOleInPlaceSiteEx` le conteneur prend en charge l’interface et les fonctionnalités de contrôle OCX96, telles que les commandes sans fenêtre et sans scintillement.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Le membre `m_spInPlaceSite` de données pointe vers un [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interface, en fonction de la valeur de la `m_bWndLess` et `m_bInPlaceSiteEx` les drapeaux. (Le membre `m_bNegotiatedWnd` des données `m_spInPlaceSite` doit être VRAI pour que le pointeur soit valide.)

Si `m_bWndLess` est `m_bInPlaceSiteEx` FALSE et `m_spInPlaceSite` est `IOleInPlaceSiteEx` VRAI, est un pointeur d’interface. Voir [m_spInPlaceSite](#m_spinplacesite) pour un tableau montrant la relation entre ces trois membres de données.

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

Indicateur indiquant si le contrôle a négocié avec le conteneur sur le support pour les caractéristiques de contrôle OCX96 (tels que les commandes sans scintillement et sans fenêtre), et si le contrôle est fenêtre ou sans fenêtre.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Le `m_bNegotiatedWnd` drapeau doit être `m_spInPlaceSite` VRAI pour que le pointeur soit valide.

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

Le drapeau indiquant le contrôle veut recomposer sa présentation lorsque le conteneur modifie la taille de l’affichage du contrôle.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Ce drapeau est vérifié par [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) et, si VRAI, `SetExtent` informe le conteneur de modifications de vue. si ce drapeau est placé, le OLEMISC_RECOMPOSEONRESIZE peu dans le recensement [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) devrait également être fixé.

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

Le drapeau indiquant que le contrôle a changé depuis sa dernière économie.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Notes

La valeur `m_bRequiresSave` de peut être réglé avec [CComControlBase::SetDirty](#setdirty) et récupéré avec [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

Le drapeau indiquant le contrôle veut redimensionner son étendue naturelle (sa taille physique non dimensionnalisée) lorsque le conteneur modifie la taille de l’écran du contrôle.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Notes

Ce drapeau est `IOleObjectImpl::SetExtent` vérifié par et, si `SetExtent` VRAI, `m_sizeNatural`la taille passée est attribué à .

La taille `SetExtent` passée est `m_sizeExtent`toujours assignée à `m_bResizeNatural`, quelle que soit la valeur de .

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase::m_bUIActive

Le drapeau indiquant l’interface utilisateur du contrôle, tels que les menus et les barres d’outils, est actif.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Notes

Le `m_bInPlaceActive` drapeau indique que le contrôle est actif, mais pas que son interface utilisateur est active.

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

Le drapeau indiquant le contrôle utilise la région de fenêtre fournie par conteneur.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

Drapeau indiquant que le contrôle a été sans fenêtre, mais peut ou ne peut pas être sans fenêtre maintenant.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

Le drapeau indiquant le contrôle doit être fenêtre, même si le conteneur prend en charge les commandes sans fenêtre.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase::m_bWndLess

Le drapeau indiquant le contrôle est sans fenêtre.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Le membre `m_spInPlaceSite` de données pointe vers un [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interface, en fonction de la valeur de la `m_bWndLess` et [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) drapeaux. (Le membre des données [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) doit être VRAI pour la [base de CComControl::m_spInPlaceSite](#m_spinplacesite) pointeur pour être valide.)

Si `m_bWndLess` est `m_spInPlaceSite` VRAI, `IOleInPlaceSiteWindowless` est un pointeur d’interface. Voir [CComControlBase:m_spInPlaceSite](#m_spinplacesite) pour un tableau montrant la relation complète entre ces membres de données.

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase::m_hWndCD

Contient une référence à la poignée de fenêtre associée au contrôle.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

Un décompte du nombre de fois où le conteneur a gelé des événements (refus d’accepter des événements) sans dégel intermédiaire des événements (acceptation des événements).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase::m_rcPos

La position en pixels du contrôle, exprimée dans les coordonnées du conteneur.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

L’étendue du contrôle dans les unités HIMETRIC (chaque unité est de 0,01 millimètre) pour un affichage particulier.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Cette taille est mise à l’échelle par l’écran. La taille physique du contrôle `m_sizeNatural` est spécifiée dans le membre des données et est fixe.

Vous pouvez convertir la taille en pixels avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

La taille physique du contrôle dans les unités HIMETRIC (chaque unité est de 0,01 millimètre).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Cette taille est fixe, `m_sizeExtent` tandis que la taille est mise à l’échelle par l’écran.

Vous pouvez convertir la taille en pixels avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

Un pointeur direct à la connexion consultative sur le conteneur [(IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)du conteneur ).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

Un `CComDispatchDriver` objet qui vous permet de récupérer et `IDispatch` de définir les propriétés d’un objet à travers un pointeur.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase::m_spClientSite

Un pointeur sur le site client du contrôle à l’intérieur du conteneur.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

Fournit un moyen standard de tenir des connexions consultatives entre les objets de données et de conseiller les éviers.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Un objet de données est un contrôle qui peut transférer des données et qui implémente [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), dont les méthodes spécifient le format et le support de transfert des données.

L’interface `m_spDataAdviseHolder` implémente les méthodes [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) et [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) pour établir et supprimer les connexions consultatives au conteneur. Le conteneur du contrôle doit implémenter un évier de conseil en soutenant l’interface [IAdviseSink.](/windows/win32/api/objidl/nn-objidl-iadvisesink)

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

Un pointeur sur [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)du conteneur , [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex), ou [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) pointeur d’interface.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

Le `m_spInPlaceSite` pointeur n’est valable que si le [drapeau m_bNegotiatedWnd](#m_bnegotiatedwnd) est VRAI.

Le tableau suivant `m_spInPlaceSite` montre comment le type de pointeur dépend des indicateurs [m_bWndLess](#m_bwndless) et [m_bInPlaceSiteEx](#m_binplacesiteex) des membres des données :

|Type m_spInPlaceSite|m_bWndLess valeur|m_bInPlaceSiteEx valeur|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|VRAI ou FALSE|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

Fournit une mise en œuvre standard d’un moyen d’avoir des connexions consultatives.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Pour utiliser ce membre des données dans votre classe de contrôle, vous devez les déclarer comme un membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas de ce membre des données de la classe de base parce qu’elle est déclarée au sein d’un syndicat de la classe de base.

L’interface `m_spOleAdviseHolder` implémente [l’IOleObject::Conseiller](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) et [IOleObject::Méthodes d’observation](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) pour établir et supprimer les connexions consultatives au conteneur. Le conteneur du contrôle doit implémenter un évier de conseil en soutenant l’interface [IAdviseSink.](/windows/win32/api/objidl/nn-objidl-iadvisesink)

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>CComControlBase::OnDraw

Remplacez cette méthode pour tirer votre contrôle.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*di*<br/>
Une référence à la structure [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) qui contient des informations de dessin telles que l’aspect tirage, les limites de contrôle, et si le dessin est optimisé ou non.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La `OnDraw` valeur par défaut supprime ou restaure le contexte de l’appareil ou ne fait rien, selon les drapeaux définis dans [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

Une `OnDraw` méthode est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle avec le assistant de contrôle ATL. Le défaut de `OnDraw` l’assistant dessine un rectangle avec l’étiquette "ATL 8.0".

### <a name="example"></a>Exemple

Voir l’exemple pour [CComControlBase::GetAmbientAppearance](#getambientappearance).

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

La `OnDrawAdvanced` valeur par défaut prépare un contexte d’appareil normalisé `OnDraw` pour le dessin, puis appelle la méthode de votre classe de contrôle.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Paramètres

*di*<br/>
Une référence à la structure [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) qui contient des informations de dessin telles que l’aspect tirage, les limites de contrôle, et si le dessin est optimisé ou non.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Remplacer cette méthode si vous souhaitez accepter le contexte de l’appareil passé par le conteneur sans la normaliser.

Voir [CComControlBase:OnDraw](#ondraw) pour plus de détails.

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>CComControlBase::OnKillFocus

Vérifie que le contrôle est actif sur place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu la mise au point.

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
Indicateur indiquant si le message de fenêtre a été manipulé avec succès. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

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
Indicateur indiquant si le message de fenêtre a été manipulé avec succès. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>CComControlBase::OnPaint

Prépare le conteneur pour la peinture, obtient la zone cliente `OnDrawAdvanced` du contrôle, puis appelle la méthode de la classe de contrôle.

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
Un CDH existant.

*lParam*<br/>
Réservé.

*lResult*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne toujours zéro.

### <a name="remarks"></a>Notes

Si *wParam* n’est pas NULL, `OnPaint` suppose qu’il contient un HDC valide et l’utilise au lieu de [CComControlBase:m_hWndCD](#m_hwndcd).

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>CComControlBase::OnSetFocus

Vérifie que le contrôle est actif sur place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a obtenu la mise au point.

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
Indicateur indiquant si le message de fenêtre a été manipulé avec succès. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 1.

### <a name="remarks"></a>Notes

Envoie une notification au conteneur que le contrôle a reçu mise au point.

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator

Remplacez cette méthode pour fournir vos propres gestionnaires d’accélérateur de clavier.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Réservé.

*hRet (en)*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Par défaut retourne FALSE.

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>CComControlBase::SendOnClose

Informe tous les éviers consultatifs enregistrés auprès du titulaire de l’avis que le contrôle a été fermé.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Envoie une notification que le contrôle a fermé ses éviers de conseil.

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CComControlBase::SendOnDataChange

Informe tous les puits de conseil enregistrés auprès du titulaire de l’avis que les données de contrôle ont changé.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Paramètres

*advf*<br/>
Informez les drapeaux qui précisent comment l’appel à [IAdviseSink::OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) est fait. Les valeurs proviennent de l’énumération [ADVF.](/windows/win32/api/objidl/ne-objidl-advf)

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CComControlBase::SendOnRename

Informe tous les éviers consultatifs enregistrés auprès du titulaire du conseil que le contrôle a un nouveau surnom.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Paramètres

*pmk*<br/>
Pointeur vers le nouveau surnom du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Envoie une notification que le surnom pour le contrôle a changé.

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>CComControlBase::SendOnSave

Informe tous les éviers consultatifs enregistrés auprès du titulaire de l’avis que le contrôle a été enregistré.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Envoie une notification que le contrôle vient d’enregistrement de ses données.

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

Informe tous les avis enregistrés que l’opinion du contrôle a changé.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Paramètres

*dwAspect*<br/>
L’aspect ou la vue du contrôle.

*Lindex*<br/>
Partie de l'affichage qui a été modifiée. Seulement -1 est valide.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

`SendOnViewChange`appelle [IAdviseSink::OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). La seule valeur du *lindex* actuellement pris en charge est de -1, ce qui indique que l’ensemble de la vue est d’intérêt.

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Définit ou supprime la mise au point du clavier vers ou à partir du contrôle.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Paramètres

*bGrab (en)*<br/>
Si TRUE, définit la mise au point du clavier sur le contrôle d’appel. Si FALSE, supprime la mise au point du clavier du contrôle d’appel, à condition qu’il ait la mise au point.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le contrôle reçoit avec succès la mise au point; autrement, FALSE.

### <a name="remarks"></a>Notes

Pour un contrôle vitré, la fonction API Windows [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) est appelée. Pour un contrôle sans fenêtre, [IOleInPlaceSiteWindowless::SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) est appelé. Grâce à cet appel, un contrôle sans fenêtre obtient la mise au point du clavier et peut répondre aux messages de fenêtre.

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CComControlBase::SetDirty

Définit le `m_bRequiresSave` membre des données à la valeur en *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*bDirty (en)*<br/>
Valeur du membre des données [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Notes

`SetDirty(TRUE)`devrait être appelé pour signaler que le contrôle a changé depuis qu’il a été sauvé pour la dernière fois. La valeur `m_bRequiresSave` de est récupéré avec [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
