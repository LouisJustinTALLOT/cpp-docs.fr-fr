---
title: CPANE, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPane
- AFXPANE/CPane
- AFXPANE/CPane::AdjustSizeImmediate
- AFXPANE/CPane::AllocElements
- AFXPANE/CPane::AllowShowOnPaneMenu
- AFXPANE/CPane::CalcAvailableSize
- AFXPANE/CPane::CalcInsideRect
- AFXPANE/CPane::CalcRecentDockedRect
- AFXPANE/CPane::CalcSize
- AFXPANE/CPane::CanBeDocked
- AFXPANE/CPane::CanBeTabbedDocument
- AFXPANE/CPane::ConvertToTabbedDocument
- AFXPANE/CPane::CopyState
- AFXPANE/CPane::Create
- AFXPANE/CPane::CreateDefaultMiniframe
- AFXPANE/CPane::CreateEx
- AFXPANE/CPane::DockByMouse
- AFXPANE/CPane::DockPane
- AFXPANE/CPane::DockPaneStandard
- AFXPANE/CPane::DockToFrameWindow
- AFXPANE/CPane::DoesAllowSiblingBars
- AFXPANE/CPane::FloatPane
- AFXPANE/CPane::GetAvailableExpandSize
- AFXPANE/CPane::GetAvailableStretchSize
- AFXPANE/CPane::GetBorders
- AFXPANE/CPane::GetClientHotSpot
- AFXPANE/CPane::GetDockSiteRow
- AFXPANE/CPane::GetExclusiveRowMode
- AFXPANE/CPane::GetHotSpot
- AFXPANE/CPane::GetMinSize
- AFXPANE/CPane::GetPaneName
- AFXPANE/CPane::GetVirtualRect
- AFXPANE/CPane::IsChangeState
- AFXPANE/CPane::IsDragMode
- AFXPANE/CPane::IsInFloatingMultiPaneFrameWnd
- AFXPANE/CPane::IsLeftOf
- AFXPANE/CPane::IsResizable
- AFXPANE/CPane::IsTabbed
- AFXPANE/CPane::LoadState
- AFXPANE/CPane::MoveByAlignment
- AFXPANE/CPane::MovePane
- AFXPANE/CPane::OnAfterChangeParent
- AFXPANE/CPane::OnBeforeChangeParent
- AFXPANE/CPane::OnPressCloseButton
- AFXPANE/CPane::OnShowControlBarMenu
- AFXPANE/CPane::RecalcLayout
- AFXPANE/CPane::SaveState
- AFXPANE/CPane::SetActiveInGroup
- AFXPANE/CPane::SetBorders
- AFXPANE/CPane::SetClientHotSpot
- AFXPANE/CPane::SetDockState
- AFXPANE/CPane::SetExclusiveRowMode
- AFXPANE/CPane::SetMiniFrameRTC
- AFXPANE/CPane::SetMinSize
- AFXPANE/CPane::SetVirtualRect
- AFXPANE/CPane::StretchPaneDeferWndPos
- AFXPANE/CPane::ToggleAutoHide
- AFXPANE/CPane::UndockPane
- AFXPANE/CPane::UpdateVirtualRect
- AFXPANE/CPane::OnAfterDock
- AFXPANE/CPane::OnAfterFloat
- AFXPANE/CPane::OnBeforeDock
- AFXPANE/CPane::OnBeforeFloat
- AFXPANE/CPane::m_bHandleMinSize
- AFXPANE/CPane::m_recentDockInfo
dev_langs:
- C++
helpviewer_keywords:
- CPane [MFC], AdjustSizeImmediate
- CPane [MFC], AllocElements
- CPane [MFC], AllowShowOnPaneMenu
- CPane [MFC], CalcAvailableSize
- CPane [MFC], CalcInsideRect
- CPane [MFC], CalcRecentDockedRect
- CPane [MFC], CalcSize
- CPane [MFC], CanBeDocked
- CPane [MFC], CanBeTabbedDocument
- CPane [MFC], ConvertToTabbedDocument
- CPane [MFC], CopyState
- CPane [MFC], Create
- CPane [MFC], CreateDefaultMiniframe
- CPane [MFC], CreateEx
- CPane [MFC], DockByMouse
- CPane [MFC], DockPane
- CPane [MFC], DockPaneStandard
- CPane [MFC], DockToFrameWindow
- CPane [MFC], DoesAllowSiblingBars
- CPane [MFC], FloatPane
- CPane [MFC], GetAvailableExpandSize
- CPane [MFC], GetAvailableStretchSize
- CPane [MFC], GetBorders
- CPane [MFC], GetClientHotSpot
- CPane [MFC], GetDockSiteRow
- CPane [MFC], GetExclusiveRowMode
- CPane [MFC], GetHotSpot
- CPane [MFC], GetMinSize
- CPane [MFC], GetPaneName
- CPane [MFC], GetVirtualRect
- CPane [MFC], IsChangeState
- CPane [MFC], IsDragMode
- CPane [MFC], IsInFloatingMultiPaneFrameWnd
- CPane [MFC], IsLeftOf
- CPane [MFC], IsResizable
- CPane [MFC], IsTabbed
- CPane [MFC], LoadState
- CPane [MFC], MoveByAlignment
- CPane [MFC], MovePane
- CPane [MFC], OnAfterChangeParent
- CPane [MFC], OnBeforeChangeParent
- CPane [MFC], OnPressCloseButton
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], RecalcLayout
- CPane [MFC], SaveState
- CPane [MFC], SetActiveInGroup
- CPane [MFC], SetBorders
- CPane [MFC], SetClientHotSpot
- CPane [MFC], SetDockState
- CPane [MFC], SetExclusiveRowMode
- CPane [MFC], SetMiniFrameRTC
- CPane [MFC], SetMinSize
- CPane [MFC], SetVirtualRect
- CPane [MFC], StretchPaneDeferWndPos
- CPane [MFC], ToggleAutoHide
- CPane [MFC], UndockPane
- CPane [MFC], UpdateVirtualRect
- CPane [MFC], OnAfterDock
- CPane [MFC], OnAfterFloat
- CPane [MFC], OnBeforeDock
- CPane [MFC], OnBeforeFloat
- CPane [MFC], m_bHandleMinSize
- CPane [MFC], m_recentDockInfo
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 629e10d06a59b926604fad3b3a6e191fefcb71e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384500"
---
# <a name="cpane-class"></a>CPane Class

Le `CPane` classe est une amélioration de la [CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md). Si vous mettez à niveau un projet MFC existant, remplacez toutes les occurrences de `CControlBar` avec `CPane`.

## <a name="syntax"></a>Syntaxe

