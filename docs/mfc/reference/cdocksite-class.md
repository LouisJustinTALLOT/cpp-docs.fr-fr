---
title: CDockSite Class
ms.date: 10/18/2018
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
ms.openlocfilehash: 471d68ead1bc5a11ace29f572647c4a7f2406b4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753273"
---
# <a name="cdocksite-class"></a>CDockSite Class

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

Fournit les fonctionnalités de réorganisation des volets dérivés de [CPane Class](../../mfc/reference/cpane-class.md) en ensembles de lignes.

## <a name="syntax"></a>Syntaxe

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Overrides [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Overrides [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Overrides [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Overrides [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Overrides [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Overrides [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Overrides [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Substitue `CBasePane::IsAccessibilityCompatible`.)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Overrides [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Retourne un volet ancré dans le site d'ancrage au point spécifié par le paramètre donné.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Ancre un volet à gauche d'un autre volet.|
|[CDockSite::FindPaneByID](#findpanebyid)|Retourne le volet identifié par l'ID donné.|
|[CDockSite::GetPaneList](#getpanelist)|Retourne la liste des volets ancrés sur le site d'ancrage.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|Affiche le volet.|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Notes

Le cadre `CDockSite` crée automatiquement des objets lorsque vous appelez [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Les fenêtres du site d'ancrage sont positionnées à l'extrémité de la zone cliente de la fenêtre frame principale.

Vous n’avez généralement pas à appeler les services fournis par le site du quai parce que [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md) gère ces services.

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet de la classe `CDockSite`.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxDockSite.h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a>CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

[dans] *pos*<br/>

[dans] *nHeight (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Notes

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a>CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Notes

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a>CDockSite::AlignDockSite

```cpp
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Paramètres

[dans] *rectToAlignBy*<br/>

[dans] *rectResult*<br/>

[dans] *bMoveImmédiment*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockSite::CalcFixedLayout

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

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a>CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitecreateex"></a><a name="createex"></a>CDockSite::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

[dans] *dwStyleEx*<br/>

[dans] *dwStyle (en)*<br/>

[dans] *rect*<br/>

[dans] *pParentWnd*<br/>

[dans] *dwControlBarStyle (en)*<br/>

[dans] *pContexte*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitecreaterow"></a><a name="createrow"></a>CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Paramètres

[dans] *pParentDockBar*<br/>

[dans] *nOffset (en anglais)*<br/>

[dans] *nRowHeight*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitedockpane"></a><a name="dockpane"></a>CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

[dans] *pWnd (pWnd)*<br/>

[dans] *dockMethod*<br/>

[dans] *lpRect*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a>CDockSite::DockPaneLeftOf

Ancre un volet à gauche d'un autre volet.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Paramètres

*pBarToDock*<br/>
[dans, dehors] Un pointeur à la vitre à amarré à gauche de *pTargetBar*.

*pTargetBar*<br/>
[dans, dehors] Un pointeur à la vitre cible.

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre est amarré avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a>CDockSite::FindPaneByID

Retourne la vitre avec l’ID donné.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] L’id de commande de la vitre à trouver.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la vitre avec l’ID de commande spécifié, ou NULL si le volet n’est pas trouvé.

### <a name="remarks"></a>Notes

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a>CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Paramètres

[dans] *pRow (pRow)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Notes

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a>CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a>CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a>CDockSite::GetPaneList

Retourne une liste de vitres qui sont amarrés dans le site du quai.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à la liste des vitres actuellement amarrés dans la barre d’amarrage.

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a>CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a>CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Paramètres

[dans] *pRow (pRow)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a>CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Paramètres

[dans] *rect*<br/>

[dans] *ptDelta*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a>CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksitemovepane"></a><a name="movepane"></a>CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Paramètres

[dans] *pWnd (pWnd)*<br/>

[dans] *nFlags*<br/>

[dans] *ptOffset (en anglais)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a>CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Paramètres

[dans] *pos*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a>CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Paramètres

[dans] *pos*<br/>

[dans] *bByShow (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a>CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Paramètres

[dans] *pRowToResize*<br/>

[dans] *nOffset (en anglais)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a>CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Paramètres

[dans] *rectavailable*<br/>

[dans] *nSide*<br/>

[dans] *bExpand (en anglais)*<br/>

[dans] *nOffset (en anglais)*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a>CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

[dans] *pWndInsertAprès*<br/>

[dans] *rectWnd*<br/>

[dans] *nFlags*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a>CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

[dans] *pos*<br/>

[dans] *bShow (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a>CDockSite::Pandepoint

Retourne un volet ancré dans le site d'ancrage au point spécifié par le paramètre donné.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
[dans] Un point, dans les coordonnées de l’écran, pour que la vitre récupère.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la vitre située au point spécifié ou NULL si aucune vitre n’était présente au point spécifié.

### <a name="remarks"></a>Notes

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a>CDockSite::RectSideDePoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Paramètres

[dans] *rect*<br/>

[dans] *point*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteremovepane"></a><a name="removepane"></a>CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

[dans] *pWnd (pWnd)*<br/>

[dans] *dockMethod*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteremoverow"></a><a name="removerow"></a>CDockSite::RemoveRow

```cpp
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Paramètres

[dans] *pRow (pRow)*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a>CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pOldBar (en)*<br/>

[dans] *pNewBar (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a>CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Paramètres

[dans] *rectNewClientArea*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a>CDockSite::ResizeDockSite

```cpp
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Paramètres

[dans] *nNewWidth (en)*<br/>

[dans] *nNewHeight*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a>CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *pRow (pRow)*<br/>

[dans] *nNewSize (en)*<br/>

[dans] *bAdjustLayout (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cdocksiteshowpane"></a><a name="showpane"></a>CDockSite::ShowPane

Affiche le volet.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans, dehors] Un pointeur à la vitre à montrer ou à cacher.

*bShow (en)*<br/>
[dans] VRAI pour spécifier que la vitre doit être montrée; FALSE pour spécifier que la vitre doit être cachée.

*bDelay (en)*<br/>
[dans] VRAI pour spécifier que la disposition de la vitre doit être retardée jusqu’à ce que la vitre soit montrée; autrement, FALSE.

*bActivate (en)*<br/>
[dans] Ce paramètre n’est pas utilisé.

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre a été montrée ou cachée avec succès. FALSE si le volet spécifié n’appartient pas à ce site de quai.

### <a name="remarks"></a>Notes

Appelez cette méthode pour montrer ou cacher les vitres amarrés. Normalement, vous n’avez `CDockSite::ShowPane` pas à appeler directement, parce qu’il est appelé par la fenêtre du cadre parent ou par la vitre de base.

## <a name="cdocksiteshowrow"></a><a name="showrow"></a>CDockSite::ShowRow

```cpp
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Paramètres

[dans] *pRow (pRow)*<br/>

[dans] *bShow (en)*<br/>

[dans] *bAdjustLayout (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a>CDockSite::SwapRows

```cpp
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Paramètres

[dans] *pFirstRow (en)*<br/>

[dans] *pSecondRow*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CBasePane](../../mfc/reference/cbasepane-class.md)
