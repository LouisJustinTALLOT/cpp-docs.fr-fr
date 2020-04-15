---
title: Classe CMultiPaneFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
ms.openlocfilehash: db5f0b3c6b48a3704803d77242904e25e053b7ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363394"
---
# <a name="cmultipaneframewnd-class"></a>Classe CMultiPaneFrameWnd

La `CMultiPaneFrameWnd` classe étend [CPaneFrameWnd Classe](../../mfc/reference/cpaneframewnd-class.md). Elle peut prendre en charge plusieurs volets. Au lieu d’une seule poignée `CMultiPaneFrameWnd` intégrée à une barre de contrôle, contient un objet `CMultiPaneFrameWnd` de classe [CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) qui permet à l’utilisateur d’amarrer l’un à l’autre et de créer dynamiquement plusieurs fenêtres flottantes et tabbed.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMultiPaneFrameWnd : public CPaneFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMultiPaneFrameWnd::AddPane](#addpane)|Ajoute un volet. (Overrides [CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane).)|
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|Ajuste la disposition de la fenêtre mini-frame. (Overrides [CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).)|
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(Overrides [CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes).)|
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcule le rectangle prévu d’une fenêtre amarrée. (Overrides [CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect).)|
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|Détermine si la vitre actuelle peut s’amarrer à une autre vitre ou à une fenêtre de cadre. (Overrides [CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached).)|
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Détermine si la fenêtre mini-cadre peut s’amarrer à une vitre. (Overrides [CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).)|
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(Overrides [CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).)|
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|(Substitue `CPaneFrameWnd::CloseMiniFrame`.)|
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Convertit le volet en document à onglets. (Overrides [CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).)|
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||
|[CMultiPaneFrameWnd::DockPane](#dockpane)|Ancre le volet. (Overrides [CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane).)|
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|Retourne le texte de légende. (Overrides [CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).)|
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|Renvoie une référence à l’objet interne de gestionnaire de conteneurs.|
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Retourne le premier volet visible contenu dans une fenêtre mini-frame. (Overrides [CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane).)|
|[CMultiPaneFrameWnd::GetPane](#getpane)|Retourne un volet contenu dans la fenêtre mini-frame. (Overrides [CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane).)|
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|Retourne le nombre de volets contenus dans une fenêtre mini-frame. (Overrides [CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount).)|
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Retourne le nombre de volets visibles contenus dans une fenêtre mini-frame. (Overrides [CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount).)|
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||
|[CMultiPaneFrameWnd::LoadState](#loadstate)|Charge l'état du volet à partir du Registre. (Overrides [CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate).)|
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ancre la fenêtre mini-frame à sa dernière position. (Overrides [CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos).)|
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Arrête le minuteur d'affichage. (Overrides [CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer).)|
|[CMultiPaneFrameWnd:::OnPaneRecalcLayout](#onpanerecalclayout)|Ajuste la disposition d’une vitre à l’intérieur d’une mini-fenêtre à monture. (Overrides [CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).)|
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Définit le minuteur d'affichage. (Overrides [CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).)|
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|Appelé par l'infrastructure quand un volet de la fenêtre mini-frame est masqué ou affiché. (Overrides [CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane).)|
|[CMultiPaneFrameWnd::PanDePoint](#panefrompoint)|Retourne un volet s'il contient un point fourni par l'utilisateur à l'intérieur d'une fenêtre mini-frame. (Overrides [CPaneFrameWnd::PanDePoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint).)|
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Appelé par l'infrastructure pour supprimer les volets non valides. (Overrides [CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes).)|
|[CMultiPaneFrameWnd::RemovePane](#removepane)|Supprime un volet de la fenêtre mini-frame. (Overrides [CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane).)|
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|Remplace un volet par un autre. (Overrides [CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane).)|
|[CMultiPaneFrameWnd::SaveState](#savestate)|Enregistre l'état du volet dans le Registre. (Overrides [CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate).)|
|[CMultiPaneFrameWnd::Serialize](#serialize)|(Substitue `CPaneFrameWnd::Serialize`.)|
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|Définit l'état d'ancrage. (Overrides [CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).)|
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|Définit l’état de prédocking. (Overrides [CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).)|
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(Overrides [CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).)|
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(Overrides [CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).)|

## <a name="remarks"></a>Notes

La plupart des méthodes de cette classe remplacent les méthodes de la classe [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

Si une vitre utilise le style AFX_CBRS_AUTO_ROLLUP et que l’utilisateur accoste cette vitre vers une fenêtre à ossature multi-volets, l’utilisateur peut rouler la fenêtre indépendamment des paramètres de style des autres vitres amarrées.

Le cadre crée `CMultiPaneFrameWnd` automatiquement un objet lorsque l’utilisateur flotte une vitre qui utilise le style CBRS_FLOAT_MULTI.

Pour plus d’informations sur `CPaneFrameWnd` le déneigement d’une classe de la classe et sa création dynamique, voir [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer `CMultiPaneFrameWnd` un pointeur sur un objet. Cet extrait de code fait partie de [l’échantillon Set Pane Size](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxMultiPaneFrameWnd.h

## <a name="cmultipaneframewndaddpane"></a><a name="addpane"></a>CMultiPaneFrameWnd::AddPane

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Paramètres

[dans] *pWnd (pWnd)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndaddrecentpane"></a><a name="addrecentpane"></a>CMultiPaneFrameWnd::AddRecentPane

```
virtual BOOL AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndadjustlayout"></a><a name="adjustlayout"></a>CMultiPaneFrameWnd::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CMultiPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CMultiPaneFrameWnd::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pWndToDock*<br/>
[dans] *ptMouse (en)*<br/>
[dans] *rectResult*<br/>
[dans] *bDrawTab (en anglais seulement)*<br/>
[dans] *ppTargetBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndcanbeattached"></a><a name="canbeattached"></a>CMultiPaneFrameWnd::CanBeAttached

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CMultiPaneFrameWnd::CanBeDockedToPane

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Paramètres

[dans] *pDockingBar (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CMultiPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndcloseminiframe"></a><a name="closeminiframe"></a>CMultiPaneFrameWnd::CloseMiniFrame

```
virtual void CloseMiniFrame();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CMultiPaneFrameWnd::ConvertToTabbedDocument

```
virtual void ConvertToTabbedDocument();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewnddockframe"></a><a name="dockframe"></a>CMultiPaneFrameWnd::DockFrame

```
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

[dans] *pDockedFrame (en)*<br/>
[dans] *dockMethod*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewnddockpane"></a><a name="dockpane"></a>CMultiPaneFrameWnd::DockPane

```
virtual BOOL DockPane(CDockablePane* pDockedBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pDockedBar (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewnddockrecentpanetomainframe"></a><a name="dockrecentpanetomainframe"></a>CMultiPaneFrameWnd::DockRecentPaneToMainFrame

```
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CMultiPaneFrameWnd::GetCaptionText

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CMultiPaneFrameWnd::GetFirstVisiblePane

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndgetpane"></a><a name="getpane"></a>CMultiPaneFrameWnd::GetPane

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndgetpanecontainermanager"></a><a name="getpanecontainermanager"></a>CMultiPaneFrameWnd::GetPaneContainerManager

Renvoie une référence à l’objet interne de gestionnaire de conteneurs.

```
CPaneContainerManager& GetPaneContainerManager();
```

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet interne de gestionnaire de conteneurs.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à l’objet interne [de classe CPaneContainerManager.](../../mfc/reference/cpanecontainermanager-class.md)

## <a name="cmultipaneframewndgetpanecount"></a><a name="getpanecount"></a>CMultiPaneFrameWnd::GetPaneCount

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CMultiPaneFrameWnd::GetVisiblePaneCount

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndinsertpane"></a><a name="insertpane"></a>CMultiPaneFrameWnd::InsertPane

```
virtual BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter);
```

### <a name="parameters"></a>Paramètres

[dans] *pControlBar (en)*<br/>
[dans] *pTarget*<br/>
[dans] *bAprès*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndloadstate"></a><a name="loadstate"></a>CMultiPaneFrameWnd::LoadState

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

[dans] *lpszProfileName*<br/>
[dans] *uiID*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CMultiPaneFrameWnd::OnDockToRecentPos

```
virtual void OnDockToRecentPos();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CMultiPaneFrameWnd::OnKillRollUpTimer

```
virtual void OnKillRollUpTimer();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CMultiPaneFrameWnd:::OnPaneRecalcLayout

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CMultiPaneFrameWnd::OnSetRollUpTimer

```
virtual void OnSetRollUpTimer();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndonshowpane"></a><a name="onshowpane"></a>CMultiPaneFrameWnd::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>
[dans] *bShow (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CMultiPaneFrameWnd::PanDePoint

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Paramètres

[dans] *point*<br/>
[dans] *nSensibilité*<br/>
[dans] *bCheckVisibilité*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CMultiPaneFrameWnd::RemoveNonValidPanes

```
virtual void RemoveNonValidPanes();
```

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndremovepane"></a><a name="removepane"></a>CMultiPaneFrameWnd::RemovePane

```
virtual void RemovePane(
    CBasePane* pBar,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>
[dans] *bDestroy (en)*<br/>
[dans] *bNoDelayedDestroy*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndreplacepane"></a><a name="replacepane"></a>CMultiPaneFrameWnd::ReplacePane

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Paramètres

[dans] *pBarOrg (en)*<br/>
[dans] *pBarReplaceAvec*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndsavestate"></a><a name="savestate"></a>CMultiPaneFrameWnd::SaveState

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

[dans] *lpszProfileName*<br/>
[dans] *uiID*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndserialize"></a><a name="serialize"></a>CMultiPaneFrameWnd::Serialize

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

[dans] *ar*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndsetdockstate"></a><a name="setdockstate"></a>CMultiPaneFrameWnd::SetDockState

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Paramètres

[dans] *pDockManager (en anglais)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndsetlastfocusedpane"></a><a name="setlastfocusedpane"></a>CMultiPaneFrameWnd::SetLastFocusedPane

```
void SetLastFocusedPane(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

[dans] *hwnd hwnd*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CMultiPaneFrameWnd::SetPreDockState

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Paramètres

[dans] *preDockState*<br/>
[dans] *pBarToDock*<br/>
[dans] *dockMethod*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CMultiPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmultipaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CMultiPaneFrameWnd::StoreRecentTabRelatedInfo

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
[CPaneFrameWnd, classe](../../mfc/reference/cpaneframewnd-class.md)
