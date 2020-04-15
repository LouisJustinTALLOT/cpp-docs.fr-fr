---
title: CMFCAutoHideBar, classe
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: 62750f4fb1261f4f30286297c3a240ab67e6df1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369898"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar, classe

`CMFCAutoHideBar` est une classe de barre d’outils spéciale qui implémente la fonctionnalité de masquage automatique.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Overrides [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Create](#create)|Crée une barre de commande et la fixe à l’objet [CPane.](../../mfc/reference/cpane-class.md) (Overrides [CPane::Créer](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Appelé par l'infrastructure quand un menu de volet spécial va être affiché. (Overrides [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Overrides [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Étire un volet sur le plan vertical ou horizontal. (Overrides [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Le délai entre le moment où l’utilisateur place le curseur de souris sur une [classe CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) et le moment où le cadre affiche la fenêtre associée.|

## <a name="remarks"></a>Notes

Quand l'utilisateur passe d'un volet d'ancrage à un mode de masquage automatique, l'infrastructure crée automatiquement un objet `CMFCAutoHideBar`. Il crée également les objets [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) et [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) nécessaires. Chaque objet `CAutoHideDockSite` est associé à un `CMFCAutoHideButton` individuel.

La classe `CMFCAutoHideBar` implémente l'affichage d'un `CAutoHideDockSite` quand l'utilisateur pointe la souris sur un `CMFCAutoHideButton`. Quand la barre d'outils reçoit un message WM_MOUSEMOVE, `CMFCAutoHideBar` démarre un minuteur. Celui-ci envoie une notification d'événement WM_TIMER à la barre d'outils à la fin du processus. La barre d'outils traite cet événement en vérifiant si le pointeur de la souris est positionné sur le même bouton de masquage automatique qu'au moment où le minuteur a démarré. Si c'est le cas, le `CAutoHideDockSite` attaché s'affiche.

Vous pouvez contrôler le délai du minuteur en définissant `m_nShowAHWndDelay`. La valeur par défaut est de 400 ms.

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet `CMFCAutoHideBar` et utiliser sa méthode `GetDockSiteRow`.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow

Ajoute des fonctionnalités à une fenêtre `CDockablePane` , ce qui lui permet de se masquer automatiquement.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

*pAutoHideWnd*<br/>
[dans] La fenêtre que tu veux cacher.

*dwAlignment*<br/>
[dans] Une valeur qui spécifie l’alignement du bouton de cache automatique avec la fenêtre d’application.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le *paramètre dwAlignment* indique où se trouve le bouton de cache automatique dans l’application. Le paramètre peut avoir l’une des valeurs suivantes :

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

[dans] *bStretch*<br/>

[dans] *bHorz (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar

Construit un objet CMFCAutoHideBar.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHideBar::Créer

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

*lpszClassName (en)*<br/>

*dwStyle (en)*<br/>

*Rect*<br/>

*pParentWnd*<br/>

*nID*<br/>

*dwControlBarStyle (en)*<br/>

*pContext*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow

Retourne un pointeur vers la première fenêtre à masquage automatique de l’application.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>Valeur de retour

La première fenêtre à masquage automatique de l’application, ou NULL si elle n’existe pas.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount

Obtient le nombre de boutons Masquer automatiquement visibles.

```
int GetVisibleCount();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de boutons Masquer automatiquement visibles.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHideBar:m_nShowAHWndDelay

Le délai entre le moment où l’utilisateur place le curseur de souris sur une [classe CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) et le moment où le cadre affiche la fenêtre associée.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur place le curseur de souris sur un, `CMFCAutoHideButton`il ya un léger retard avant que le cadre affiche la fenêtre associée. Ce paramètre détermine la durée de ce délai en millisecondes.

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Paramètres

[dans] *CPoint (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow

Supprime et détruit la fenêtre à masquage automatique.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>Paramètres

CDockablePaneMD *pAutoHideWnd* La fenêtre de cache automatique à enlever.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup

Marque une barre à masquage automatique comme active.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Paramètres

[dans] BOOL *bActive* TRUE à mettre en actif; autrement FALSE.

### <a name="remarks"></a>Notes

Consultez [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState

```
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>Paramètres

*bState*<br/>
[dans] État à définir.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow

Affiche la fenêtre à masquage automatique.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Paramètres

*pAutoHideWnd*<br/>
[dans] Fenêtre à montrer.

*bShow (en)*<br/>
[dans] VRAI pour montrer la fenêtre.

*bDelay (en)*<br/>
[dans] Ce paramètre est ignoré.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFCAutoHideBar::StretchPane

Redimensionne la barre à masquage automatique à son état réduit pour faire tenir l’objet `CMFCAutoHideButton` .

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>Paramètres

*nLength (en)*<br/>
[dans] La valeur n’est pas utilisée dans la mise en œuvre de base. Dans les implémentations dérivées, utilisez cette valeur pour indiquer la longueur du volet redimensionné.

*bVert (en)*<br/>
[dans] La valeur n’est pas utilisée dans la mise en œuvre de base. Dans les implémentations dérivées, utilisez TRUE pour gérer le boîtier où la barre de cache automatique est effondrée verticalement, et FALSE pour le cas où la barre de cache automatique est effondrée horizontalement.

### <a name="return-value"></a>Valeur de retour

Taille résultante du volet redimensionné.

### <a name="remarks"></a>Notes

Les classes dérivées peuvent substituer cette méthode pour personnaliser le comportement.

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode

Désactive le mode de masquage automatique pour un groupe de barres avec masquage automatique.

```
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>Paramètres

[dans] pFirstBarInGroup Un pointeur à la première barre de cache automatique dans le groupe.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState

Appelé par l’infrastructure quand de la barre à masquage automatique doit être redessinée.

```
void UpdateVisibleState();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[Classe CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton, classe](../../mfc/reference/cmfcautohidebutton-class.md)
