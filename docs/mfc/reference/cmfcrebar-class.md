---
title: Classe CMFCReBar
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: 409c97aba64c97ecf0443d14a70848cc298a44ba
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750004"
---
# <a name="cmfcrebar-class"></a>Classe CMFCReBar

Un `CMFCReBar` objet est une barre de contrôle qui fournit la disposition, la persistance et l’information d’état pour les contrôles de barres d’armature.
Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Ajoute une bande à une barre d’armature.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Overrides [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar:CanFloat](#canfloat)|(Overrides [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCReBar::Créer](#create)|Crée le contrôle des barres d’armature et le fixe à l’objet. `CMFCReBar`|
|[CMFCReBar::EnableDocking](#enabledocking)|(Overrides [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Fournit un accès direct au contrôle commun [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) sous-jacent.|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Overrides [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Overrides [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Overrides [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Overrides [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Notes

Un `CMFCReBar` objet peut contenir une variété de fenêtres d’enfant. Cela comprend les boîtes de modification, les barres d’outils et les boîtes de liste. Vous pouvez resize la barre d’armature de façon programmatique, ou l’utilisateur peut resize manuellement la barre d’armature en faisant glisser sa barre de pincement. Vous pouvez également définir l’arrière-plan d’un objet de barre d’armature à un bitmap de votre choix.

Un objet de barre d’armature se comporte de la même façon qu’un objet de barre d’outils. Un contrôle des barres d’armature peut contenir une ou plusieurs bandes, et chaque bande peut contenir une barre de pincement, une bitmap, une étiquette de texte, et une fenêtre pour enfants.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCReBar` . L’exemple montre comment créer un contrôle des barres d’armature et y ajouter une bande. La bande fonctionne comme une barre d’outils interne. Cet extrait de code fait partie de [l’échantillon de test de barres d’armature.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCReBar::AddBar

Ajoute une bande à une barre d’armature.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans, dehors] Un pointeur à la fenêtre de l’enfant qui doit être inséré dans la barre d’armature. L’objet référencé doit avoir le style de fenêtre **WS_CHILD.**

*pszText*<br/>
[dans] Spécifie le texte à apparaître sur la barre d’armature. Le texte ne fait pas partie de la fenêtre de l’enfant. Au contraire, il est affiché sur la barre d’armature elle-même.

*pbmp*<br/>
[dans, dehors] Spécifie la bitmap à afficher sur le fond de la barre d’armature.

*dwStyle (en)*<br/>
[dans] Contient le style à appliquer à la bande. Pour une liste complète des styles `fStyle` de bande, consultez la description de la structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) dans la documentation Windows SDK.

*clrFore*<br/>
[dans] Représente la couleur de premier plan de la barre d’armature.

*clrBack (en)*<br/>
[dans] Représente la couleur de fond de la barre d’armature.

### <a name="return-value"></a>Valeur de retour

VRAI si la bande a été ajoutée avec succès à la barre d’armature; autrement, FALSE.

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCReBar::Créer

Crée le contrôle des barres d’armature et le fixe à l’objet [CMFCReBar.](../../mfc/reference/cmfcrebar-class.md)

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[dans, dehors] Un pointeur à la fenêtre parente de ce contrôle de barre d’armature.

*dwCtrlStyle (en)*<br/>
[dans] Spécifie le style pour le contrôle des barres d’armature. La valeur de style par défaut est **RBS_BANDBORDERS**, qui affiche des lignes étroites pour séparer les bandes adjacentes sur le contrôle des barres d’armature. Pour une liste de styles valides, voir [Rebar Control Styles](/windows/win32/Controls/rebar-control-styles) dans la documentation Windows SDK.

*dwStyle (en)*<br/>
[dans] Le style de fenêtre du contrôle des barres d’armature. Pour une liste de styles valides, voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[dans] L’id de la fenêtre pour enfants de la barre d’armature.

### <a name="return-value"></a>Valeur de retour

VRAI si la barre d’armature a été créée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

Fournit un `CReBarCtrl` accès direct au `CMFCReBar` contrôle commun sous-jacent des objets.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à `CReBarCtrl` l’objet sous-jacent.

### <a name="remarks"></a>Notes

Appelez cette méthode pour profiter de la fonctionnalité de contrôle commun de barre d’armature windows lors de la personnalisation de votre barre d’armature.

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

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

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCReBar:CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar::EnableDocking

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

[dans] *dwDockStyle (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Paramètres

[dans] *CPoint (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Paramètres

[dans] *point*<br/>
[dans] *pTI (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

[dans] *pTarget*<br/>
[dans] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

[dans] *dwAlignment*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CReBarCtrl](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
