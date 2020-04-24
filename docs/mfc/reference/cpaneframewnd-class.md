---
title: CPaneFrameWnd, classe
ms.date: 11/04/2016
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
ms.openlocfilehash: 76f7c5c2c21f0e823545db3669ce454c8172317c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753612"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd, classe

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

Implémente une fenêtre mini-frame qui contient un volet. Le volet remplit la zone cliente de la fenêtre.

## <a name="syntax"></a>Syntaxe

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|Ajoute un volet.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Ajoute ou supprime un volet de la liste globale.|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Ajuste la disposition de la fenêtre mini-frame.|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Calcule la taille des bordures d'une fenêtre mini-frame.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcule le rectangle attendu d'une fenêtre ancrée.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Détermine si le volet actif peut être ancré à un autre volet ou à une fenêtre frame.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Détermine si la fenêtre mini-frame peut être ancrée à un volet.|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Convertit le volet en document à onglets.|
|[CPaneFrameWnd::Create](#create)|Crée une fenêtre mini-frame et l'attache à l'objet `CPaneFrameWnd`.|
|[CPaneFrameWnd::CreateEx](#createex)|Crée une fenêtre mini-frame et l'attache à l'objet `CPaneFrameWnd`.|
|[CPaneFrameWnd::DockPane](#dockpane)|Ancre le volet.|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Recherche un volet à partir de l'ID de contrôle spécifié dans la liste globale des volets flottants.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Recherche la fenêtre mini-frame contenant un point fourni par l'utilisateur.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Retourne la hauteur de la légende de fenêtre mini-frame.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Calcule le rectangle englobant d'une légende de fenêtre mini-frame.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Retourne le texte de légende.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Retourne le mode d'ancrage.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Retourne le premier volet visible contenu dans une fenêtre mini-frame.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|Retourne un volet contenu dans la fenêtre mini-frame.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Retourne le nombre de volets contenus dans une fenêtre mini-frame.|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Retourne le nombre de volets visibles contenus dans une fenêtre mini-frame.|
|[CPaneFrameWnd::HitTest](#hittest)|Détermine la partie d'une fenêtre mini-frame qui se trouve à un point donné.|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Détermine si une fenêtre mini-frame doit être masquée.|
|[CPaneFrameWnd::IsRollUp](#isrollup)|Détermine si une fenêtre mini-frame doit être affichée.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Arrête le minuteur d'ancrage.|
|[CPaneFrameWnd::LoadState](#loadstate)|Charge l'état du volet à partir du Registre.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Détermine si l'ancrage est possible.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ancre la fenêtre mini-frame à sa dernière position.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Arrête le minuteur d'affichage.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Déplace la fenêtre mini-frame selon un décalage spécifié.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Ajuste la disposition d'un volet contenu.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Définit le minuteur d'affichage.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Appelé par l'infrastructure quand un volet de la fenêtre mini-frame est masqué ou affiché.|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Retourne un volet s'il contient un point fourni par l'utilisateur à l'intérieur d'une fenêtre mini-frame.|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage)|
|[CPaneFrameWnd::RedrawAll](#redrawall)|Redessine toutes les fenêtres mini-frame.|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Appelé par l'infrastructure pour supprimer les volets non valides.|
|[CPaneFrameWnd::RemovePane](#removepane)|Supprime un volet de la fenêtre mini-frame.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|Remplace un volet par un autre.|
|[CPaneFrameWnd::SaveState](#savestate)|Enregistre l'état du volet dans le Registre.|
|`CPaneFrameWnd::Serialize`|Lit ou écrit cet objet dans une archive.|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Définit les boutons de légende.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Définit le minuteur d'ancrage.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|Définit l'état d'ancrage.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Appelé par l'infrastructure pour définir l'état de pré-ancrage.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Ajuste une fenêtre mini-frame de sorte qu'elle ait une taille équivalente à celle d'un volet contenu.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Détache un menu.|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Détermine si une fenêtre mini-frame doit être masquée ou affichée.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Dessine les bordures d'une fenêtre mini-frame.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Précise s’il faut enregistrer la classe de fenêtre avec le style de classe CS_SAVEBITS.|

## <a name="remarks"></a>Notes

L'infrastructure crée automatiquement un objet `CPaneFrameWnd` quand un volet passe de l'état ancré à l'état flottant.

Vous pouvez faire glisser une fenêtre mini-frame avec son contenu visible (ancrage immédiat) ou en utilisant un rectangle de glissement (ancrage standard). Le mode d'ancrage du volet conteneur du mini-frame détermine le comportement de glissement du mini-frame. Pour plus d’informations, voir [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Une fenêtre mini-frame présente des boutons sur la légende en fonction du style du volet contenu. Si la vitre peut être fermée ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), elle affiche un bouton Close. Si la vitre a le style AFX_CBRS_AUTO_ROLLUP, elle affiche une épingle.

Si vous faites dériver une classe de `CPaneFrameWnd`, vous devez indiquer à l'infrastructure comment la créer. Soit créez la classe en dominant [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), ou définissez le `CPane::m_pMiniFrameRTC` membre de sorte qu’il indique les informations de classe runtime pour votre classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête:** afxPaneFrameWnd.h

## <a name="cpaneframewndaddpane"></a><a name="addpane"></a>CPaneFrameWnd::AddPane

Ajoute un volet.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] La vitre à ajouter.

## <a name="cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList

Ajoute ou supprime un volet de la liste globale.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] La vitre pour ajouter ou enlever.

*Badd*<br/>
[dans] Si non-zéro, ajouter la vitre. Si 0, retirez la vitre.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode a été couronnée de succès; sinon 0.

## <a name="cpaneframewndadjustlayout"></a><a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout

Ajuste la disposition de la fenêtre mini-frame.

```
virtual void AdjustLayout();
```

## <a name="cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Notes

## <a name="cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize

Calcule la taille des bordures pour une fenêtre de miniframe.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Paramètres

*rectBorderSize*<br/>
[out] Contient la taille, en pixels, de la bordure de la fenêtre miniframe.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pour calculer la taille de la bordure d’une fenêtre de miniframe. La taille retournée dépend si une fenêtre miniframe contient une barre d’outils ou un [CDockablePane](../../mfc/reference/cdockablepane-class.md).

## <a name="cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect

Calcule le rectangle attendu d'une fenêtre ancrée.

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Paramètres

*pWndToDock*<br/>
[dans] Un pointeur à la fenêtre pour accoster.

*ptMouse (en)*<br/>
[dans] L’emplacement de la souris.

*rectResult*<br/>
[out] Le rectangle calculé.

*bDrawTab (en anglais seulement)*<br/>
[out] Si VRAI, dessinez un onglet. Si FALSE, ne pas dessiner un onglet.

*ppTargetBar*<br/>
[out] Un pointeur à la vitre cible.

### <a name="remarks"></a>Notes

Cette méthode calcule le rectangle qu’une fenêtre occuperait si un utilisateur traînait la fenêtre au point spécifié par *ptMouse* et l’a amarré là.

## <a name="cpaneframewndcanbeattached"></a><a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached

Détermine si le volet actif peut être ancré à un autre volet ou à une fenêtre frame.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre peut être amarrée à une autre vitre ou fenêtre de cadre; autrement FALSE.

## <a name="cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane

Détermine si la fenêtre mini-frame peut être ancrée à un volet.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Paramètres

*pDockingBar (en)*<br/>
[dans] Une vitre.

### <a name="return-value"></a>Valeur de retour

Nonzero si le mini-cadre peut être amarré à *pDockingBar*; sinon 0.

## <a name="cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Notes

## <a name="cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument

Convertit le volet en document à onglets.

```
virtual void ConvertToTabbedDocument();
```

## <a name="cpaneframewndcreate"></a><a name="create"></a>CPaneFrameWnd::Créer

Crée une fenêtre de miniframe et la fixe à l’objet [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszWindowName (en)*<br/>
[dans] Spécifie le texte à afficher sur la fenêtre du miniframe.

*dwStyle (en)*<br/>
[dans] Spécifie le style de fenêtre. Pour plus d’informations, voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[dans] Précise la taille et la position initiales de la fenêtre de miniframe.

*pParentWnd*<br/>
[dans, dehors] Spécifie le cadre parent de la fenêtre miniframe. Cette valeur ne doit pas être NULL.

*pContext*<br/>
[dans, dehors] Spécifie le contexte défini par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre a été créée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Une fenêtre miniframe est créée en deux étapes. Tout d’abord, `CPaneFrameWnd` le cadre crée un objet. Deuxièmement, `Create` il appelle à créer la fenêtre de `CPaneFrameWnd` miniframe Windows et l’attacher à l’objet.

## <a name="cpaneframewndcreateex"></a><a name="createex"></a>CPaneFrameWnd::CreateEx

Crée une fenêtre de miniframe et la fixe à l’objet [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Paramètres

*dwStyleEx*<br/>
[dans] Spécifie le style de fenêtre étendue. Pour plus d’informations, voir [Extended Window Styles](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName (en)*<br/>
[dans] Spécifie le texte à afficher sur la fenêtre du miniframe.

*dwStyle (en)*<br/>
[dans] Spécifie le style de fenêtre. Pour plus d’informations, voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[dans] Précise la taille et la position initiales de la fenêtre de miniframe.

*pParentWnd*<br/>
[dans, dehors] Spécifie le cadre parent de la fenêtre miniframe. Cette valeur ne doit pas être NULL.

*pContext*<br/>
[dans, dehors] Spécifie le contexte défini par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre a été créée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Une fenêtre miniframe est créée en deux étapes. Tout d’abord, `CPaneFrameWnd` le cadre crée un objet. Deuxièmement, `Create` il appelle à créer la fenêtre de `CPaneFrameWnd` miniframe Windows et l’attacher à l’objet.

## <a name="cpaneframewnddockpane"></a><a name="dockpane"></a>CPaneFrameWnd::DockPane

Ancre le volet.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Paramètres

*bWasDocked*<br/>
[out] VRAI si la vitre était déjà amarré; autrement FALSE.

### <a name="return-value"></a>Valeur de retour

Si l’opération a `CDockablePane` été couronnée de succès, la vitre a été amarré à; autrement NULL.

## <a name="cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID

Recherche un volet à partir de l'ID de contrôle spécifié dans la liste globale des volets flottants.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] Représente l’ID de contrôle de la vitre à trouver.

### <a name="return-value"></a>Valeur de retour

La vitre avec l’ID de contrôle spécifié; autrement, NULL, si aucun volet n’a l’ID de contrôle spécifié.

## <a name="cpaneframewndframefrompoint"></a><a name="framefrompoint"></a>CPaneFrameWnd::FrameDePoint

Trouve la fenêtre mini-cadre qui contient le point spécifié.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
[dans] Le point, dans les coordonnées de l’écran.

*nSensibilité*<br/>
[dans] Augmentez la zone de recherche de la fenêtre mini-cadre par cette taille. Une fenêtre à mini-cadre répond aux critères de recherche si le point donné tombe dans la zone accrue.

*pFrameToExclude*<br/>
[dans] Spécifie une fenêtre de mini-cadre à exclure de la recherche.

*bFloatMultiOnly*<br/>
[dans] Si VRAI, ne recherchez que des fenêtres à mini-cadre qui ont le style CBRS_FLOAT_MULTI. Si FALSE, recherchez toutes les fenêtres à mini-cadre.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre mini-cadre qui contient *pt;* autrement NULL.

## <a name="cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight

Retourne la hauteur de la légende de fenêtre mini-frame.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, de la fenêtre mini-cadre.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer la hauteur d’une fenêtre à mini-cadre. Par défaut, la hauteur est réglée pour SM_CYSMCAPTION. Pour plus d’informations, voir [GetSystemMetrics Function](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

## <a name="cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect

Calcule le rectangle englobant d'une légende de fenêtre mini-frame.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Paramètres

*rectCaption*<br/>
[out] Contient la taille et la position de la légende de fenêtre mini-cadre, dans les coordonnées de l’écran.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pour calculer le rectangle de délimitation d’une légende de fenêtre mini-cadre.

## <a name="cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText

Retourne le texte de légende.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Valeur de retour

Le texte de légende de la fenêtre mini-cadre.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre lorsqu’elle affiche le texte de légende.

## <a name="cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode

Retourne le mode d'ancrage.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Valeur de retour

Le mode d’amarrage. L’une des valeurs suivantes :

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

## <a name="cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane

Retourne le premier volet visible contenu dans une fenêtre mini-frame.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Valeur de retour

Le premier volet dans la fenêtre mini-cadre, ou NULL si la fenêtre mini-cadre ne contient pas de vitres.

## <a name="cpaneframewndgethotpoint"></a><a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetpane"></a><a name="getpane"></a>CPaneFrameWnd::GetPane

Retourne un volet contenu dans la fenêtre mini-frame.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Valeur de retour

La vitre contenue dans le mini-cadre, ou NULL si la fenêtre mini-cadre ne contient pas de vitres.

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetpanecount"></a><a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount

Retourne le nombre de volets contenus dans une fenêtre mini-frame.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de vitres dans la fenêtre mini-cadre. Cette valeur peut être zéro.

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetparent"></a><a name="getparent"></a>CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetpinstate"></a><a name="getpinstate"></a>CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount

Retourne le nombre de volets visibles contenus dans une fenêtre mini-frame.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de vitres visibles.

### <a name="remarks"></a>Notes

## <a name="cpaneframewndhittest"></a><a name="hittest"></a>CPaneFrameWnd::HitTest

Détermine la partie d'une fenêtre mini-frame qui se trouve à un point donné.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
[dans] Le point à tester.

*bDetectCaption (en)*<br/>
[dans] Si VRAI, vérifiez le point par rapport à la légende. Si FALSE, ignorez la légende.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|HTNOWHERE|Le point est à l’extérieur de la fenêtre mini-cadre.|
|HTCLIENT (EN)|Le point est dans la zone client.|
|HTCAPTION (EN)|Le point est sur la légende.|
|HTTOP|Le point est au sommet.|
|HTTOPLEFT (HTTOPLEFT)|Le point est en haut à gauche.|
|HTTOPRIGHT (EN)|Le point est en haut à droite.|
|HTLEFT (HTLEFT)|Le point est à gauche.|
|HTRIGHT (HTRIGHT)|Le point est à droite.|
|HTBOTTOM (HTBOTTOM)|Le point est au fond.|
|HTBOTTOMLEFT|Le point est en bas à gauche.|
|HTBOTTOMRIGHT (HTBOTTOMRIGHT)|Le point est en bas à droite.|

## <a name="cpaneframewndiscaptured"></a><a name="iscaptured"></a>CPaneFrameWnd::IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndisdelayshow"></a><a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cpaneframewndisrolldown"></a><a name="isrolldown"></a>CPaneFrameWnd::IsRollDown

Détermine si une fenêtre mini-frame doit être masquée.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre mini-cadre doit être roulée; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pour déterminer si une fenêtre mini-cadre doit être roulée. La fonction de rollup/rolldown est activée pour une mini-fenêtre à monture si elle contient au moins un volet qui a le drapeau AFX_CBRS_AUTO_ROLLUP. Ce drapeau est défini lorsqu’une vitre est créée. Pour plus d’informations, voir [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Par défaut, le cadre vérifie si le pointeur de la souris est à l’intérieur du rectangle de délimitation de la fenêtre à mini-cadre pour déterminer si la fenêtre doit être roulée vers le bas. Vous pouvez remplacer ce comportement dans une classe dérivée.

## <a name="cpaneframewndisrollup"></a><a name="isrollup"></a>CPaneFrameWnd::IsRollUp

Détermine si une fenêtre mini-frame doit être affichée.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre mini-cadre doit être enroulée; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pour déterminer si une fenêtre mini-cadre doit être enroulée. La fonction de rollup/rolldown est activée pour une mini-fenêtre à monture si elle contient au moins un volet qui a le drapeau AFX_CBRS_AUTO_ROLLUP. Ce drapeau est défini lorsqu’une vitre est créée. Pour plus d’informations, voir [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Par défaut, le cadre vérifie si le pointeur de la souris est à l’intérieur du rectangle de délimitation de la fenêtre à mini-cadre pour déterminer si la fenêtre doit être enroulée. Vous pouvez remplacer ce comportement dans une classe dérivée.

## <a name="cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer

Arrête le minuteur d'ancrage.

```cpp
void KillDockingTimer();
```

## <a name="cpaneframewndloadstate"></a><a name="loadstate"></a>CPaneFrameWnd::LoadState

Charge l'état du volet à partir du Registre.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Le nom du profil.

*uiID*<br/>
[dans] L’ID de la vitre.

### <a name="return-value"></a>Valeur de retour

VRAI si l’état de la vitre a été chargé avec succès; autrement FALSE.

## <a name="cpaneframewndm_busesavebits"></a><a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits

Précise s’il faut enregistrer la classe de fenêtre qui a le style de classe CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Notes

Définissez ce membre statique à TRUE pour enregistrer la classe de fenêtre à mini-cadre qui a le style CS_SAVEBITS. Cela peut aider à réduire le scintillement lorsqu’un utilisateur fait glisser la fenêtre mini-cadre.

## <a name="cpaneframewndonbeforedock"></a><a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock

Détermine si l'ancrage est possible.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’amarrage est possible; autrement, FALSE.

## <a name="cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState

Détermine si une fenêtre mini-frame doit être masquée ou affichée.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pour déterminer si une fenêtre mini-cadre doit être enroulée vers le haut ou vers le bas.

Par défaut, le cadre appelle [CPaneFrameWnd::IsRollUp](#isrollup) et [CPaneFrameWnd::IsRollDown](#isrolldown) et s’étire ou restaure la fenêtre mini-cadre. Vous pouvez remplacer cette méthode dans une classe dérivée pour utiliser un effet visuel différent.

## <a name="cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos

Ancre la fenêtre mini-frame à sa dernière position.

```
virtual void OnDockToRecentPos();
```

## <a name="cpaneframewndondrawborder"></a><a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder

Dessine les bordures d'une fenêtre mini-frame.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil utilisé pour dessiner la frontière.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pour dessiner les frontières de la fenêtre mini-cadre.

## <a name="cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer

Arrête le minuteur d'affichage.

```
virtual void OnKillRollUpTimer();
```

## <a name="cpaneframewndonmovepane"></a><a name="onmovepane"></a>CPaneFrameWnd::OnMovePane

Déplace la fenêtre mini-frame selon un décalage spécifié.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans] Un pointeur à une vitre (ignoré).

*ptOffset (en anglais)*<br/>
[dans] Le décalage par lequel déplacer la vitre.

## <a name="cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout

Ajuste la disposition d’une vitre à l’intérieur d’une mini-fenêtre à monture.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’elle doit ajuster la disposition d’une vitre à l’intérieur de la fenêtre mini-cadre.

Par défaut, la vitre est positionnée pour couvrir la zone client complète de la mini-fenêtre de cadre.

## <a name="cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer

Définit le minuteur d'affichage.

```
virtual void OnSetRollUpTimer();
```

## <a name="cpaneframewndonshowpane"></a><a name="onshowpane"></a>CPaneFrameWnd::OnShowPane

Appelé par l'infrastructure quand un volet de la fenêtre mini-frame est masqué ou affiché.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans] La vitre qui est montrée ou cachée.

*bShow (en)*<br/>
[dans] VRAI si la vitre est montrée; FALSE si la vitre est cachée.

### <a name="remarks"></a>Notes

Appelé par le cadre quand une vitre dans la fenêtre mini-cadre est montrée ou cachée. L'implémentation par défaut n'exécute aucune opération.

## <a name="cpaneframewndpin"></a><a name="pin"></a>CPaneFrameWnd::Pin

```cpp
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *bPin*<br/>

### <a name="remarks"></a>Notes

## <a name="cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CPaneFrameWnd::PanDePoint

Retourne un volet s'il contient un point fourni par l'utilisateur à l'intérieur d'une fenêtre mini-frame.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
[dans] Le point que l’utilisateur a cliqué, dans les coordonnées de l’écran.

*nSensibilité*<br/>
[dans] Ce paramètre n’est pas utilisé.

*bCheckVisibilité*<br/>
[dans] VRAI pour spécifier que seules les vitres visibles doivent être retournées; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

La vitre que l’utilisateur a cliqué, ou NULL si aucun volet n’existe à cet endroit.

### <a name="remarks"></a>Notes

Appelez cette méthode pour obtenir une vitre qui contient le point donné.

## <a name="cpaneframewndredrawall"></a><a name="redrawall"></a>CPaneFrameWnd::RedrawAll

Redessine toutes les fenêtres mini-frame.

```
static void RedrawAll();
```

### <a name="remarks"></a>Notes

Cette méthode met à jour toutes les fenêtres mini-cadre en appelant [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) pour chaque fenêtre.

## <a name="cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes

Appelé par l'infrastructure pour supprimer les volets non valides.

```
virtual void RemoveNonValidPanes();
```

## <a name="cpaneframewndremovepane"></a><a name="removepane"></a>CPaneFrameWnd::RemovePane

Supprime un volet de la fenêtre mini-frame.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] Un pointeur à la vitre à enlever.

*bDestroy (en)*<br/>
[dans] Précise ce qui arrive à la fenêtre mini-cadre. Si *bDestroy* est VRAI, cette méthode détruit immédiatement la fenêtre mini-cadre. Si c’est FALSE, cette méthode détruit la fenêtre mini-cadre après un certain retard.

*bNoDelayedDestroy*<br/>
[dans] Si VRAI, la destruction retardée est désactivée. Si FALSE, la destruction retardée est activée.

### <a name="remarks"></a>Notes

Le cadre peut détruire les fenêtres à mini-cadre immédiatement ou après un certain retard. Si vous voulez retarder la destruction des fenêtres mini-cadre, passez FALSE dans le paramètre *bNoDelayedDestroy.* La destruction retardée se produit lorsque le cadre traite le message AFX_WM_CHECKEMPTYMINIFRAME.

## <a name="cpaneframewndreplacepane"></a><a name="replacepane"></a>CPaneFrameWnd::ReplacePane

Remplace un volet par un autre.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Paramètres

*pBarOrg (en)*<br/>
[dans] Un pointeur à la vitre originale.

*pBarReplaceAvec*<br/>
[dans] Un pointeur à la vitre qui remplace la vitre d’origine.

## <a name="cpaneframewndsavestate"></a><a name="savestate"></a>CPaneFrameWnd::SaveState

Enregistre l'état du volet dans le Registre.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Le nom du profil.

*uiID*<br/>
[dans] L’ID de la vitre.

### <a name="return-value"></a>Valeur de retour

VRAI si l’état de la vitre a été sauvé avec succès; autrement FALSE.

## <a name="cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons

Définit les boutons de légende.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Paramètres

*dwButtons dwButtons*<br/>
[dans] Combinaison Bitwise-OR des valeurs suivantes :

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

## <a name="cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow

```cpp
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Paramètres

[dans] *bDelayShow (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager

```cpp
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Paramètres

[dans] *pManager (en anglais)*<br/>

### <a name="remarks"></a>Notes

## <a name="cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer

Définit le minuteur d'ancrage.

```cpp
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Paramètres

*nTimeOut (en)*<br/>
[dans] Valeur de temps d’arrêt en millisecondes.

## <a name="cpaneframewndsetdockstate"></a><a name="setdockstate"></a>CPaneFrameWnd::SetDockState

Définit l'état d'ancrage.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Paramètres

*pDockManager (en anglais)*<br/>
[dans] Un pointeur pour un gestionnaire d’amarrage.

## <a name="cpaneframewndsethotpoint"></a><a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint

```cpp
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Paramètres

[dans] *ptNouveau*<br/>

### <a name="remarks"></a>Notes

## <a name="cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState

Appelé par l'infrastructure pour définir l'état de pré-ancrage.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Paramètres

*preDockState*<br/>
[dans] Valeurs possibles :

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
[dans] Un pointeur à la vitre pour accoster.

*dockMethod*<br/>
[dans] La méthode d’amarrage. (Ce paramètre est ignoré.)

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre mini-cadre est désamarrée; FALSE s’il est amarré.

## <a name="cpaneframewndsizetocontent"></a><a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent

Ajuste la taille d’une fenêtre à mini-cadre de sorte qu’elle soit équivalente à une vitre contenue.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajuster la taille d’une fenêtre mini-cadre à la taille d’une vitre contenue.

## <a name="cpaneframewndstarttearoff"></a><a name="starttearoff"></a>CPaneFrameWnd::StartTearOff

Détache un menu.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
[dans] Un pointeur à un menu.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement, FALSE.

## <a name="cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>

### <a name="remarks"></a>Notes

## <a name="cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pDockingBar (en)*<br/>
[dans] *pTabbedBar (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
