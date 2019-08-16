---
title: CMFCReBar, classe
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
ms.openlocfilehash: d348cf7aac57ce213e4d3f602501d12cee8e20d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505444"
---
# <a name="cmfcrebar-class"></a>CMFCReBar, classe

Un `CMFCReBar` objet est une barre de contrôle qui fournit des informations de disposition, de persistance et d’État pour les contrôles Rebar.
Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Ajoute une bande à un Rebar.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar::CanFloat](#canfloat)|(Substitue [CBasePane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCReBar:: Create](#create)|Crée le contrôle rebar et l’attache à l' `CMFCReBar` objet.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Substitue [CBasePane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Fournit un accès direct au contrôle commun [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) sous-jacent.|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Substitue [CPane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Substitue [CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Substitue [CBasePane:: OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Substitue [CBasePane:: SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Notes

Un `CMFCReBar` objet peut contenir diverses fenêtres enfants. Cela comprend les zones d’édition, les barres d’outils et les zones de liste. Vous pouvez redimensionner le rebar par programme ou l’utilisateur peut redimensionner manuellement le rebar en faisant glisser sa barre de redimensionnement. Vous pouvez également définir l’arrière-plan d’un objet Rebar sur l’image bitmap de votre choix.

Un objet Rebar se comporte de la même façon qu’un objet Toolbar. Un contrôle rebar peut contenir une ou plusieurs bandes, et chaque bande peut contenir une barre de redimensionnement, une image bitmap, une étiquette de texte et une fenêtre enfant.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCReBar` . L’exemple montre comment créer un contrôle rebar et y ajouter une bande. La bande fonctionne comme une barre d’outils interne. Cet extrait de code fait partie de l' [exemple de test Rebar](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxRebar. h

##  <a name="addbar"></a>  CMFCReBar::AddBar

Ajoute une bande à un Rebar.

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

*pBar*<br/>
[in, out] Pointeur vers la fenêtre enfant qui doit être insérée dans le rebar. L’objet référencé doit avoir le style de fenêtre **WS_CHILD** .

*pszText*<br/>
dans Spécifie le texte à afficher sur le rebar. Le texte ne fait pas partie de la fenêtre enfant. Au lieu de cela, elle est affichée sur le rebar lui-même.

*pbmp*<br/>
[in, out] Spécifie l’image bitmap à afficher sur l’arrière-plan du Rebar.

*dwStyle*<br/>
dans Contient le style à appliquer à la bande. Pour obtenir la liste complète des styles de bande, consultez la `fStyle` Description de dans la structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) dans la documentation SDK Windows.

*clrFore*<br/>
dans Représente la couleur de premier plan du Rebar.

*clrBack*<br/>
dans Représente la couleur d’arrière-plan du Rebar.

### <a name="return-value"></a>Valeur de retour

TRUE si la bande a été correctement ajoutée au Rebar. Sinon, FALSe.

##  <a name="create"></a>  CMFCReBar::Create

Crée le contrôle rebar et l’attache à l’objet [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) .

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[in, out] Pointeur vers la fenêtre parente de ce contrôle rebar.

*dwCtrlStyle*<br/>
dans Spécifie le style du contrôle rebar. La valeur de style par défaut est **RBS_BANDBORDERS**, qui affiche des lignes étroites pour séparer les bandes adjacentes sur le contrôle rebar. Pour obtenir la liste des styles valides, consultez [styles de contrôle rebar](/windows/win32/Controls/rebar-control-styles) dans la documentation SDK Windows.

*dwStyle*<br/>
dans Style de fenêtre du contrôle rebar. Pour obtenir la liste des styles valides, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
dans ID de la fenêtre enfant du Rebar.

### <a name="return-value"></a>Valeur de retour

TRUE si le rebar a été créé avec succès; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl

Fournit un accès direct `CReBarCtrl` au contrôle commun sous- `CMFCReBar` jacent pour les objets.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à l’objet sous `CReBarCtrl` -jacent.

### <a name="remarks"></a>Notes

Appelez cette méthode pour tirer parti de la fonctionnalité de contrôle commun Windows Rebar lors de la personnalisation de votre Rebar.

##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

dans *bStretch*<br/>
dans *bHorz*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="canfloat"></a>  CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

[in] *dwDockStyle*<br/>

### <a name="remarks"></a>Notes

##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Paramètres

dans *CPoint*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Paramètres

dans *point*<br/>
dans *pTI*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

dans *pTarget*<br/>
dans *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Notes

##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

dans *dwAlignment*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl, classe](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane, classe](../../mfc/reference/cpane-class.md)
