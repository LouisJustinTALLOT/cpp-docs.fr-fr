---
title: Classe CComControlBase | Documents Microsoft
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
ms.openlocfilehash: 8b72157db26d4cb7d576e32ca704a32b62b4c2da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366352"
---
# <a name="ccomcontrolbase-class"></a>Classe CComControlBase
Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL_NO_VTABLE CComControlBase
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](#appearancetype)|Remplacer si votre `m_nAppearance` propriété stock n’est pas de type `short`.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Constructeur.|  
|[CComControlBase :: ~ CComControlBase](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Récupère un pointeur vers l'interface demandée.|  
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Vérifie que le `iVerb` paramètre utilisé par `IOleObjectImpl::DoVerb` soit active l’interface utilisateur du contrôle ( `iVerb` est égal à `OLEIVERB_UIACTIVATE`), définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle ( `iVerb` est égal à `OLEIVERB_PRIMARY`), affiche le contrôle ( `iVerb` est égal à `OLEIVERB_SHOW`), ou Active le contrôle ( `iVerb` est égal à **OLEIVERB_INPLACEACTIVATE**).|  
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Vérifie que le `iVerb` paramètre utilisé par `IOleObjectImpl::DoVerb` provoque l’interface du contrôle utilisateur à activer et renvoie **TRUE**.|  
|[CComControlBase::DoVerbProperties](#doverbproperties)|Affiche les pages de propriétés du contrôle.|  
|[CComControlBase::FireViewChange](#fireviewchange)|Appelez cette méthode pour indiquer le conteneur de redessiner le contrôle, ou pour avertir les récepteurs advise inscrit l’affichage du contrôle a changé.|  
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Récupère **DISPID_AMBIENT_APPEARANCE**, l’apparence actuelle définition du contrôle : 0 pour plat et 1 pour la 3D.|  
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Récupère **DISPID_AMBIENT_AUTOCLIP**, un indicateur qui signale si le conteneur prend en charge le découpage automatique de la zone d’affichage de contrôle.|  
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Récupère **DISPID_AMBIENT_BACKCOLOR**, la couleur d’arrière-plan ambiante pour tous les contrôles, définie par le conteneur.|  
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Récupère **DISPID_AMBIENT_CHARSET**, de jeu de caractères ambiant pour tous les contrôles, définies par le conteneur.|  
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Récupère **DISPID_AMBIENT_CODEPAGE**, de jeu de caractères ambiant pour tous les contrôles, définies par le conteneur.|  
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Récupère **DISPID_AMBIENT_DISPLAYASDEFAULT**, un indicateur est **TRUE** si le conteneur a marqué le contrôle de ce site pour être un bouton par défaut, et par conséquent, un contrôle de bouton doit être dessiné avec un frame épais.|  
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Récupère **DISPID_AMBIENT_DISPLAYNAME**, le nom du conteneur a fourni pour le contrôle.|  
|[CComControlBase::GetAmbientFont](#getambientfont)|Récupère un pointeur vers le conteneur d’ambiant `IFont` interface.|  
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Récupère un pointeur vers le conteneur d’ambiant **IFontDisp** interface de dispatch.|  
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Récupère **DISPID_AMBIENT_FORECOLOR**, la couleur de premier plan ambiante pour tous les contrôles, définie par le conteneur.|  
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Récupère **DISPID_AMBIENT_LOCALEID**, l’identificateur de la langue utilisée par le conteneur.|  
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Récupère **DISPID_AMBIENT_MESSAGEREFLECT**, un indicateur qui signale si le conteneur souhaite recevoir des messages de fenêtre (tels que `WM_DRAWITEM`) en tant qu’événements.|  
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Récupère **DISPID_AMBIENT_PALETTE**, utilisé pour accéder au conteneur `HPALETTE`.|  
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Récupère la propriété conteneur spécifiée par `id`.|  
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Récupère **DISPID_AMBIENT_RIGHTTOLEFT**, la direction dans laquelle le contenu est affiché par le conteneur.|  
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Récupère **DISPID_AMBIENT_SCALEUNITS**, unités d’ambiante du conteneur (telles que des pouces ou en centimètres) pour étiqueter les affiche.|  
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Récupère **DISPID_AMBIENT_SHOWGRABHANDLES**, un indicateur qui signale si le conteneur autorise le contrôle afficher les poignées de manipulation pour lui-même lorsqu’il est actif.|  
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Récupère **DISPID_AMBIENT_SHOWHATCHING**, un indicateur qui signale si le conteneur autorise le contrôle lui-même affiche un motif hachuré lors de l’interface utilisateur est active.|  
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Récupère **DISPID_AMBIENT_SUPPORTSMNEMONICS**, un indicateur qui signale si le conteneur prend en charge des touches mnémoniques.|  
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Récupère **DISPID_AMBIENT_TEXTALIGN**, l’alignement de texte préféré par le conteneur : 0 pour l’alignement général (texte de droite, de nombres à gauche), 1 pour l’alignement à gauche, 2 pour l’alignement au centre et 3 pour l’alignement à droite.|  
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Récupère **DISPID_AMBIENT_TOPTOBOTTOM**, la direction dans laquelle le contenu est affiché par le conteneur.|  
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Récupère **DISPID_AMBIENT_UIDEAD**, un indicateur qui signale si le conteneur souhaite que le contrôle de répondre aux actions de l’interface utilisateur.|  
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Récupère **DISPID_AMBIENT_USERMODE**, un indicateur qui indique si le conteneur est en mode d’exécution ( **TRUE**) ou en mode design ( **FALSE**).|  
|[CComControlBase::GetDirty](#getdirty)|Retourne la valeur du membre de données `m_bRequiresSave`.|  
|[CComControlBase::GetZoomInfo](#getzoominfo)|X et y récupère les valeurs de numérateur et dénominateur de facteur de zoom pour un contrôle est activé pour la modification sur place.|  
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Provoque la transition de l’état inactif à l’état du verbe dans le contrôle `iVerb` indique.|  
|[CComControlBase::InternalGetSite](#internalgetsite)|Appelez cette méthode pour interroger le site de contrôle pour un pointeur vers l’interface identifié.|  
|[CComControlBase::OnDraw](#ondraw)|Substituez cette méthode pour dessiner votre contrôle.|  
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|La valeur par défaut **OnDrawAdvanced** prépare un contexte de périphérique normalisé pour le dessin, puis appelle la classe de votre contrôle `OnDraw` (méthode).|  
|[CComControlBase::OnKillFocus](#onkillfocus)|Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur que le contrôle a perdu le focus.|  
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Vérifie que l’interface utilisateur est en mode utilisateur, puis active le contrôle.|  
|[CComControlBase::OnPaint](#onpaint)|Prépare le conteneur pour la peinture, obtient la zone du contrôle client, puis appelle la classe de contrôle `OnDraw` (méthode).|  
|[CComControlBase::OnSetFocus](#onsetfocus)|Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur du contrôle a obtenu le focus.|  
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Substituez cette méthode pour fournir votre propre clavier gestionnaires d’accélérateur.|  
|[CComControlBase::SendOnClose](#sendonclose)|Notifie les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été fermé.|  
|[CComControlBase::SendOnDataChange](#sendondatachange)|Notifie les récepteurs de toutes les notifications inscrits avec le titulaire advise que les données de contrôle a changé.|  
|[CComControlBase::SendOnRename](#sendonrename)|Notifie les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a un nouveau moniker.|  
|[CComControlBase::SendOnSave](#sendonsave)|Notifie les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été enregistré.|  
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Avertit que tous enregistrés récepteurs de notifications que l’affichage du contrôle a été modifié.|  
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Définit ou supprime le focus clavier vers ou à partir du contrôle.|  
|[CComControlBase::SetDirty](#setdirty)|Définit le membre de données `m_bRequiresSave` à la valeur de `bDirty`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComControlBase::m_bAutoSize](#m_bautosize)|Indicateur qui spécifie que le contrôle ne peut pas être de n’importe quelle autre taille.|  
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Indicateur spécifiant si `IDataObjectImpl::GetData` et `CComControlBase::GetZoomInfo` doit définir la taille du contrôle à partir de `m_sizeNatural` plutôt qu’à partir de `m_sizeExtent`.|  
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Indicateur spécifiant si `IDataObjectImpl::GetData` doit utiliser des unités HIMETRIC et non en pixels lors du dessin.|  
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Indicateur qui spécifie que le contrôle est actif en place.|  
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Indicateur précisant s’il le prend en charge de conteneur du **IOleInPlaceSiteEx** interface et OCX96 contrôlent les fonctionnalités, tels que les contrôles sans fenêtre et sans scintillement.|  
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Indicateur précisant si le contrôle a négocié avec le conteneur sur la prise en charge des fonctionnalités de contrôle OCX96 (tels que les contrôles sans fenêtre et sans scintillement), et si le contrôle est avec fenêtres ou sans fenêtre.|  
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Indicateur précisant s’il que souhaite que le contrôle recompose sa présentation lorsque le conteneur change de taille d’affichage du contrôle.|  
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Indicateur qui spécifie que le contrôle a changé depuis son dernier enregistrement.|  
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Indicateur spécifiant le contrôle souhaite redimensionner son extension naturelle (sa taille physique sans échelle) lorsque le conteneur modifie la taille d’affichage du contrôle.|  
|[CComControlBase::m_bUIActive](#m_buiactive)|Indicateur de l’interface du contrôle utilisateur, comme les menus et barres d’outils, est actif.|  
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Indicateur qui spécifie que le contrôle à l’aide de la région de la fenêtre du conteneur.|  
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Indicateur précisant le contrôle a été sans fenêtre, mais peut ou ne peut pas être sans fenêtre maintenant.|  
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Indicateur qui spécifie que le contrôle doit utiliser une fenêtre, même si le conteneur prend en charge les contrôles sans fenêtre.|  
|[CComControlBase::m_bWndLess](#m_bwndless)|Indicateur qui spécifie que le contrôle est sans fenêtre.|  
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contient une référence à un handle de fenêtre associé au contrôle.|  
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Le nombre de fois où le conteneur a figé événements (refusées à accepter des événements) sans un déblocage intermédiaire d’événements (acceptation d’événements).|  
|[CComControlBase::m_rcPos](#m_rcpos)|La position en pixels du contrôle, exprimée dans les coordonnées du conteneur.|  
|[CComControlBase::m_sizeExtent](#m_sizeextent)|L’étendue du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres) pour un affichage particulier.|  
|[CComControlBase::m_sizeNatural](#m_sizenatural)|La taille physique du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres).|  
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Un pointeur direct vers la connexion de notifications sur le conteneur (du conteneur [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).|  
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A `CComDispatchDriver` objet qui vous permet de récupérer et définir les propriétés du conteneur via une `IDispatch` pointeur.|  
|[CComControlBase::m_spClientSite](#m_spclientsite)|Pointeur vers le site du client du contrôle dans le conteneur.|  
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Fournit que le moyen standard maintenir les connexions de notifications entre les objets de données et de récepteurs de notifications.|  
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Un pointeur vers du conteneur [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), ou [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) pointeur d’interface.|  
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Fournit une implémentation standard d’un moyen de contenir des connexions de notifications.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des méthodes pour créer et gérer des contrôles ATL. [Classe de CComControl](../../atl/reference/ccomcontrol-class.md) dérive `CComControlBase`. Lorsque vous créez un contrôle DHTML ou de contrôle Standard à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre classe de `CComControlBase`.  
  
 Pour plus d’informations sur la création d’un contrôle, consultez la [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="appearancetype"></a>  CComControlBase::AppearanceType  
 Remplacer si votre **m_nAppearance** propriété stock n’est pas de type **court**.  
  
```
typedef short AppearanceType;
```  
  
### <a name="remarks"></a>Notes  
 L’Assistant contrôle ATL ajoute **m_nAppearance** Guide de la propriété de type short. Substituer `AppearanceType` si vous utilisez un autre type de données.  
  
##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase  
 Constructeur.  
  
```
CComControlBase(HWND& h);
```  
  
### <a name="parameters"></a>Paramètres  
 `h`  
 Le handle de fenêtre associé au contrôle.  
  
### <a name="remarks"></a>Notes  
 Initialise la taille du contrôle aux unités HIMETRIC de 5080 X 5080 (2 « X 2 ») et initialise le `CComControlBase` des valeurs de membre de données à **NULL** ou **FALSE**.  
  
##  <a name="dtor"></a>  CComControlBase :: ~ CComControlBase  
 Destructeur.  
  
```
~CComControlBase();
```  
  
### <a name="remarks"></a>Notes  
 Si le contrôle est fenêtré, `~CComControlBase` détruit en appelant [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682).  
  
##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 Le GUID de l’interface demandée.  
  
 `ppv`  
 Un pointeur vers le pointeur d’interface identifié par `iid`, ou **NULL** si l’interface est introuvable.  
  
### <a name="remarks"></a>Notes  
 Gère seulement des interfaces dans la table de mappage COM.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]  
  
##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate  
 Vérifie que le `iVerb` paramètre utilisé par `IOleObjectImpl::DoVerb` soit active l’interface utilisateur du contrôle ( `iVerb` est égal à `OLEIVERB_UIACTIVATE`), définit l’action effectuée lorsque l’utilisateur double-clique sur le contrôle ( `iVerb` est égal à `OLEIVERB_PRIMARY`), affiche le contrôle ( `iVerb` est égal à `OLEIVERB_SHOW`), ou Active le contrôle ( `iVerb` est égal à **OLEIVERB_INPLACEACTIVATE**).  
  
```
BOOL DoesVerbActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Paramètres  
 `iVerb`  
 Valeur qui indique l’action à effectuer par `DoVerb`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** si `iVerb` est égal à `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, ou **OLEIVERB_INPLACEACTIVATE**; sinon, retourne **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez substituer cette méthode pour définir votre propre verbe d’activation.  
  
##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate  
 Vérifie que le `iVerb` paramètre utilisé par `IOleObjectImpl::DoVerb` provoque l’interface du contrôle utilisateur à activer et renvoie **TRUE**.  
  
```
BOOL DoesVerbUIActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Paramètres  
 `iVerb`  
 Valeur qui indique l’action à effectuer par `DoVerb`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** si `iVerb` est égal à `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, ou **OLEIVERB_INPLACEACTIVATE**. Sinon, la méthode retourne **FALSE**.  
  
##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties  
 Affiche les pages de propriétés du contrôle.  
  
```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 `prcPosRec`  
 Réservé.  
  
 *hwndParent*  
 Handle de la fenêtre contenant le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]  
  
 [!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]  
  
##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange  
 Appelez cette méthode pour indiquer le conteneur de redessiner le contrôle, ou pour avertir les récepteurs advise inscrit l’affichage du contrôle a changé.  
  
```
HRESULT FireViewChange();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Si le contrôle est actif (le membre de données de classe de contrôle [CComControlBase::m_bInPlaceActive](#m_binplaceactive) est **TRUE**), avertit le conteneur que vous souhaitez redessiner l’ensemble du contrôle. Si le contrôle est inactif, notifie le contrôle de l’inscrit récepteurs de notifications (via le membre de données de classe de contrôle [CComControlBase::m_spAdviseSink](#m_spadvisesink)) que l’affichage du contrôle a été modifié.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]  
  
##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance  
 Récupère **DISPID_AMBIENT_APPEARANCE**, l’apparence actuelle définition du contrôle : 0 pour plat et 1 pour la 3D.  
  
```
HRESULT GetAmbientAppearance(short& nAppearance);
```  
  
### <a name="parameters"></a>Paramètres  
 `nAppearance`  
 La propriété **DISPID_AMBIENT_APPEARANCE**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]  
  
##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip  
 Récupère **DISPID_AMBIENT_AUTOCLIP**, un indicateur qui signale si le conteneur prend en charge le découpage automatique de la zone d’affichage de contrôle.  
  
```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAutoClip*  
 La propriété **DISPID_AMBIENT_AUTOCLIP**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor  
 Récupère **DISPID_AMBIENT_BACKCOLOR**, la couleur d’arrière-plan ambiante pour tous les contrôles, définie par le conteneur.  
  
```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *Couleur d’arrière-plan*  
 La propriété **DISPID_AMBIENT_BACKCOLOR**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet  
 Récupère **DISPID_AMBIENT_CHARSET**, de jeu de caractères ambiant pour tous les contrôles, définies par le conteneur.  
  
```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```  
  
### <a name="parameters"></a>Paramètres  
 *bstrCharSet*  
 La propriété **DISPID_AMBIENT_CHARSET**.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage  
 Récupère **DISPID_AMBIENT_CODEPAGE**, la page de codes ambiante pour tous les contrôles, définie par le conteneur.  
  
```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```  
  
### <a name="parameters"></a>Paramètres  
 *ulCodePage*  
 La propriété **DISPID_AMBIENT_CODEPAGE**.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault  
 Récupère **DISPID_AMBIENT_DISPLAYASDEFAULT**, un indicateur est **TRUE** si le conteneur a marqué le contrôle de ce site pour être un bouton par défaut, et par conséquent, un contrôle de bouton doit être dessiné avec un frame épais.  
  
```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 `bDisplayAsDefault`  
 La propriété **DISPID_AMBIENT_DISPLAYASDEFAULT**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName  
 Récupère **DISPID_AMBIENT_DISPLAYNAME**, le nom du conteneur a fourni pour le contrôle.  
  
```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```  
  
### <a name="parameters"></a>Paramètres  
 *bstrDisplayName*  
 La propriété **DISPID_AMBIENT_DISPLAYNAME**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont  
 Récupère un pointeur vers le conteneur d’ambiant `IFont` interface.  
  
```
HRESULT GetAmbientFont(IFont** ppFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `ppFont`  
 Un pointeur vers le conteneur d’ambiant [IFont](http://msdn.microsoft.com/library/windows/desktop/ms680673) interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Si la propriété est **NULL**, le pointeur est **NULL**. Si le pointeur n’est pas **NULL**, l’appelant doit libérer le pointeur.  
  
##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp  
 Récupère un pointeur vers le conteneur d’ambiant **IFontDisp** interface de dispatch.  
  
```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `ppFont`  
 Un pointeur vers le conteneur d’ambiant [IFontDisp](http://msdn.microsoft.com/library/windows/desktop/ms692695) interface de dispatch.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Si la propriété est **NULL**, le pointeur est **NULL**. Si le pointeur n’est pas **NULL**, l’appelant doit libérer le pointeur.  
  
##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor  
 Récupère **DISPID_AMBIENT_FORECOLOR**, la couleur de premier plan ambiante pour tous les contrôles, définie par le conteneur.  
  
```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *Couleur de premier plan*  
 La propriété **DISPID_AMBIENT_FORECOLOR**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID  
 Récupère **DISPID_AMBIENT_LOCALEID**, l’identificateur de la langue utilisée par le conteneur.  
  
```
HRESULT GetAmbientLocaleID(LCID& lcid);
```  
  
### <a name="parameters"></a>Paramètres  
 `lcid`  
 La propriété **DISPID_AMBIENT_LOCALEID**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Le contrôle peut utiliser cet identificateur pour adapter son interface utilisateur pour différentes langues.  
  
##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect  
 Récupère **DISPID_AMBIENT_MESSAGEREFLECT**, un indicateur qui signale si le conteneur souhaite recevoir des messages de fenêtre (tels que `WM_DRAWITEM`) en tant qu’événements.  
  
```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```  
  
### <a name="parameters"></a>Paramètres  
 `bMessageReflect`  
 La propriété **DISPID_AMBIENT_MESSAGEREFLECT**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette  
 Récupère **DISPID_AMBIENT_PALETTE**, utilisé pour accéder au conteneur `HPALETTE`.  
  
```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```  
  
### <a name="parameters"></a>Paramètres  
 `hPalette`  
 La propriété **DISPID_AMBIENT_PALETTE**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty  
 Récupère la propriété conteneur spécifiée par `dispid`.  
  
```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```  
  
### <a name="parameters"></a>Paramètres  
 `dispid`  
 Identificateur de la propriété de conteneur doit être récupéré.  
  
 `var`  
 Variable devant recevoir la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 ATL a fourni un ensemble de fonctions d’assistance pour récupérer des propriétés spécifiques, par exemple, [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Si aucune méthode appropriée n’est disponible, utilisez `GetAmbientProperty`.  
  
##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft  
 Récupère **DISPID_AMBIENT_RIGHTTOLEFT**, la direction dans laquelle le contenu est affiché par le conteneur.  
  
```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```  
  
### <a name="parameters"></a>Paramètres  
 *bRightToLeft*  
 La propriété **DISPID_AMBIENT_RIGHTTOLEFT**. La valeur **TRUE** si le contenu est affiché de droite à gauche, **FALSE** s’il est affiché de gauche à droite.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits  
 Récupère **DISPID_AMBIENT_SCALEUNITS**, unités d’ambiante du conteneur (telles que des pouces ou en centimètres) pour étiqueter les affiche.  
  
```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```  
  
### <a name="parameters"></a>Paramètres  
 *bstrScaleUnits*  
 La propriété **DISPID_AMBIENT_SCALEUNITS**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles  
 Récupère **DISPID_AMBIENT_SHOWGRABHANDLES**, un indicateur qui signale si le conteneur autorise le contrôle afficher les poignées de manipulation pour lui-même lorsqu’il est actif.  
  
```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```  
  
### <a name="parameters"></a>Paramètres  
 *bShowGrabHandles*  
 La propriété **DISPID_AMBIENT_SHOWGRABHANDLES**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching  
 Récupère **DISPID_AMBIENT_SHOWHATCHING**, un indicateur qui signale si le conteneur autorise le contrôle lui-même affiche un motif hachuré lorsque l’interface utilisateur du contrôle est actif.  
  
```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```  
  
### <a name="parameters"></a>Paramètres  
 *bShowHatching*  
 La propriété **DISPID_AMBIENT_SHOWHATCHING**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics  
 Récupère **DISPID_AMBIENT_SUPPORTSMNEMONICS**, un indicateur qui signale si le conteneur prend en charge des touches mnémoniques.  
  
```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```  
  
### <a name="parameters"></a>Paramètres  
 *bSupportsMnemonics*  
 La propriété **DISPID_AMBIENT_SUPPORTSMNEMONICS**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign  
 Récupère **DISPID_AMBIENT_TEXTALIGN**, l’alignement de texte préféré par le conteneur : 0 pour l’alignement général (texte de droite, de nombres à gauche), 1 pour l’alignement à gauche, 2 pour l’alignement au centre et 3 pour l’alignement à droite.  
  
```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```  
  
### <a name="parameters"></a>Paramètres  
 *nTextAlign*  
 La propriété **DISPID_AMBIENT_TEXTALIGN**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom  
 Récupère **DISPID_AMBIENT_TOPTOBOTTOM**, la direction dans laquelle le contenu est affiché par le conteneur.  
  
```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```  
  
### <a name="parameters"></a>Paramètres  
 *bTopToBottom*  
 La propriété **DISPID_AMBIENT_TOPTOBOTTOM**. La valeur **TRUE** si le texte est affiché de haut en bas, **FALSE** si elle est affichée en bas en haut.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead  
 Récupère **DISPID_AMBIENT_UIDEAD**, un indicateur qui signale si le conteneur souhaite que le contrôle de répondre aux actions de l’interface utilisateur.  
  
```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```  
  
### <a name="parameters"></a>Paramètres  
 *bUIDead*  
 La propriété **DISPID_AMBIENT_UIDEAD**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Si **TRUE**, le contrôle ne doit pas répondre. Cet indicateur s’applique, quel que soit le **DISPID_AMBIENT_USERMODE** indicateur. Consultez [CComControlBase::GetAmbientUserMode](#getambientusermode).  
  
##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode  
 Récupère **DISPID_AMBIENT_USERMODE**, un indicateur qui indique si le conteneur est en mode d’exécution ( **TRUE**) ou en mode design ( **FALSE**).  
  
```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```  
  
### <a name="parameters"></a>Paramètres  
 `bUserMode`  
 La propriété **DISPID_AMBIENT_USERMODE**.  
  
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
 X et y récupère les valeurs de numérateur et dénominateur de facteur de zoom pour un contrôle est activé pour la modification sur place.  
  
```
void GetZoomInfo(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Paramètres  
 `di`  
 La structure qui conserve le facteur de zoom numérateur et dénominateur. Pour plus d’informations, consultez [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).  
  
### <a name="remarks"></a>Notes  
 Le facteur de zoom est la proportion de la taille du contrôle naturelle à son étendue actuelle.  
  
##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate  
 Provoque la transition de l’état inactif à l’état du verbe dans le contrôle `iVerb` indique.  
  
```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `iVerb`  
 Valeur qui indique l’action à effectuer par [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).  
  
 *prcPosRect*  
 Pointeur vers la position du contrôle sur place.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Avant l’activation, cette méthode vérifie que le contrôle a un site client et vérifie la quantité du contrôle est visible et obtient l’emplacement du contrôle dans la fenêtre parente. Une fois que le contrôle est activé, cette méthode active l’interface utilisateur du contrôle et indique au conteneur pour rendre le contrôle visible.  
  
 Cette méthode récupère également une `IOleInPlaceSite`, **IOleInPlaceSiteEx**, ou **IOleInPlaceSiteWindowless** pointeur d’interface pour le contrôle et le stocke dans le membre de données de la classe du contrôle [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Membres de données de la classe de contrôle [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)et [ CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) définie sur true si nécessaire.  
  
##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite  
 Appelez cette méthode pour interroger le site de contrôle pour un pointeur vers l’interface identifié.  
  
```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```  
  
### <a name="parameters"></a>Paramètres  
 `riid`  
 IID du pointeur d’interface qui doit être retourné dans `ppUnkSite`.  
  
 `ppUnkSite`  
 Adresse de la variable pointeur qui reçoit le pointeur d’interface demandé dans `riid`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Si le site prend en charge l’interface demandée dans `riid`, le pointeur est retourné à l’aide de `ppUnkSite`. Sinon, `ppUnkSite` est définie sur NULL.  
  
##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize  
 Indicateur qui spécifie que le contrôle ne peut pas être de n’importe quelle autre taille.  
  
```
unsigned m_bAutoSize:1;
```  
  
### <a name="remarks"></a>Notes  
 Cet indicateur est vérifié par `IOleObjectImpl::SetExtent` et, s’il **TRUE**, provoque la fonction retourne **E_FAIL**.  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Si vous ajoutez le **taille automatique** option sur le [Propriétés Stock](../../atl/reference/stock-properties-atl-control-wizard.md) onglet de l’Assistant contrôle ATL, l’Assistant crée automatiquement ce membre de données dans votre classe de contrôle, crée put et des méthodes pour la propriété get et prend en charge [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) pour vous informer automatiquement le conteneur lorsque la propriété change.  
  
##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural  
 Indicateur spécifiant si `IDataObjectImpl::GetData` et `CComControlBase::GetZoomInfo` doit définir la taille du contrôle à partir de `m_sizeNatural` plutôt qu’à partir de `m_sizeExtent`.  
  
```
unsigned m_bDrawFromNatural:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric  
 Indicateur spécifiant si `IDataObjectImpl::GetData` doit utiliser des unités HIMETRIC et non en pixels lors du dessin.  
  
```
unsigned m_bDrawGetDataInHimetric:1;
```  
  
### <a name="remarks"></a>Notes  
 Chaque unité logique de HIMETRIC 0,01 millimètre.  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive  
 Indicateur qui spécifie que le contrôle est actif en place.  
  
```
unsigned m_bInPlaceActive:1;
```  
  
### <a name="remarks"></a>Notes  
 Cela signifie que le contrôle est visible et sa fenêtre, le cas échéant, est visible, mais ses menus et les barres d’outils ne peuvent pas être actifs. Le `m_bUIActive` indicateur indique l’interface du contrôle utilisateur, tels que des menus, est également actif.  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx  
 Indicateur précisant s’il le prend en charge de conteneur du **IOleInPlaceSiteEx** interface et OCX96 contrôlent les fonctionnalités, tels que les contrôles sans fenêtre et sans scintillement.  
  
```
unsigned m_bInPlaceSiteEx:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Le membre de données `m_spInPlaceSite` pointe vers un [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), ou [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) interface, selon la valeur de la `m_bWndLess` et `m_bInPlaceSiteEx` indicateurs. (Le membre de données `m_bNegotiatedWnd` doit être **TRUE** pour la `m_spInPlaceSite` pointeur soit valide.)  
  
 Si `m_bWndLess` est **FALSE** et `m_bInPlaceSiteEx` est **TRUE**, `m_spInPlaceSite` est un **IOleInPlaceSiteEx** pointeur d’interface. Consultez [m_spInPlaceSite](#m_spinplacesite) pour un tableau montrant la relation entre ces données de trois membres.  
  
##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd  
 Indicateur précisant si le contrôle a négocié avec le conteneur sur la prise en charge des fonctionnalités de contrôle OCX96 (tels que les contrôles sans fenêtre et sans scintillement), et si le contrôle est avec fenêtres ou sans fenêtre.  
  
```
unsigned m_bNegotiatedWnd:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Le `m_bNegotiatedWnd` indicateur doit être **TRUE** pour la `m_spInPlaceSite` pointeur soit valide.  
  
##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize  
 Indicateur précisant s’il que souhaite que le contrôle recompose sa présentation lorsque le conteneur change de taille d’affichage du contrôle.  
  
```
unsigned m_bRecomposeOnResize:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Cet indicateur est vérifié par [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) et, s’il **TRUE**, `SetExtent` avertit le conteneur des modifications d’affichage. Si cet indicateur est défini, le **OLEMISC_RECOMPOSEONRESIZE** bit dans le [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) énumération doit également être définie.  
  
##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave  
 Indicateur qui spécifie que le contrôle a changé depuis son dernier enregistrement.  
  
```
unsigned m_bRequiresSave:1;
```  
  
### <a name="remarks"></a>Notes  
 La valeur de `m_bRequiresSave` peut être défini avec [CComControlBase::SetDirty](#setdirty) et récupéré avec [CComControlBase::GetDirty](#getdirty).  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural  
 Indicateur spécifiant le contrôle souhaite redimensionner son extension naturelle (sa taille physique sans échelle) lorsque le conteneur modifie la taille d’affichage du contrôle.  
  
```
unsigned m_bResizeNatural:1;
```  
  
### <a name="remarks"></a>Notes  
 Cet indicateur est vérifié par `IOleObjectImpl::SetExtent` et, s’il **TRUE**, la taille est passé dans `SetExtent` est affectée à `m_sizeNatural`.  
  
 La taille est passé dans `SetExtent` est toujours attribué au `m_sizeExtent`, quelle que soit la valeur de `m_bResizeNatural`.  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive  
 Indicateur de l’interface du contrôle utilisateur, comme les menus et barres d’outils, est actif.  
  
```
unsigned m_bUIActive:1;
```  
  
### <a name="remarks"></a>Notes  
 Le `m_bInPlaceActive` indicateur indique que le contrôle est actif, mais pas que son interface utilisateur est actif.  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn  
 Indicateur qui spécifie que le contrôle à l’aide de la région de la fenêtre du conteneur.  
  
```
unsigned m_bUsingWindowRgn:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless  
 Indicateur précisant le contrôle a été sans fenêtre, mais peut ou ne peut pas être sans fenêtre maintenant.  
  
```
unsigned m_bWasOnceWindowless:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly  
 Indicateur qui spécifie que le contrôle doit utiliser une fenêtre, même si le conteneur prend en charge les contrôles sans fenêtre.  
  
```
unsigned m_bWindowOnly:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess  
 Indicateur qui spécifie que le contrôle est sans fenêtre.  
  
```
unsigned m_bWndLess:1;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Le membre de données `m_spInPlaceSite` pointe vers un [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), ou [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) interface, selon la valeur de la `m_bWndLess` et [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) indicateurs. (Le membre de données [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) doit être **TRUE** pour le [CComControlBase::m_spInPlaceSite](#m_spinplacesite) pointeur soit valide.)  
  
 Si `m_bWndLess` est **TRUE**, `m_spInPlaceSite` est un **IOleInPlaceSiteWindowless** pointeur d’interface. Consultez [CComControlBase::m_spInPlaceSite](#m_spinplacesite) pour un tableau montrant la relation complète entre ces membres de données.  
  
##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD  
 Contient une référence à un handle de fenêtre associé au contrôle.  
  
```
HWND& m_hWndCD;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents  
 Le nombre de fois où le conteneur a figé événements (refusées à accepter des événements) sans un déblocage intermédiaire d’événements (acceptation d’événements).  
  
```
short m_nFreezeEvents;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos  
 La position en pixels du contrôle, exprimée dans les coordonnées du conteneur.  
  
```
RECT m_rcPos;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent  
 L’étendue du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres) pour un affichage particulier.  
  
```
SIZE m_sizeExtent;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Cette taille est monté en charge par l’affichage. La taille du contrôle physique est spécifiée dans le `m_sizeNatural` membre de données et est fixe.  
  
 Vous pouvez convertir la taille en pixels, avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural  
 La taille physique du contrôle en unités HIMETRIC (chaque unité représente 0,01 millimètres).  
  
```
SIZE m_sizeNatural;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Cette taille est fixe, lors de la taille en `m_sizeExtent` est mis à l’échelle par l’affichage.  
  
 Vous pouvez convertir la taille en pixels, avec la fonction globale [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink  
 Un pointeur direct vers la connexion de notifications sur le conteneur (du conteneur [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).  
  
```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```     
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch  
 A `CComDispatchDriver` objet qui vous permet de récupérer et définir les propriétés d’un objet via une `IDispatch` pointeur.  
  
```
CComDispatchDriver m_spAmbientDispatch;
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite  
 Pointeur vers le site du client du contrôle dans le conteneur.  
  
```
CComPtr<IOleClientSite>
    m_spClientSite;
```     
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder  
 Fournit que le moyen standard maintenir les connexions de notifications entre les objets de données et de récepteurs de notifications.  
  
```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```     
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Un objet de données est un contrôle qui peut transférer des données et qui implémente [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421), dont les méthodes spécifient le support de format et le transfert des données.  
  
 L’interface `m_spDataAdviseHolder` implémente la [IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) et [IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) méthodes pour définir et supprimer des connexions de notifications au conteneur. Le conteneur du contrôle doit implémenter un récepteur de notifications en prenant en charge la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interface.  
  
##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite  
 Un pointeur vers du conteneur [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), ou [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) pointeur d’interface.  
  
```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```     
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 Le `m_spInPlaceSite` pointeur est valide uniquement si le [m_bNegotiatedWnd](#m_bnegotiatedwnd) indicateur est **TRUE**.  
  
 Le tableau suivant montre comment la `m_spInPlaceSite` dépend de type pointeur le [m_bWndLess](#m_bwndless) et [m_bInPlaceSiteEx](#m_binplacesiteex) indicateurs de membres de données :  
  
|Type de m_spInPlaceSite|m_bWndLess valeur|m_bInPlaceSiteEx valeur|  
|---------------------------|-----------------------|-----------------------------|  
|**IOleInPlaceSiteWindowless**|**TRUE**|**TRUE** ou **FALSE**|  
|**IOleInPlaceSiteEx**|**FALSE**|**TRUE**|  
|`IOleInPlaceSite`|**FALSE**|**FALSE**|  
  
##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder  
 Fournit une implémentation standard d’un moyen de contenir des connexions de notifications.  
  
```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```     
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Pour utiliser ce membre de données dans votre classe de contrôle, vous devez la déclarer comme membre de données dans votre classe de contrôle. Votre classe de contrôle n’héritera pas ce membre de données à partir de la classe de base, car il est déclaré dans une union dans la classe de base.  
  
 L’interface `m_spOleAdviseHolder` implémente la [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) et [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) méthodes pour définir et supprimer des connexions de notifications au conteneur. Le conteneur du contrôle doit implémenter un récepteur de notifications en prenant en charge la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interface.  
  
##  <a name="ondraw"></a>  CComControlBase::OnDraw  
 Substituez cette méthode pour dessiner votre contrôle.  
  
```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Paramètres  
 `di`  
 Une référence à la [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) structure qui contient des informations de dessin de l’aspect de dessin, les limites du contrôle, et si le dessin est optimisé ou non.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 La valeur par défaut `OnDraw` supprime ou restaure le contexte de périphérique ou ne fait rien, selon les indicateurs définis [CComControlBase::OnDrawAdvanced](#ondrawadvanced).  
  
 Un `OnDraw` (méthode) est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle avec l’Assistant contrôle ATL. Par défaut de l’Assistant `OnDraw` Dessine un rectangle avec l’étiquette « ATL 8.0 ».  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CComControlBase::GetAmbientAppearance](#getambientappearance).  
  
##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced  
 La valeur par défaut `OnDrawAdvanced` prépare un contexte de périphérique normalisé pour le dessin, puis appelle la classe de votre contrôle `OnDraw` (méthode).  
  
```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Paramètres  
 `di`  
 Une référence à la [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) structure qui contient des informations de dessin de l’aspect de dessin, les limites du contrôle, et si le dessin est optimisé ou non.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
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
 `nMsg`  
 Réservé.  
  
 `wParam`  
 Réservé.  
  
 `lParam`  
 Réservé.  
  
 `bHandled`  
 Indicateur qui indique si le message de fenêtre a été correctement géré. La valeur par défaut est `FALSE`.  
  
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
 `nMsg`  
 Réservé.  
  
 `wParam`  
 Réservé.  
  
 `lParam`  
 Réservé.  
  
 `bHandled`  
 Indicateur qui indique si le message de fenêtre a été correctement géré. La valeur par défaut est `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours 1.  
  
##  <a name="onpaint"></a>  CComControlBase::OnPaint  
 Prépare le conteneur pour la peinture, obtient la zone du contrôle client, puis appelle la classe de contrôle `OnDrawAdvanced` (méthode).  
  
```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMsg`  
 Réservé.  
  
 `wParam`  
 HDC existant.  
  
 `lParam`  
 Réservé.  
  
 `lResult`  
 Réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours zéro.  
  
### <a name="remarks"></a>Notes  
 Si `wParam` n’est pas NULL, `OnPaint` part du principe qu’il contient un HDC valide et utilise à la place de [CComControlBase::m_hWndCD](#m_hwndcd).  
  
##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus  
 Vérifie que le contrôle est actif en place et dispose d’un site de contrôle valide, puis informe le conteneur du contrôle a obtenu le focus.  
  
```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMsg`  
 Réservé.  
  
 `wParam`  
 Réservé.  
  
 `lParam`  
 Réservé.  
  
 `bHandled`  
 Indicateur qui indique si le message de fenêtre a été correctement géré. La valeur par défaut est `FALSE`.  
  
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
 `pMsg`  
 Réservé.  
  
 *hRet*  
 Réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Par défaut retourne **FALSE**.  
  
##  <a name="sendonclose"></a>  CComControlBase::SendOnClose  
 Notifie les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été fermé.  
  
```
HRESULT SendOnClose();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Envoie une notification que le contrôle a fermé ses récepteurs de notifications.  
  
##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange  
 Notifie les récepteurs de toutes les notifications inscrits avec le titulaire advise que les données de contrôle a changé.  
  
```
HRESULT SendOnDataChange(DWORD advf = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *ADVF*  
 Informez les indicateurs qui spécifient comment l’appel à [IAdviseSink::OnDataChange](http://msdn.microsoft.com/library/windows/desktop/ms687283) est effectuée. Les valeurs sont à partir de la [ADVF](http://msdn.microsoft.com/library/windows/desktop/ms693742) énumération.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="sendonrename"></a>  CComControlBase::SendOnRename  
 Notifie les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a un nouveau moniker.  
  
```
HRESULT SendOnRename(IMoniker* pmk);
```  
  
### <a name="parameters"></a>Paramètres  
 *PMK*  
 Pointeur vers le nouveau moniker du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Envoie une notification indiquant que le moniker du contrôle a changé.  
  
##  <a name="sendonsave"></a>  CComControlBase::SendOnSave  
 Notifie les récepteurs de toutes les notifications inscrits avec le détenteur de notifications que le contrôle a été enregistré.  
  
```
HRESULT SendOnSave();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Envoie une notification que le contrôle vient de ses données.  
  
##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange  
 Avertit que tous enregistrés récepteurs de notifications que l’affichage du contrôle a été modifié.  
  
```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwAspect`  
 La hauteur ou la vue du contrôle.  
  
 *lindex*  
 La partie de la vue a changé. Uniquement -1 est valide.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 `SendOnViewChange` appels [IAdviseSink::OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337). La seule valeur de *lIndex Valeur de type* actuellement pris en charge est -1, ce qui indique que la vue d’ensemble présente un intérêt.  
  
##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus  
 Définit ou supprime le focus clavier vers ou à partir du contrôle.  
  
```
BOOL SetControlFocus(BOOL bGrab);
```  
  
### <a name="parameters"></a>Paramètres  
 *bGrab*  
 Si **TRUE**, définit le focus clavier au contrôle appelant. Si **FALSE**, supprime le focus clavier à partir du contrôle en appelant, sous réserve qu’il a le focus.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** si le contrôle reçoit le focus ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Pour un contrôle avec fenêtres, la fonction API Windows [SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312) est appelée. Pour un contrôle sans fenêtre, [IOleInPlaceSiteWindowless::SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms679745) est appelée. Via cet appel, un contrôle sans fenêtre Obtient le focus clavier et peut répondre aux messages de fenêtre.  
  
##  <a name="setdirty"></a>  CComControlBase::SetDirty  
 Définit le membre de données `m_bRequiresSave` à la valeur de `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Paramètres  
 `bDirty`  
 Valeur du membre de données [CComControlBase::m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Notes  
 **SetDirty(TRUE)** doit être appelée pour signaler que le contrôle a changé depuis son dernier enregistrement. La valeur de `m_bRequiresSave` est récupérée avec [CComControlBase::GetDirty](#getdirty).  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