```
class CPane : public CBasePane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CPane::~CPane`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|Immédiatement recalcule la disposition d’un volet.|
|[CPane::AllocElements](#allocelements)|Alloue du stockage à un usage interne.|
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|Spécifie si le volet est répertorié dans la liste générée par runtime des volets de l’application.|
|[CPane::CalcAvailableSize](#calcavailablesize)|Calcule la différence de taille entre un rectangle spécifié et le rectangle actuel de la fenêtre.|
|[CPane::CalcInsideRect](#calcinsiderect)|Calcule l’intérieur rectangle d’un volet, en prenant en compte les bordures et les barres de défilement.|
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|Calcule le rectangle récemment ancré.|
|[CPane::CalcSize](#calcsize)|Calcule la taille du volet.|
|[CPane::CanBeDocked](#canbedocked)|Détermine si le volet peut être ancré dans le volet de base spécifié.|
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|Détermine si le volet peut être converti en un document à onglets.|
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|Convertit un volet ancrable à un document à onglets.|
|[CPane::CopyState](#copystate)|Copie l’état d’un volet. (Substitue [CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate).)|
|[CPane::Create](#create)|Crée une barre de contrôle et l’attache à la `CPane` objet.|
|[CPane::CreateDefaultMiniframe](#createdefaultminiframe)|Crée une fenêtre mini-frame pour un volet flottant.|
|[CPane::CreateEx](#createex)|Crée une barre de contrôle et l’attache à la `CPane` objet.|
|`CPane::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CPane::DockByMouse](#dockbymouse)|Ancre un volet à l’aide de la souris d’ancrage (méthode).|
|[CPane::DockPane](#dockpane)|Ancre le volet flottant à un volet de base.|
|[CPane::DockPaneStandard](#dockpanestandard)|Ancre un volet à l’aide de contour de la station d’accueil (standard).|
|[CPane::DockToFrameWindow](#docktoframewindow)|Ancre un volet ancrable à un frame. (Substitue `CBasePane::DockToFrameWindow`.)|
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|Indique si vous pouvez ancrer un autre volet à la même ligne où le volet actif est ancré.|
|[CPane::FloatPane](#floatpane)|Flotte le volet.|
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|Retourne la quantité, en pixels, que le volet peut développer.|
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|Retourne la quantité, en pixels, permettant de réduire le volet.|
|[CPane::GetBorders](#getborders)|Retourne la largeur des bordures du volet.|
|[CPane::GetClientHotSpot](#getclienthotspot)|Retourne le *réactive* pour le volet.|
|[CPane::GetDockSiteRow](#getdocksiterow)|Retourne la ligne d’ancrage dans lequel le volet est ancré.|
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|Détermine si le volet est en mode exclusif de ligne.|
|[CPane::GetHotSpot](#gethotspot)|Retourne la zone réactive qui est stockée dans un sous-jacent `CMFCDragFrameImpl` objet.|
|[CPane::GetMinSize](#getminsize)|Récupère la valeur minimale autorisée pour le volet.|
|[CPane::GetPaneName](#getpanename)|Récupère le titre du volet.|
|`CPane::GetResizeStep`|Utilisé en interne.|
|`CPane::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CPane::GetVirtualRect](#getvirtualrect)|Récupère le *rectangle virtuel* du volet.|
|[CPane::IsChangeState](#ischangestate)|Comme le volet est déplacée, cette méthode analyse la position du volet par rapport à d’autres volets, ancrer les lignes et les fenêtres mini-frame et retourne la valeur AFX_CS_STATUS appropriée.|
|[CPane::IsDragMode](#isdragmode)|Spécifie si le volet est glissé.|
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Spécifie si le volet est dans une fenêtre frame de plusieurs volets. (Substitue `CBasePane::IsInFloatingMultiPaneFrameWnd`.)|
|[CPane::IsLeftOf](#isleftof)|Détermine si le volet est laissé de (ou plus) du rectangle spécifié.|
|[CPane::IsResizable](#isresizable)|Détermine si le volet peut être redimensionné. (Substitue [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CPane::IsTabbed](#istabbed)|Détermine si le volet a été inséré dans le contrôle onglet d’une fenêtre à onglets. (Substitue [CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed).)|
|[CPane::LoadState](#loadstate)|Charge l’état du volet à partir du Registre. (Substitue [CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate).)|
|[CPane::MoveByAlignment](#movebyalignment)|Déplace le volet et le rectangle virtuel selon la valeur spécifiée.|
|[CPane::MovePane](#movepane)|Déplace le volet vers le rectangle spécifié.|
|[CPane::OnAfterChangeParent](#onafterchangeparent)|Appelé par le framework lorsque le parent d’un volet a changé.|
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|Appelé par le framework lorsque le parent du volet est va être modifiée.|
|[CPane::OnPressCloseButton](#onpressclosebutton)|Appelé par l’infrastructure quand l’utilisateur choisit le bouton Fermer dans la légende pour le volet.|
|`CPane::OnProcessDblClk`|Utilisé en interne.|
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Appelé par l'infrastructure quand un menu de volet spécial va être affiché.|
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Appelé par l'infrastructure quand un menu de volet spécial va être affiché.|
|`CPane::PrepareToDock`|Utilisé en interne.|
|[CPane::RecalcLayout](#recalclayout)|Recalcule les informations de disposition pour le volet. (Substitue [CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout).)|
|[CPane::SaveState](#savestate)|Enregistre l’état du volet dans le Registre. (Substitue [CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate).)|
|[CPane::SetActiveInGroup](#setactiveingroup)|Marque un volet comme actif.|
|[CPane::SetBorders](#setborders)|Définit les valeurs de la bordure du volet.|
|[CPane::SetClientHotSpot](#setclienthotspot)|Définit la zone réactive du volet.|
|[CPane::SetDockState](#setdockstate)|Restaurations d’ancrage des informations d’état pour le volet.|
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|Active ou désactive le mode de ligne exclusifs.|
|[CPane::SetMiniFrameRTC](#setminiframertc)|Définit les informations de classe runtime pour la fenêtre mini-frame par défaut.|
|[CPane::SetMinSize](#setminsize)|Définit la valeur minimale autorisée pour le volet.|
|[CPane::SetVirtualRect](#setvirtualrect)|Définit le *rectangle virtuel* du volet.|
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|Étire le volet verticalement ou horizontalement en fonction de style d’ancrage.|
|[CPane::ToggleAutoHide](#toggleautohide)|Mode de masquage automatique de bascules.|
|[CPane::UndockPane](#undockpane)|Supprime le volet à partir du site d’ancrage, le curseur de la valeur par défaut ou la fenêtre mini-frame dans lequel il est actuellement ancré. (Substitue [CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane).)|
|[CPane::UpdateVirtualRect](#updatevirtualrect)|Met à jour le rectangle virtuel.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CPane::OnAfterDock](#onafterdock)|Appelé par le framework lorsqu’un volet a été verrouillée.|
|[CPane::OnAfterFloat](#onafterfloat)|Appelé par l’infrastructure quand un volet flotte.|
|[CPane::OnBeforeDock](#onbeforedock)|Appelé par le framework lorsque le volet est sur le point d’être ancrée.|
|[CPane::OnBeforeFloat](#onbeforefloat)|Appelé par le framework lorsqu’un volet est sur le point d’être flottantes.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|Permet une gestion cohérente de la taille minimale pour les volets.|
|[CPane::m_recentDockInfo](#m_recentdockinfo)|Contient des informations récentes sur la station d’accueil.|

## <a name="remarks"></a>Notes

En règle générale, `CPane` objets ne sont pas instanciées directement. Si vous avez besoin d’un volet qui dispose de fonctionnalités d’ancrage, dérivez votre objet de [CDockablePane](../../mfc/reference/cdockablepane-class.md). Si vous avez besoin des fonctionnalités de la barre d’outils, dérivez votre objet de [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).

Lorsque vous dérivez une classe de `CPane`, elle peut être ancrée dans un [CDockSite](../../mfc/reference/cdocksite-class.md) et il peut flotter dans un [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxPane.h

##  <a name="adjustsizeimmediate"></a>  CPane::AdjustSizeImmediate

Immédiatement recalcule la disposition d’un volet.

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRecalcLayout*<br/>
[in] TRUE pour recalculer automatiquement la disposition du volet. Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode lorsque vous modifiez dynamiquement la disposition d’un volet. Vous souhaiterez par exemple, appelez cette méthode lorsque vous masquer ou afficher des boutons de barre d’outils.

##  <a name="allocelements"></a>  CPane::AllocElements

Alloue du stockage à un usage interne.

```
BOOL AllocElements(
    int nElements,
    int cbElement);
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
[in] Le nombre d’éléments pour lesquels allouer le stockage.

*cbElement*<br/>
[in] La taille, en octets, d’un élément.

### <a name="return-value"></a>Valeur de retour

FALSE si l’allocation de mémoire échoue ; Sinon, la valeur TRUE.

##  <a name="allowshowonpanemenu"></a>  CPane::AllowShowOnPaneMenu

Spécifie si le volet est répertorié dans la liste générée par runtime des volets de l’application.

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet s’affiche dans la liste ; Sinon, FALSE. L’implémentation de base toujours retourne la valeur TRUE.

### <a name="remarks"></a>Notes

L’application générée par AppWizard contient une option de menu qui répertorie les volets qu’il contient. Cette méthode détermine si le volet s’affiche dans la liste.

##  <a name="calcavailablesize"></a>  CPane::CalcAvailableSize

Calcule la différence de taille entre un rectangle spécifié et le rectangle actuel de la fenêtre.

```
virtual CSize CalcAvailableSize(CRect rectRequired);
```

### <a name="parameters"></a>Paramètres

*rectRequired*<br/>
[in] Le rectangle requis.

### <a name="return-value"></a>Valeur de retour

La différence entre la largeur et hauteur entre *rectRequired* et le rectangle actuel de la fenêtre.

##  <a name="calcinsiderect"></a>  CPane::CalcInsideRect

Calcule l’intérieur rectangle d’un volet, y compris les bordures et les barres de défilement.

```
void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[out] Contient la taille et le décalage de la zone cliente du volet.

*bHorz*<br/>
[in] TRUE si le volet est orienté horizontalement ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure lorsqu’elle doit recalculer la disposition d’un volet. Le *rect* paramètre est renseigné avec la taille et le décalage de la zone cliente du volet. Cela inclut les bordures et des barres de défilement.

##  <a name="calcrecentdockedrect"></a>  CPane::CalcRecentDockedRect

Calcule le rectangle récemment ancré.

```
void CalcRecentDockedRect();
```

### <a name="remarks"></a>Notes

Cette méthode met à jour [CPane::m_recentDockInfo](#m_recentdockinfo).

##  <a name="calcsize"></a>  CPane::CalcSize

Calcule la taille du volet.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Paramètres

*bVertDock*<br/>
[in] TRUE si le volet est ancré verticalement, FALSE sinon.

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut de cette méthode retourne la taille (0, 0).

### <a name="remarks"></a>Notes

Les classes dérivées doivent substituer cette méthode.

##  <a name="canbedocked"></a>  CPane::CanBeDocked

Détermine si le volet peut être ancré dans le volet de base spécifié.

```
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;
```

### <a name="parameters"></a>Paramètres

*pDockBar*<br/>
[in] Spécifie le volet où ce volet doit être ancré.

### <a name="return-value"></a>Valeur de retour

TRUE si ce volet peut être ancré dans le volet d’ancrage spécifié ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est généralement appelée par l’infrastructure pour déterminer si un volet peut être ancré dans le volet d’ancrage spécifié. Pour déterminer que si le volet peut être ancré, la méthode prend la valeur du volet actuellement activé l’alignement d’ancrage.

Vous activez l’ancrage sur les différents côtés de la fenêtre frame en appelant [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).

##  <a name="canbetabbeddocument"></a>  CPane::CanBeTabbedDocument

Détermine si le volet peut être converti en un document à onglets.

```
virtual BOOL CanBeTabbedDocument() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet peut être converti en un document à onglets ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée et FALSE si vous souhaitez empêcher un volet de la conversion à un document à onglets. Un document à onglets s’afficheront pas dans le menu de la Position de la fenêtre.

##  <a name="converttotabbeddocument"></a>  CPane::ConvertToTabbedDocument

Convertit un volet ancrable à un document à onglets.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bActiveTabOnly*<br/>
[in] Non utilisé dans `CPane::ConvertToTabbedDocument`.

### <a name="remarks"></a>Notes

Uniquement les volets ancrables peuvent être convertis en documents avec onglet. Pour plus d’informations, consultez [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).

##  <a name="copystate"></a>  CPane::CopyState

Copie l’état d’un volet.

```
virtual void CopyState(CPane* pOrgBar);
```

### <a name="parameters"></a>Paramètres

*pOrgBar*<br/>
[in] Pointeur vers un volet.

### <a name="remarks"></a>Notes

Cette méthode copie l’état de *pOrgBar* dans le volet en cours.

##  <a name="create"></a>  CPane::Create

Crée une barre de contrôle et l’attache à la [CPane](../../mfc/reference/cpane-class.md) objet.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszClassName*<br/>
[in] Spécifie le nom de la classe de Windows.

*dwStyle*<br/>
[in] Spécifie les attributs de style de fenêtre. Pour plus d’informations, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[in] Spécifie la taille initiale et la position de la *pParentWnd* fenêtre, en coordonnées clientes.

[in] [out] *pParentWnd* spécifie la fenêtre parente de ce volet.

*nID*<br/>
[in] Spécifie l’ID du volet.

*dwControlBarStyle*<br/>
[in] Spécifie le style pour le volet. Pour plus d’informations, consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

[in] [out] *pContext* Spécifie le contexte de la création du volet.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été créé avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode crée un volet de Windows et l’attache à la `CPane` objet.

Si vous n’avez pas explicitement initialisé [CPane::m_recentDockInfo](#m_recentdockinfo) avant d’appeler `Create`, le paramètre *rect* sera utilisé comme le rectangle lorsque flottante ou le volet d’ancrage.

##  <a name="createdefaultminiframe"></a>  CPane::CreateDefaultMiniframe

Crée une fenêtre mini-frame pour un volet flottant.

```
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```

### <a name="parameters"></a>Paramètres

*rectInitial*<br/>
[in] Spécifie la taille initiale et la position, en coordonnées d’écran, de la fenêtre mini-frame à créer.

### <a name="return-value"></a>Valeur de retour

La fenêtre mini-frame nouvellement créé.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour créer une fenêtre mini-frame lorsqu’un volet est flottante. La fenêtre mini-frame peut être de type [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) ou de type [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md). Une fenêtre mini-frame de multiples est créée si le volet a le style AFX_CBRS_FLOAT_MULTI.

Les informations de classe runtime pour la fenêtre mini-frame sont stockées dans le `CPane::m_pMiniFrameRTC` membre. Vous pouvez utiliser une classe dérivée pour affecter à ce membre si vous décidez de créer des fenêtres mini-frame personnalisé.

##  <a name="createex"></a>  CPane::CreateEx

Crée une barre de contrôle et l’attache à la [CPane](../../mfc/reference/cpane-class.md) objet.

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszClassName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*dwStyleEx*<br/>
[in] Spécifie les attributs de style de fenêtre étendus. Pour plus d’informations, consultez [Styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

*lpszClassName*<br/>
[in] Spécifie le nom de la classe de Windows.

*dwStyle*<br/>
[in] Spécifie les attributs de style de fenêtre. Pour plus d’informations, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[in] Spécifie la taille initiale et la position de la *pParentWnd* fenêtre, en coordonnées clientes.

[in] [out] *pParentWnd* spécifie la fenêtre parente de ce volet.

*nID*<br/>
[in] Spécifie l’ID du volet.

*dwControlBarStyle*<br/>
[in] Spécifie le style pour le volet. Pour plus d’informations, consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

[in] [out] *pContext* Spécifie le contexte de créer pour le volet.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été créé avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode crée un volet de Windows et l’attache à la `CPane` objet.

Si vous n’avez pas explicitement initialisé [CPane::m_recentDockInfo](#m_recentdockinfo) avant d’appeler `CreateEx`, le paramètre *rect* sera utilisé comme le rectangle lorsque flottante ou le volet d’ancrage.

##  <a name="dockbymouse"></a>  CPane::DockByMouse

Ancre un volet à l’aide de la souris.

```
virtual BOOL DockByMouse(CBasePane* pDockBar);
```

### <a name="parameters"></a>Paramètres

*pDockBar*<br/>
[in] Spécifie le volet de base à laquelle ce volet d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été ancré avec succès ; Sinon, FALSE.

##  <a name="dockpane"></a>  CPane::DockPane

Ancre le volet flottant à un volet de base.

```
virtual BOOL DockPane(
    CBasePane* pDockBar,
    LPCRECT lpRect,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

[in] [out] *pDockBar* Spécifie le volet de base pour l’ancrer ce volet pour.

*lpRect*<br/>
[in] Spécifie le rectangle dans le volet de base où ce volet doit être ancré.

*dockMethod*<br/>
[in] Spécifie la méthode d’ancrage à utiliser. Les options disponibles sont les suivantes :

|Option|Description|
|------------|-----------------|
|DM_UNKNOWN|L’infrastructure utilise cette option lorsque la méthode d’ancrage est inconnue. Le volet ne stocke pas de sa dernière position flottante. Vous pouvez également utiliser cette option pour un volet d’ancrage par programmation lorsque vous n’êtes pas obligé de stocker sa position récente.|
|DM_MOUSE|Utilisé en interne.|
|DM_DBL_CLICK|Cette option est utilisée lorsque l’utilisateur double-clique sur la barre de redimensionnement. Le volet est repositionné à sa position d’ancrage plus récent. Si le volet est non ancré en double-cliquant dessus, le volet est repositionné à sa position flottante plus récente.|
|DM_SHOW|Cette option peut être utilisée pour le volet d’ancrage par programmation. Le volet stocke sa dernière position flottante.|
|DM_RECT|Le volet est ancré dans la région spécifiée par *lpRect*.|
|DM_STANDARD|Lorsque vous utilisez cette option, le framework Dessine le volet comme une trame de contour pendant son déplacement.|

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été ancré avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode ancre le volet vers le volet de base qui est spécifié par le *pDockBar* paramètre. Vous devez d’abord activer d’ancrage en appelant [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).

##  <a name="dockpanestandard"></a>  CPane::DockPaneStandard

Ancre un volet à l’aide de contour de la station d’accueil (standard).

```
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```

### <a name="parameters"></a>Paramètres

*bWasDocked*<br/>
[in] TRUE si le volet a été ancré avec succès ; Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne toujours la **cela** pointeur.

### <a name="remarks"></a>Notes

Cette méthode est utilisée uniquement pour les volets qui sont dérivés de la [CDockablePane, classe](../../mfc/reference/cdockablepane-class.md). Pour plus d’informations, consultez [CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard).

##  <a name="docktoframewindow"></a>  CPane::DockToFrameWindow

Ancre un volet ancrable à un frame.

```
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,
    LPCRECT lpRect = NULL,
    DWORD dwDockFlags = DT_DOCK_LAST,
    CBasePane* pRelativeBar = NULL,
    int nRelativeIndex = -1,
    BOOL bOuterEdge = FALSE);
```

### <a name="parameters"></a>Paramètres

*dwAlignment*<br/>
[in] Le côté du frame parent que vous souhaitez ancrer le volet à.

*lpRect*<br/>
[in] La taille spécifiée.

*dwDockFlags*<br/>
[in] Ignoré.

*pRelativeBar*<br/>
[in] Ignoré.

*nRelativeIndex*<br/>
[in] Ignoré.

*bOuterEdge*<br/>
[in] Si TRUE et il existe des autres volets ancrables situé sur le côté qui sont spécifiées par *dwAlignment*, le volet est ancré à l’extérieur les autres volets, plus proche sur le bord du frame parent. Si la valeur est FALSE, le volet est plus proche ancré au centre de la zone cliente.

### <a name="return-value"></a>Valeur de retour

FALSE si une barre de séparation ( [cpanedivider, classe](../../mfc/reference/cpanedivider-class.md)) ne peut pas être créé ; sinon, TRUE.

### <a name="remarks"></a>Notes

##  <a name="doesallowsiblingbars"></a>  CPane::DoesAllowSiblingBars

Indique si vous pouvez ancrer un autre volet à la même ligne où le volet actif est ancré.

```
virtual BOOL DoesAllowSiblingBars() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si ce volet permettre ancrer à un autre volet sur la même ligne en tant que telle ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Vous pouvez activer ou désactiver ce comportement en appelant [CPane::SetExclusiveRowMode](#setexclusiverowmode).

Par défaut, les barres d’outils ont désactivé le mode ligne exclusifs et la barre de menus a activé le mode ligne exclusifs.

##  <a name="floatpane"></a>  CPane::FloatPane

Flotte le volet.

```
virtual BOOL FloatPane(
    CRect rectFloat,
    AFX_DOCK_METHOD dockMethod = DM_UNKNOWN,
    bool bShow = true);
```

### <a name="parameters"></a>Paramètres

*rectFloat*<br/>
[in] Spécifie l’emplacement, en coordonnées d’écran, pour positionner le volet lorsqu’elle est flottante.

*dockMethod*<br/>
[in] Spécifie la méthode d’ancrage à utiliser lorsque le volet est flottante. Pour obtenir la liste des valeurs possibles, consultez [CPane::DockPane](#dockpane).

*bShow*<br/>
[in] TRUE pour afficher le volet lorsque flottantes ; Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été correctement flottantes ou si le volet ne peut pas être flottante car [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat) retourne la valeur FALSE ; sinon, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour détacher le volet à la position spécifiée par le *rectFloat* paramètre. Cette méthode crée automatiquement une fenêtre mini-frame parent du volet.

##  <a name="getavailableexpandsize"></a>  CPane::GetAvailableExpandSize

Retourne la quantité, en pixels, que le volet peut développer.

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Valeur de retour

Si le volet est ancré horizontalement, la valeur de retour est la largeur disponible ; Sinon, la valeur de retour est la hauteur disponible.

### <a name="remarks"></a>Notes

##  <a name="getavailablestretchsize"></a>  CPane::GetAvailableStretchSize

Retourne la quantité, en pixels, permettant de réduire le volet.

```
virtual int GetAvailableStretchSize() const;
```

### <a name="return-value"></a>Valeur de retour

La quantité, en pixels, permettant de réduire le volet. Si le volet est ancré horizontalement, ce montant est la largeur disponible ; Sinon, elle est la hauteur disponible.

### <a name="remarks"></a>Notes

La taille d’extension disponible est calculée en soustrayant la valeur minimale autorisée pour le volet ( [CPane::GetMinSize](#getminsize)) à partir de la taille actuelle ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect)).

##  <a name="getborders"></a>  CPane::GetBorders

Retourne la largeur des bordures du volet.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valeur de retour

Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui contient la largeur actuelle, en pixels, de chaque côté du volet. Par exemple, la valeur de la `left` membre de la `CRect` objet correspond à la largeur de la bordure gauche.

### <a name="remarks"></a>Notes

Pour définir la taille des bordures, appelez [CPane::SetBorders](#setborders).

##  <a name="getclienthotspot"></a>  CPane::GetClientHotSpot

Retourne le *réactive* pour le volet.

```
CPoint GetClientHotSpot() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le *réactive* est le point dans le volet de l’utilisateur sélectionne et qu’il conserve pour déplacer le volet. Une zone réactive est utilisée pour réaliser des animations fluides lorsque le volet est déplacé d’une position ancrée.

##  <a name="getdocksiterow"></a>  CPane::GetDockSiteRow

Retourne la ligne d’ancrage ( [cdockingpanesrow, classe](../../mfc/reference/cdockingpanesrow-class.md)) dans le volet est ancré.

```
CDockingPanesRow* GetDockSiteRow() const;
```

### <a name="return-value"></a>Valeur de retour

A `CDockingPanesRow`* qui pointe vers la ligne d’ancrage dans lequel le volet est ancré, ou NULL si le volet n’est pas ancré.

##  <a name="getexclusiverowmode"></a>  CPane::GetExclusiveRowMode

Détermine si le volet est en mode exclusif de ligne.

```
virtual BOOL GetExclusiveRowMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet est en mode de ligne exclusifs ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le mode de ligne exclusifs, consultez [CPane::SetExclusiveRowMode](#setexclusiverowmode).

##  <a name="gethotspot"></a>  CPane::GetHotSpot

Retourne la zone réactive qui est stockée dans un sous-jacent `CMFCDragFrameImpl` objet.

```
CPoint GetHotSpot() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le `CPane` classe contient un `CMFCDragFrameImpl` objet, `m_dragFrameImpl`, qui est chargé de dessiner le rectangle qui apparaît lorsque l’utilisateur déplace un volet dans le mode d’ancrage standard. La zone réactive est utilisée pour dessiner le rectangle par rapport à la position actuelle de la souris quand l’utilisateur déplace le volet.

##  <a name="getminsize"></a>  CPane::GetMinSize

Récupère la valeur minimale autorisée pour le volet.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*size*<br/>
[out] Un `CSize` objet qui est rempli avec la valeur minimale autorisée.

### <a name="remarks"></a>Notes

##  <a name="getpanename"></a>  CPane::GetPaneName

Récupère le titre du volet.

```
virtual void GetPaneName(CString& strName) const;
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[out] Un `CString` objet qui est rempli avec le nom de la légende.

### <a name="remarks"></a>Notes

Titre du volet s’affiche dans la zone de légende lorsque le volet est ancré ou flottant. Si le volet fait partie d’un groupe à onglets, le titre est affiché dans la zone d’onglet. Si le volet est en mode de masquage automatique, le titre est affiché sur un `CMFCAutoHideButton`.

##  <a name="getvirtualrect"></a>  CPane::GetVirtualRect

Récupère le *rectangle virtuel* du volet.

```
void GetVirtualRect(CRect& rectVirtual) const;
```

### <a name="parameters"></a>Paramètres

*rectVirtual*<br/>
[out] Un `CRect` objet qui est rempli avec le rectangle virtuel.

### <a name="remarks"></a>Notes

Lorsqu’un volet est déplacé, le framework stocke la position d’origine du volet dans un rectangle virtuel. Le framework peut utiliser le rectangle virtuel pour restaurer la position d’origine du volet.

N’appelez pas les méthodes qui sont liées aux rectangles virtuels, sauf si vous déplacez des volets par programmation.

##  <a name="ischangestate"></a>  CPane::IsChangeState

Comme le volet est déplacée, cette méthode analyse sa position par rapport à d’autres volets, ancrer les lignes et les fenêtres mini-frame et retourne la valeur AFX_CS_STATUS appropriée.

```
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,
    CBasePane** ppTargetBar) const;
```

### <a name="parameters"></a>Paramètres

*nOffset*<br/>
[in] Spécifie la sensibilité d’ancrage. Par exemple, un volet qui est déplacé dans *nOffset* pixels à partir d’une ligne d’ancrage seront ancrés.

*ppTargetBar*<br/>
[in] Lorsque la méthode est retournée, *ppTargetBar* contient soit un pointeur vers l’objet auquel le volet actif doit être ancré, ou NULL si aucun ancrage ne doit se produire.

### <a name="return-value"></a>Valeur de retour

Une des valeurs AFX_CS_STATUS suivantes :

|Value|Description|
|-----------|-----------------|
|CS_NOTHING|Le volet n’est pas près d’un site d’ancrage. Le framework n’ancre pas le volet.|
|CS_DOCK_IMMEDIATELY|Le volet se trouve sur un site d’ancrage et le style DT_IMMEDIATE est activé. Le framework ancre le volet immédiatement.|
|CS_DELAY_DOCK|Le volet se trouve sur un site d’ancrage est un autre volet d’ancrage ou sur un bord du frame principal. Le framework ancre le volet lorsque l’utilisateur relâche le déplacement.|
|CS_DELAY_DOCK_TO_TAB|Le volet se trouve sur un site d’ancrage qui provoque le volet ancré dans une fenêtre à onglets. Cela se produit lorsque le volet est sur la légende d’un autre volet d’ancrage ou sur la zone d’onglet d’un volet à onglets. Le framework ancre le volet lorsque l’utilisateur relâche le déplacement.|

##  <a name="isdragmode"></a>  CPane::IsDragMode

Spécifie si le volet est déplacé.

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet est déplacé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="isinfloatingmultipaneframewnd"></a>  CPane::IsInFloatingMultiPaneFrameWnd

Spécifie si le volet est dans une fenêtre frame de plusieurs volets ( [cmultipaneframewnd, classe](../../mfc/reference/cmultipaneframewnd-class.md)).

```
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet se trouve dans une fenêtre frame de plusieurs volets ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Uniquement les volets ancrables peuvent flotter dans une fenêtre frame de plusieurs volets. Par conséquent, `CPane::IsInFloatingMultiPaneFrameWnd` retourne toujours FALSE.

##  <a name="isleftof"></a>  CPane::IsLeftOf

Détermine si le volet est laissé de (ou plus) du rectangle spécifié.

```
bool IsLeftOf(
    CRect rect,
    bool bWindowRect = true) const;
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[in] Un `CRect` objet qui est utilisé pour la comparaison.

*bWindowRect*<br/>
[in] Si la valeur est TRUE, *rect* est supposée pour contenir les coordonnées d’écran ; si la valeur est FALSE, *rect* est supposée pour contenir les coordonnées clientes.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Si le volet est ancré horizontalement, cette méthode vérifie si son emplacement est laissé de *rect*. Sinon, cette méthode vérifie si l’emplacement ci-dessus *rect*.

##  <a name="isresizable"></a>  CPane::IsResizable

Spécifie si le volet est redimensionnable.

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet est redimensionnable ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Base `CPane` objets ne sont pas redimensionnables.

Le Gestionnaire d’ancrage utilise l’indicateur redimensionnable pour déterminer la présentation du volet. Volets non redimensionnables se trouvent toujours aux bords externes du frame parent.

Volets non redimensionnables ne peuvent pas résider dans la station d’accueil de conteneurs.

##  <a name="istabbed"></a>  CPane::IsTabbed

Détermine si le volet a été inséré dans le contrôle onglet d’une fenêtre à onglets.

```
virtual BOOL IsTabbed() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet est avec onglets ; Sinon, FALSE.

### <a name="remarks"></a>Notes

L’état à onglets est traitée séparément à partir de flottante, ancré et masquer les États.

##  <a name="loadstate"></a>  CPane::LoadState

Charge l’état du volet à partir du Registre.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Nom du profil.

*nIndex*<br/>
[in] Index de profil.

*uiID*<br/>
[in] ID de volet.

### <a name="return-value"></a>Valeur de retour

TRUE si l’état du volet a été chargé avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour charger l’état du volet à partir du Registre. Substituer dans une classe dérivée pour charger des informations supplémentaires qui est enregistrée par [CPane::SaveState](#savestate).

Lorsque vous substituez cette méthode, également appeler la méthode de base et renvoie FALSE si la méthode de base retourne FALSE.

##  <a name="m_bhandleminsize"></a>  CPane::m_bHandleMinSize

Permet une gestion cohérente des tailles de minimale du volet.

```
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;
```

### <a name="remarks"></a>Notes

Si un ou plusieurs volets d’ancrage dans votre application remplacent `GetMinSize`, ou si votre application appelle `SetMinSize`, vous souhaiterez définissez ce membre statique sur TRUE pour permettre au framework de façon cohérente gérer comment les volets sont dimensionnés.

Si cette valeur est définie sur TRUE, dont la taille doit être inférieure à leur taille minimale de tous les volets sont tronqués, ne pas étiré. Étant donné que l’infrastructure utilise des zones de fenêtre à des fins volet dimensionnement, ne modifiez pas la taille de la région de fenêtre pour les volets d’ancrage si cette valeur est définie sur TRUE.

##  <a name="m_recentdockinfo"></a>  CPane::m_recentDockInfo

Contient des informations récentes sur la station d’accueil.

```
CRecentDockSiteInfo m_recentDockInfo;
```

### <a name="remarks"></a>Notes

Le framework stocke les informations d’état plus récente d’ancrage du volet dans ce membre.

##  <a name="movebyalignment"></a>  CPane::MoveByAlignment

Déplace le volet et le rectangle virtuel selon la valeur spécifiée.

```
BOOL MoveByAlignment(
    DWORD dwAlignment,
    int nOffset);
```

### <a name="parameters"></a>Paramètres

*dwAlignment*<br/>
[in] Spécifie l’alignement du volet.

*nOffset*<br/>
[in] La quantité, en pixels, de laquelle déplacer le volet et le rectangle virtuel.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

*dwAlignment* peut être une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|CBRS_ALIGN_TOP|Active le volet pour être ancré en haut de la zone cliente d’une fenêtre frame.|
|CBRS_ALIGN_BOTTOM|Active le volet pour être ancré en bas de la zone cliente d’une fenêtre frame.|
|CBRS_ALIGN_LEFT|Active le volet pour être ancré sur le côté gauche de la zone cliente d’une fenêtre frame.|
|CBRS_ALIGN_RIGHT|Active le volet pour être ancré à droite de la zone cliente d’une fenêtre frame.|
|CBRS_ALIGN_ANY|Active le volet pour être ancré à n’importe quel côté de la zone cliente d’une fenêtre frame.|

Si *dwAlignment* contient l’indicateur CBRS_ALIGN_LEFT ou CBRS_ALIGN_RIGHT, le volet et le rectangle virtuel sont déplacés horizontalement ; sinon, si *dwAlignment* contient le CBRS_ALIGN_TOP ou CBRS_ALIGN Indicateur de moins _bons, le volet et le rectangle virtuel sont déplacés verticalement.

##  <a name="movepane"></a>  CPane::MovePane

Déplace le volet vers le rectangle spécifié.

```
virtual CSize MovePane(
    CRect rectNew,
    BOOL bForceMove,
    HDWP& hdwp);
```

### <a name="parameters"></a>Paramètres

*rectNew*<br/>
[in] Spécifie le nouveau rectangle pour le volet.

*bForceMove*<br/>
[in] Si la valeur est TRUE, cette méthode ignore la taille minimale autorisée du volet ( [CPane::GetMinSize](#getminsize)) ; sinon, le volet est ajusté, si nécessaire, pour vous assurer qu’il est d’au moins la valeur minimale autorisée.

*hdwp*<br/>
[in] Non utilisé.

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet qui contient les différences de largeur et hauteur entre les rectangles de nouvelles et anciennes (rectangle ancien - *rectNew*).

### <a name="remarks"></a>Notes

Cette méthode est utilisée uniquement pour les volets ancrables.

##  <a name="onafterchangeparent"></a>  CPane::OnAfterChangeParent

Appelé par le framework lorsque le parent d’un volet a changé.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Paramètres

[in] [out] *pWndOldParent* fenêtre parente de la précédente du volet.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le framework lorsque le parent d’un volet a été modifiée en raison d’une opération d’ancrage ou flottante.

##  <a name="onafterdock"></a>  CPane::OnAfterDock

Appelé par le framework lorsqu’un volet a été verrouillée.

```
virtual void OnAfterDock(
    CBasePane* pBar,
    LPCRECT lpRect,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Ce paramètre n’est pas utilisé.

*lpRect*<br/>
[in] Ce paramètre n’est pas utilisé.

*dockMethod*<br/>
[in] Ce paramètre n’est pas utilisé.

##  <a name="onafterfloat"></a>  CPane::OnAfterFloat

Appelé par le framework après qu’un volet est rendu flottant.

```
virtual void OnAfterFloat();
```

### <a name="remarks"></a>Notes

Vous pouvez substituer cette méthode dans une classe dérivée si vous souhaitez effectuer tout traitement une fois un volet est rendu flottant.

##  <a name="onbeforechangeparent"></a>  CPane::OnBeforeChangeParent

Appelé par le framework lorsque le parent du volet est va être modifiée.

```
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Paramètres

[in] [out] *pWndNewParent* spécifie la nouvelle fenêtre parente.

*bDelay*<br/>
[in] TRUE pour différer l’ajustement global de mise en page d’accueil ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le framework lorsque le parent du volet est va être modifiée, car le volet est ancré ou flottantes.

Par défaut, le volet n’est plus inscrit auprès du volet d’ancrage en appelant `CDockSite::RemovePane`.

##  <a name="onbeforedock"></a>  CPane::OnBeforeDock

Appelé par le framework lorsque le volet est sur le point d’ancrage.

```
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,
    LPCRECT lpRect,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

[in] [out] *ppDockBar* Spécifie le volet d’accueil pour ce volet.

*lpRect*<br/>
[in] Spécifie le rectangle d’ancrage.

*dockMethod*<br/>
[in] Spécifie la méthode d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet peut être ancré. Si la fonction retourne FALSE, l’opération d’ancrage va être annulée.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le framework lorsqu’un volet est sur le point d’être ancrée. Vous pouvez substituer cette méthode dans une classe dérivée si vous souhaitez effectuer tout traitement avant un volet est ancré enfin.

##  <a name="onbeforefloat"></a>  CPane::OnBeforeFloat

Appelé par le framework lorsqu’un volet est sur le type float.

```
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

*rectFloat*<br/>
[in] Spécifie la position et la taille du volet lorsqu’il est dans un état flottant.

*dockMethod*<br/>
[in] Spécifie la méthode d’ancrage du volet.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet peut flotter ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le framework lorsqu’un volet est sur le type float. Vous pouvez remplacer cette méthode dans une classe dérivée si vous souhaitez effectuer tout traitement avant le volet enfin flotte.

##  <a name="onpressclosebutton"></a>  CPane::OnPressCloseButton

Appelé par l’infrastructure lorsque l’utilisateur appuie sur le bouton Fermer sur la légende pour le volet.

```
virtual void OnPressCloseButton();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand un utilisateur appuie sur le **fermer** bouton dans légende du volet. Pour recevoir des notifications sur les **fermer** événement, vous pouvez substituer cette méthode dans une classe dérivée.

##  <a name="onshowcontrolbarmenu"></a>  CPane::OnShowControlBarMenu

Appelé par l'infrastructure quand un menu de volet spécial va être affiché.

```
virtual BOOL OnShowControlBarMenu(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Spécifie l’emplacement du menu.

### <a name="return-value"></a>Valeur de retour

TRUE si le menu peut être affiché ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Le menu contient plusieurs éléments qui vous permettent de spécifier le comportement du volet, à savoir : **flottante**, **ancrage**, **masquage automatique**, et **masquer**. Vous pouvez activer ce menu pour tous les volets en appelant [CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu).

##  <a name="recalclayout"></a>  CPane::RecalcLayout

Recalcule les informations de disposition pour le volet.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

Si le volet est ancré, cette méthode met à jour le rectangle virtuel pour le volet en définissant sa taille à la taille actuelle du volet.

Si le volet est flottant, cette méthode avertit le mini-frame de parent pour ajuster la taille du volet pour la taille de la mini-frame. Le framework garantit que le mini-frame est au moins la valeur minimale autorisée pour le volet ( [CPane::GetMinSize](#getminsize)) et redimensionne le mini-frame si nécessaire.

##  <a name="savestate"></a>  CPane::SaveState

Enregistre l’état du volet dans le Registre.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Nom du profil.

*nIndex*<br/>
[in] Index de profil.

*uiID*<br/>
[in] ID de volet.

### <a name="return-value"></a>Valeur de retour

TRUE si l’état a été enregistré avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’il enregistre l’état du volet dans le Registre. Substituer `SaveState` dans une classe dérivée pour stocker des informations supplémentaires.

Lorsque vous substituez cette méthode, également appeler la méthode de base et renvoie FALSE si la méthode de base retourne FALSE.

##  <a name="setactiveingroup"></a>  CPane::SetActiveInGroup

Marque un volet comme actif.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Paramètres

*bActive*<br/>
[in] Une valeur Booléenne qui spécifie si le volet est marqué comme active.

### <a name="remarks"></a>Notes

Lorsqu’un volet ancrable est affiché ou qu’un bouton Masquer automatiquement est choisi, le volet de masquage automatique correspondant est marqué comme actif.

L’apparence d’un bouton de masquage automatique qui est associé au volet est basée sur deux facteurs. Si le volet est actif et le `static BOOL CMFCAutoHideButton::m_bOverlappingTabs` a la valeur TRUE, le bouton de masquage automatique comme une icône et une étiquette s’affiche framework. Pour un volet inactif, l’infrastructure affiche uniquement l’icône de masquage automatique.

Si `CMFCAutoHideButton::m_bOverlappingTabs` a la valeur FALSE, ou si le volet ne se trouve pas dans un groupe, l’infrastructure affiche le bouton Masquer automatiquement associé en tant qu’une icône et une étiquette.

##  <a name="setborders"></a>  CPane::SetBorders

Définit les valeurs de la bordure du volet.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*cxLeft*<br/>
[in] Spécifie la largeur, en pixels, de la bordure gauche du volet.

*cyTop*<br/>
[in] Spécifie la largeur, en pixels, de la bordure supérieure du volet.

*cxRight*<br/>
[in] Spécifie la largeur, en pixels, de la bordure droite du volet.

*cyBottom*<br/>
[in] Spécifie la largeur, en pixels, de la bordure inférieure du volet.

*lpRect*<br/>
[in] Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui contient la largeur, en pixels, de chaque bordure du volet.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir les tailles de bordures du volet.

##  <a name="setclienthotspot"></a>  CPane::SetClientHotSpot

Définit le *réactive* pour le volet.

```
void SetClientHotSpot(const CPoint& ptNew);
```

### <a name="parameters"></a>Paramètres

*ptNew*<br/>
[in] Un `CPoint` objet qui spécifie la nouvelle zone réactive.

### <a name="remarks"></a>Notes

Le *réactive* est le point dans le volet de l’utilisateur sélectionne et qu’il conserve pour déplacer le volet. Une zone réactive est utilisée pour réaliser des animations fluides lorsque le volet est déplacé à partir d’une position ancrée.

##  <a name="setdockstate"></a>  CPane::SetDockState

Restaurations d’ancrage des informations d’état pour le volet.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Paramètres

*pDockManager*<br/>
[in] Pointeur vers le Gestionnaire d’ancrage pour la fenêtre frame principale.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour restaurer les informations d’état d’ancrage récentes pour le volet. Stocke les informations d’état d’ancrage récentes dans un volet [CPane::m_recentDockInfo](#m_recentdockinfo). Pour plus d’informations, consultez le [crecentdocksiteinfo, classe](../../mfc/reference/crecentdocksiteinfo-class.md).

Vous pouvez également appeler cette méthode pour définir l’état d’ancrage lorsque vous chargez les informations du volet d’une source externe.

##  <a name="setexclusiverowmode"></a>  CPane::SetExclusiveRowMode

Active ou désactive le mode de ligne exclusifs.

```
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```

### <a name="parameters"></a>Paramètres

*bExclusive*<br/>
[in] TRUE pour activer le mode de ligne exclusifs ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour activer ou désactiver le mode de ligne exclusifs. Lorsqu’un volet est en mode exclusif de ligne, il ne peut pas partager la même ligne avec les autres barres d’outils.

Par défaut, toutes les barres d’outils ont désactivé le mode ligne exclusifs et la barre de menus a activé le mode ligne exclusifs.

##  <a name="setminsize"></a>  CPane::SetMinSize

Définit la valeur minimale autorisée pour le volet.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
[in] Un `CSize` objet qui contient la valeur minimale autorisée pour le volet.

### <a name="remarks"></a>Notes

##  <a name="setvirtualrect"></a>  CPane::SetVirtualRect

Définit le *rectangle virtuel* du volet.

```
void SetVirtualRect(
    const CRect& rect,
    BOOL bMapToParent = TRUE);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[in] Un `CRect` objet qui spécifie le rectangle virtuel à définir.

*bMapToParent*<br/>
[in] Spécifiez la valeur TRUE si *rect* contient les points par rapport à la fenêtre parente.

### <a name="remarks"></a>Notes

Un *rectangle virtuel* stocke la position d’origine d’un volet lorsqu’elles sont déplacées. Le framework peut utiliser le rectangle virtuel pour restaurer la position d’origine.

N’appelez pas les méthodes qui sont liées aux rectangles virtuels, sauf si vous déplacez des volets par programmation.

##  <a name="setminiframertc"></a>  CPane::SetMiniFrameRTC

Définit les informations de classe runtime pour la fenêtre mini-frame par défaut.

```
void SetMiniFrameRTC(CRuntimeClass* pClass);
```

### <a name="parameters"></a>Paramètres

[in] [out] *pClass* spécifie les informations de classe runtime pour la fenêtre mini-frame.

### <a name="remarks"></a>Notes

Lorsqu’un volet est flottantes, elle est placée un [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) fenêtre (mini-frame). Vous pouvez fournir un personnalisé `CPaneFrameWnd`-classe dérivée qui sera utilisée lorsque [CPane::CreateDefaultMiniframe](#createdefaultminiframe) est appelée.

##  <a name="stretchpanedeferwndpos"></a>  CPane::StretchPaneDeferWndPos

Étire le volet verticalement ou horizontalement en fonction de style d’ancrage.

```
virtual int StretchPaneDeferWndPos(
    int nStretchSize,
    HDWP& hdwp);
```

### <a name="parameters"></a>Paramètres

*nStretchSize*<br/>
[in] La quantité, en pixels, à étendre le volet. Utilisez une valeur négative pour réduire le volet.

*hdwp*<br/>
[in] Non utilisé.

### <a name="return-value"></a>Valeur de retour

La quantité réelle, en pixels, que le volet étendue.

### <a name="remarks"></a>Notes

Si nécessaire, cette méthode modifie les *nStretchSize* pour vous assurer que le volet ne dépasse pas les limites de taille. Ces limites sont obtenus en appelant [CPane::GetAvailableStretchSize](#getavailablestretchsize) et [CPane::GetAvailableExpandSize](#getavailableexpandsize).

##  <a name="toggleautohide"></a>  CPane::ToggleAutoHide

Mode de masquage automatique de bascules.

```
virtual void ToggleAutoHide();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour activer/désactiver le mode de masquage automatique. Un volet doit être ancré dans une fenêtre frame principale afin d’être basculer en mode de masquage automatique.

##  <a name="undockpane"></a>  CPane::UndockPane

Supprime le volet à partir du site d’ancrage, le curseur de la valeur par défaut ou la fenêtre mini-frame dans lequel il est actuellement ancré.

```
virtual void UndockPane(BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Paramètres

*bDelay*<br/>
[in] Si la valeur est FALSE, le framework appelle [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout) pour ajuster la disposition d’ancrage.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour annuler l’ancrage par programmation un volet.

##  <a name="updatevirtualrect"></a>  CPane::UpdateVirtualRect

Met à jour le rectangle virtuel.

```
void UpdateVirtualRect();
void UpdateVirtualRect(CPoint ptOffset);
  void UpdateVirtualRect(CSize sizeNew);
```

### <a name="parameters"></a>Paramètres

*ptOffset*<br/>
[in] Un `CPoint` objet qui spécifie un offset selon lequel décaler le volet.

*hachagetaille, nouvelle*<br/>
[in] Un `CSize` objet qui spécifie une nouvelle taille pour le volet.

### <a name="remarks"></a>Notes

La première surcharge définit le rectangle virtuel à l’aide de la position actuelle et la taille du volet.

La deuxième surcharge décale le rectangle virtuel la quantité spécifiée par *ptOffset*.

La troisième surcharge définit le rectangle virtuel à l’aide de la position actuelle du volet et la taille spécifiée par *hachagetaille, nouvelle*.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane, classe](../../mfc/reference/cbasepane-class.md)
