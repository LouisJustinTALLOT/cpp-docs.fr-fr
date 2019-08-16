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
ms.openlocfilehash: 37ab241219f28336e73ea459a4e32ff413de8964
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502975"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd, classe

Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.

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
|`CPaneFrameWnd::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) .|
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

### <a name="data-members"></a>Membres de données

|Nom|Description|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Spécifie s’il faut inscrire la classe de fenêtre avec le style de classe CS_SAVEBITS.|

## <a name="remarks"></a>Notes

L'infrastructure crée automatiquement un objet `CPaneFrameWnd` quand un volet passe de l'état ancré à l'état flottant.

Vous pouvez faire glisser une fenêtre mini-frame avec son contenu visible (ancrage immédiat) ou en utilisant un rectangle de glissement (ancrage standard). Le mode d'ancrage du volet conteneur du mini-frame détermine le comportement de glissement du mini-frame. Pour plus d’informations, consultez [CBasePane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Une fenêtre mini-frame présente des boutons sur la légende en fonction du style du volet contenu. Si le volet peut être fermé ( [CBasePane:: CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), il affiche un bouton Fermer. Si le volet a le style AFX_CBRS_AUTO_ROLLUP, il affiche un code confidentiel.

Si vous faites dériver une classe de `CPaneFrameWnd`, vous devez indiquer à l'infrastructure comment la créer. Créez la classe en remplaçant [CPane:: CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), ou définissez le `CPane::m_pMiniFrameRTC` membre afin qu’il pointe vers les informations de classe d’exécution de votre classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxPaneFrameWnd. h

##  <a name="addpane"></a>  CPaneFrameWnd::AddPane

Ajoute un volet.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Volet à ajouter.

##  <a name="addremovepanefromgloballist"></a>  CPaneFrameWnd::AddRemovePaneFromGlobalList

Ajoute ou supprime un volet de la liste globale.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Volet à ajouter ou supprimer.

*bAdd*<br/>
dans Si la valeur est différente de zéro, ajoutez le volet. Si la valeur est 0, supprimez le volet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode a réussi; Sinon, 0.

##  <a name="adjustlayout"></a>  CPaneFrameWnd::AdjustLayout

Ajuste la disposition de la fenêtre mini-frame.

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>  CPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Notes

##  <a name="calcbordersize"></a>  CPaneFrameWnd::CalcBorderSize

Calcule la taille des bordures d’une fenêtre Miniframe.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Paramètres

*rectBorderSize*<br/>
à Contient la taille, en pixels, de la bordure de la fenêtre Miniframe.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour calculer la taille de la bordure d’une fenêtre Miniframe. La taille retournée varie selon qu’une fenêtre Miniframe contient une barre d’outils ou un [CDockablePane](../../mfc/reference/cdockablepane-class.md).

##  <a name="calcexpecteddockedrect"></a>  CPaneFrameWnd::CalcExpectedDockedRect

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
dans Pointeur vers la fenêtre à ancrer.

*ptMouse*<br/>
dans Emplacement de la souris.

*rectResult*<br/>
à Rectangle calculé.

*bDrawTab*<br/>
à Si la valeur est TRUE, dessinez un onglet. Si la valeur est FALSe, ne dessinez pas d’onglet.

*ppTargetBar*<br/>
à Pointeur vers le volet cible.

### <a name="remarks"></a>Notes

Cette méthode calcule le rectangle qu’une fenêtre occuperait si un utilisateur a fait glisser la fenêtre jusqu’au point spécifié par *ptMouse* et l’a ancré ici.

##  <a name="canbeattached"></a>  CPaneFrameWnd::CanBeAttached

Détermine si le volet actif peut être ancré à un autre volet ou à une fenêtre frame.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet peut être ancré à un autre volet ou fenêtre frame; Sinon, FALSe.

##  <a name="canbedockedtopane"></a>  CPaneFrameWnd::CanBeDockedToPane

Détermine si la fenêtre mini-frame peut être ancrée à un volet.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Paramètres

*pDockingBar*<br/>
dans Un volet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le mini-frame peut être ancré à *pDockingBar*; Sinon, 0.

##  <a name="checkgrippervisibility"></a>  CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Notes

##  <a name="converttotabbeddocument"></a>  CPaneFrameWnd::ConvertToTabbedDocument

Convertit le volet en document à onglets.

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>  CPaneFrameWnd::Create

Crée une fenêtre Miniframe et l’attache à l’objet [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszWindowName*<br/>
dans Spécifie le texte à afficher dans la fenêtre Miniframe.

*dwStyle*<br/>
dans Spécifie le style de la fenêtre. Pour plus d’informations, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*rect*<br/>
dans Spécifie la taille et la position initiales de la fenêtre Miniframe.

*pParentWnd*<br/>
[in, out] Spécifie le cadre parent de la fenêtre Miniframe. Cette valeur ne doit pas être NULL.

*pContext*<br/>
[in, out] Spécifie le contexte défini par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre a été créée avec succès; Sinon, FALSe.

### <a name="remarks"></a>Notes

Une fenêtre Miniframe est créée en deux étapes. Tout d’abord, l’infrastructure `CPaneFrameWnd` crée un objet. Ensuite, il appelle `Create` pour créer la fenêtre Miniframe Windows et l’attacher à l' `CPaneFrameWnd` objet.

##  <a name="createex"></a>  CPaneFrameWnd::CreateEx

Crée une fenêtre Miniframe et l’attache à l’objet [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

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
dans Spécifie le style de fenêtre étendu. Pour plus d’informations, consultez [styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) .

*lpszWindowName*<br/>
dans Spécifie le texte à afficher dans la fenêtre Miniframe.

*dwStyle*<br/>
dans Spécifie le style de la fenêtre. Pour plus d’informations, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*rect*<br/>
dans Spécifie la taille et la position initiales de la fenêtre Miniframe.

*pParentWnd*<br/>
[in, out] Spécifie le cadre parent de la fenêtre Miniframe. Cette valeur ne doit pas être NULL.

*pContext*<br/>
[in, out] Spécifie le contexte défini par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre a été créée avec succès; Sinon, FALSe.

### <a name="remarks"></a>Notes

Une fenêtre Miniframe est créée en deux étapes. Tout d’abord, l’infrastructure `CPaneFrameWnd` crée un objet. Ensuite, il appelle `Create` pour créer la fenêtre Miniframe Windows et l’attacher à l' `CPaneFrameWnd` objet.

##  <a name="dockpane"></a>  CPaneFrameWnd::DockPane

Ancre le volet.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Paramètres

*bWasDocked*<br/>
à TRUE si le volet a déjà été ancré; Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

Si l’opération a réussi, le `CDockablePane` auquel le volet a été ancré; sinon, null.

##  <a name="findfloatingpanebyid"></a>  CPaneFrameWnd::FindFloatingPaneByID

Recherche un volet à partir de l'ID de contrôle spécifié dans la liste globale des volets flottants.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans Représente l’ID de contrôle du volet à rechercher.

### <a name="return-value"></a>Valeur de retour

Volet avec l’ID de contrôle spécifié; Sinon, NULL, si aucun volet n’a l’ID de contrôle spécifié.

##  <a name="framefrompoint"></a>  CPaneFrameWnd::FrameFromPoint

Recherche la fenêtre mini-frame qui contient le point spécifié.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
dans Point, en coordonnées d’écran.

*nSensitivity*<br/>
dans Augmentez la taille de la zone de recherche de la fenêtre mini-frame. Une fenêtre mini-frame répond aux critères de recherche si le point donné se trouve dans la zone augmentée.

*pFrameToExclude*<br/>
dans Spécifie une fenêtre mini-frame à exclure de la recherche.

*bFloatMultiOnly*<br/>
dans Si la valeur est TRUE, seules les fenêtres de mini-frame de recherche ont le style CBRS_FLOAT_MULTI. Si la valeur est FALSe, effectuer une recherche dans toutes les fenêtres mini-frame.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre mini-frame qui contient *PT*; Sinon, NULL.

##  <a name="getcaptionheight"></a>  CPaneFrameWnd::GetCaptionHeight

Retourne la hauteur de la légende de fenêtre mini-frame.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Valeur de retour

Hauteur, en pixels, de la fenêtre mini-frame.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer la hauteur d’une fenêtre mini-frame. Par défaut, la hauteur est définie sur SM_CYSMCAPTION. Pour plus d’informations, consultez [fonction GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

##  <a name="getcaptionrect"></a>  CPaneFrameWnd::GetCaptionRect

Calcule le rectangle englobant d'une légende de fenêtre mini-frame.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Paramètres

*rectCaption*<br/>
à Contient la taille et la position de la légende de la fenêtre mini-frame, en coordonnées d’écran.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour calculer le rectangle englobant d’une légende de fenêtre mini-frame.

##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText

Retourne le texte de légende.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Valeur de retour

Texte de légende de la fenêtre mini-frame.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand elle affiche le texte de la légende.

##  <a name="getdockingmanager"></a>  CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getdockingmode"></a>  CPaneFrameWnd::GetDockingMode

Retourne le mode d'ancrage.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Valeur de retour

Mode d’ancrage. L’une des valeurs suivantes :

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>  CPaneFrameWnd::GetFirstVisiblePane

Retourne le premier volet visible contenu dans une fenêtre mini-frame.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Valeur de retour

Le premier volet de la fenêtre mini-frame, ou NULL si la fenêtre mini-frame ne contient aucun volet.

##  <a name="gethotpoint"></a>  CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getpane"></a>  CPaneFrameWnd::GetPane

Retourne un volet contenu dans la fenêtre mini-frame.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Valeur de retour

Volet contenu dans le mini-frame, ou NULL si la fenêtre mini-frame ne contient aucun volet.

### <a name="remarks"></a>Notes

##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount

Retourne le nombre de volets contenus dans une fenêtre mini-frame.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de volets dans la fenêtre mini-frame. Cette valeur peut être égale à zéro.

### <a name="remarks"></a>Notes

##  <a name="getparent"></a>  CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getpinstate"></a>  CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getrecentfloatingrect"></a>  CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getvisiblepanecount"></a>  CPaneFrameWnd::GetVisiblePaneCount

Retourne le nombre de volets visibles contenus dans une fenêtre mini-frame.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de volets visibles.

### <a name="remarks"></a>Notes

##  <a name="hittest"></a>  CPaneFrameWnd::HitTest

Détermine la partie d'une fenêtre mini-frame qui se trouve à un point donné.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
dans Point à tester.

*bDetectCaption*<br/>
dans Si la valeur est TRUE, vérifiez le point par rapport à la légende. Si la valeur est FALSe, ignorez la légende.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|HTNOWHERE|Le point est en dehors de la fenêtre mini-frame.|
|HTCLIENT|Le point se trouve dans la zone cliente.|
|HTCAPTION|Le point se trouve sur la légende.|
|HTTOP|Le point se trouve en haut.|
|HTTOPLEFT|Le point se trouve en haut à gauche.|
|HTTOPRIGHT|Le point se trouve en haut à droite.|
|HTLEFT|Le point se trouve à gauche.|
|HTRIGHT|Le point se trouve à droite.|
|HTBOTTOM|Le point se trouve en bas.|
|HTBOTTOMLEFT|Le point se trouve en bas à gauche.|
|HTBOTTOMRIGHT|Le point se trouve en bas à droite.|

##  <a name="iscaptured"></a>  CPaneFrameWnd::IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isdelayshow"></a>  CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isrolldown"></a>  CPaneFrameWnd::IsRollDown

Détermine si une fenêtre mini-frame doit être masquée.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre mini-frame doit être restaurée; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour déterminer si une fenêtre mini-frame doit être restaurée. La fonctionnalité ROLLUP/répercuter est activée pour une fenêtre mini-frame si elle contient au moins un volet qui a l’indicateur AFX_CBRS_AUTO_ROLLUP. Cet indicateur est défini lors de la création d’un volet. Pour plus d’informations, consultez [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Par défaut, le Framework vérifie si le pointeur de la souris se trouve à l’intérieur du rectangle englobant de la fenêtre mini-frame pour déterminer si la fenêtre doit être restaurée. Vous pouvez substituer ce comportement dans une classe dérivée.

##  <a name="isrollup"></a>  CPaneFrameWnd::IsRollUp

Détermine si une fenêtre mini-frame doit être affichée.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre mini-frame doit être reportée; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour déterminer si une fenêtre mini-frame doit être cumulée. La fonctionnalité ROLLUP/répercuter est activée pour une fenêtre mini-frame si elle contient au moins un volet qui a l’indicateur AFX_CBRS_AUTO_ROLLUP. Cet indicateur est défini lors de la création d’un volet. Pour plus d’informations, consultez [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Par défaut, le Framework vérifie si le pointeur de la souris se trouve à l’intérieur du rectangle englobant de la fenêtre mini-frame pour déterminer si la fenêtre doit être cumulée. Vous pouvez substituer ce comportement dans une classe dérivée.

##  <a name="killdockingtimer"></a>  CPaneFrameWnd::KillDockingTimer

Arrête le minuteur d'ancrage.

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>  CPaneFrameWnd::LoadState

Charge l'état du volet à partir du Registre.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Nom du profil.

*uiID*<br/>
dans ID du volet.

### <a name="return-value"></a>Valeur de retour

TRUE si l’état du volet a été chargé avec succès; Sinon, FALSe.

##  <a name="m_busesavebits"></a>  CPaneFrameWnd::m_bUseSaveBits

Spécifie s’il faut inscrire la classe de fenêtre qui a le style de classe CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre statique pour inscrire la classe de fenêtre mini-frame qui a le style CS_SAVEBITS. Cela peut contribuer à réduire le scintillement lorsqu’un utilisateur fait glisser la fenêtre mini-frame.

##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock

Détermine si l'ancrage est possible.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’ancrage est possible; Sinon, FALSe.

##  <a name="oncheckrollstate"></a>  CPaneFrameWnd::OnCheckRollState

Détermine si une fenêtre mini-frame doit être masquée ou affichée.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour déterminer si une fenêtre mini-frame doit être reportée ou déroulée.

Par défaut, l’infrastructure appelle [CPaneFrameWnd:: IsRollUp](#isrollup) et [CPaneFrameWnd:: IsRollDown](#isrolldown) , puis étire ou restaure simplement la fenêtre mini-frame. Vous pouvez substituer cette méthode dans une classe dérivée pour utiliser un autre effet visuel.

##  <a name="ondocktorecentpos"></a>  CPaneFrameWnd::OnDockToRecentPos

Ancre la fenêtre mini-frame à sa dernière position.

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>  CPaneFrameWnd::OnDrawBorder

Dessine les bordures d'une fenêtre mini-frame.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Contexte de périphérique (Device Context) utilisé pour dessiner la bordure.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pour dessiner les bordures de la fenêtre mini-frame.

##  <a name="onkillrolluptimer"></a>  CPaneFrameWnd::OnKillRollUpTimer

Arrête le minuteur d'affichage.

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>  CPaneFrameWnd::OnMovePane

Déplace la fenêtre mini-frame selon un décalage spécifié.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
dans Pointeur vers un volet (ignoré).

*ptOffset*<br/>
dans Décalage selon lequel déplacer le volet.

##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout

Ajuste la disposition d’un volet à l’intérieur d’une fenêtre mini-frame.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’elle doit ajuster la disposition d’un volet à l’intérieur de la fenêtre mini-frame.

Par défaut, le volet est positionné pour couvrir la totalité de la zone cliente de la fenêtre mini-frame.

##  <a name="onsetrolluptimer"></a>  CPaneFrameWnd::OnSetRollUpTimer

Définit le minuteur d'affichage.

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>  CPaneFrameWnd::OnShowPane

Appelé par l'infrastructure quand un volet de la fenêtre mini-frame est masqué ou affiché.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
dans Volet affiché ou masqué.

*bShow*<br/>
dans TRUE si le volet est affiché; FALSe si le volet est masqué.

### <a name="remarks"></a>Notes

Appelé par le Framework quand un volet dans la fenêtre mini-frame est affiché ou masqué. L'implémentation par défaut n'exécute aucune opération.

##  <a name="pin"></a>  CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *bPin*<br/>

### <a name="remarks"></a>Notes

##  <a name="panefrompoint"></a>  CPaneFrameWnd::PaneFromPoint

Retourne un volet s'il contient un point fourni par l'utilisateur à l'intérieur d'une fenêtre mini-frame.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
dans Point sur lequel l’utilisateur a cliqué, en coordonnées d’écran.

*nSensitivity*<br/>
dans Ce paramètre n’est pas utilisé.

*bCheckVisibility*<br/>
dans TRUE pour spécifier que seuls les volets visibles doivent être retournés; Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

Le volet sur lequel l’utilisateur a cliqué, ou NULL s’il n’existe aucun volet à cet emplacement.

### <a name="remarks"></a>Notes

Appelez cette méthode pour obtenir un volet qui contient le point donné.

##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll

Redessine toutes les fenêtres mini-frame.

```
static void RedrawAll();
```

### <a name="remarks"></a>Notes

Cette méthode met à jour toutes les fenêtres mini-frame en appelant [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) pour chaque fenêtre.

##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes

Appelé par l'infrastructure pour supprimer les volets non valides.

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>  CPaneFrameWnd::RemovePane

Supprime un volet de la fenêtre mini-frame.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Pointeur vers le volet à supprimer.

*bDestroy*<br/>
dans Spécifie ce qui se passe dans la fenêtre mini-frame. Si *bDestroy* a la valeur true, cette méthode détruit immédiatement la fenêtre mini-frame. Si la valeur est FALSe, cette méthode détruit la fenêtre mini-frame après un certain délai.

*bNoDelayedDestroy*<br/>
dans Si la valeur est TRUE, la destruction différée est désactivée. Si la valeur est FALSe, la destruction différée est activée.

### <a name="remarks"></a>Notes

L’infrastructure peut détruire les fenêtres mini-frame immédiatement ou après un certain délai. Si vous souhaitez différer la destruction des fenêtres mini-frame, transmettez FALSe dans le paramètre *bNoDelayedDestroy* . La destruction différée se produit lorsque l’infrastructure traite le message AFX_WM_CHECKEMPTYMINIFRAME.

##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane

Remplace un volet par un autre.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Paramètres

*pBarOrg*<br/>
dans Pointeur vers le volet d’origine.

*pBarReplaceWith*<br/>
dans Pointeur vers le volet qui remplace le volet d’origine.

##  <a name="savestate"></a>  CPaneFrameWnd::SaveState

Enregistre l'état du volet dans le Registre.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Nom du profil.

*uiID*<br/>
dans ID du volet.

### <a name="return-value"></a>Valeur de retour

TRUE si l’état du volet a été enregistré avec succès; Sinon, FALSe.

##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons

Définit les boutons de légende.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Paramètres

*dwButtons*<br/>
dans Combinaison au niveau du bit des valeurs suivantes:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Paramètres

dans *bDelayShow*<br/>

### <a name="remarks"></a>Notes

##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Paramètres

dans *pManager*<br/>

### <a name="remarks"></a>Notes

##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer

Définit le minuteur d'ancrage.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Paramètres

*nTimeOut*<br/>
dans Valeur du délai d’attente en millisecondes.

##  <a name="setdockstate"></a>  CPaneFrameWnd::SetDockState

Définit l'état d'ancrage.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Paramètres

*pDockManager*<br/>
dans Pointeur vers un gestionnaire d’ancrage.

##  <a name="sethotpoint"></a>  CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Paramètres

dans *ptNew*<br/>

### <a name="remarks"></a>Notes

##  <a name="setpredockstate"></a>  CPaneFrameWnd::SetPreDockState

Appelé par l'infrastructure pour définir l'état de pré-ancrage.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Paramètres

*preDockState*<br/>
dans Valeurs possibles:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
dans Pointeur vers le volet à ancrer.

*dockMethod*<br/>
dans Méthode d’ancrage. (Ce paramètre est ignoré.)

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre mini-frame n’est pas ancrée; FALSe s’il est ancré.

##  <a name="sizetocontent"></a>  CPaneFrameWnd::SizeToContent

Ajuste la taille d’une fenêtre mini-frame afin qu’elle soit équivalente à un volet contenu.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajuster la taille d’une fenêtre mini-frame à la taille d’un volet contenu.

##  <a name="starttearoff"></a>  CPaneFrameWnd::StartTearOff

Détache un menu.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
dans Pointeur vers un menu.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi; Sinon, FALSe.

##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="remarks"></a>Notes

##  <a name="storerecenttabrelatedinfo"></a>  CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Paramètres

dans *pDockingBar*<br/>
dans *pTabbedBar*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
