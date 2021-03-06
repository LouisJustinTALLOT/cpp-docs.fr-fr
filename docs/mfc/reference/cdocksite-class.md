---
description: 'En savoir plus sur : classe CDockSite'
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
ms.openlocfilehash: e8d56ed3d343f68215f6c1f053cd045cf37fe064
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184996"
---
# <a name="cdocksite-class"></a>CDockSite Class

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

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
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Substitue [CBasePane :: AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Substitue [CBasePane :: AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane :: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Substitue [CBasePane :: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Substitue [CBasePane :: CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Substitue [CBasePane ::D ockpane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Substitue [CBasePane ::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Substitue `CBasePane::IsAccessibilityCompatible`.)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Substitue [CBasePane :: IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Retourne un volet ancré dans le site d'ancrage au point spécifié par le paramètre donné.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Ancre un volet à gauche d'un autre volet.|
|[CDockSite :: FindPaneByID](#findpanebyid)|Retourne le volet identifié par l'ID donné.|
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

L’infrastructure crée `CDockSite` automatiquement des objets quand vous appelez [CFrameWndEx :: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Les fenêtres du site d'ancrage sont positionnées à l'extrémité de la zone cliente de la fenêtre frame principale.

En règle générale, il n’est pas nécessaire d’appeler les services fournis par le site Dock, car la [classe CFrameWndEx](../../mfc/reference/cframewndex-class.md) gère ces services.

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet de la classe `CDockSite`.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDockSite. h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a> CDockSite :: AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

dans *pos*<br/>

dans *nHeight*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a> CDockSite :: AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Notes

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a> CDockSite :: AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Notes

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a> CDockSite :: AlignDockSite

```cpp
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Paramètres

dans *rectToAlignBy*<br/>

dans *rectResult*<br/>

dans *bMoveImmediately*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a> CDockSite :: CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

dans *bStretch*<br/>

dans *bHorz*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a> CDockSite :: CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitecreateex"></a><a name="createex"></a> CDockSite :: CreateEx

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

dans *dwStyleEx*<br/>

dans *dwStyle*<br/>

dans *Rect*<br/>

dans *pParentWnd*<br/>

dans *dwControlBarStyle*<br/>

dans *pContext*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitecreaterow"></a><a name="createrow"></a> CDockSite :: CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Paramètres

dans *pParentDockBar*<br/>

dans *nOffset*<br/>

dans *nRowHeight*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitedockpane"></a><a name="dockpane"></a> CDockSite ::D ockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

dans *pwnd*<br/>

dans *dockMethod*<br/>

dans *lpRect*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a> CDockSite ::D ockPaneLeftOf

Ancre un volet à gauche d'un autre volet.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Paramètres

*pBarToDock*<br/>
[in, out] Pointeur vers le volet à ancrer à gauche de *pTargetBar*.

*pTargetBar*<br/>
[in, out] Pointeur vers le volet cible.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le volet est correctement ancré ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CDockSite ::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a> CDockSite :: FindPaneByID

Retourne le volet avec l’ID donné.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans ID de commande du volet à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le volet avec l’ID de commande spécifié, ou NULL si le volet est introuvable.

### <a name="remarks"></a>Notes

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a> CDockSite :: FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Paramètres

dans *Prow*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a> CDockSite :: FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Notes

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a> CDockSite :: GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a> CDockSite :: GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a> CDockSite :: GetPaneList

Retourne la liste des volets qui sont ancrés dans le site d’ancrage.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence en lecture seule à la liste des volets actuellement ancrées dans la barre d’ancrage.

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a> CDockSite :: IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a> CDockSite :: IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a> CDockSite :: IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Paramètres

dans *Prow*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a> CDockSite :: IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

dans *ptDelta*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a> CDockSite :: IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksitemovepane"></a><a name="movepane"></a> CDockSite :: MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Paramètres

dans *pwnd*<br/>

dans *nFlags*<br/>

dans *ptOffset*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a> CDockSite :: OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Paramètres

dans *pos*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a> CDockSite :: OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Paramètres

dans *pos*<br/>

dans *bByShow*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a> CDockSite :: OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Paramètres

dans *pRowToResize*<br/>

dans *nOffset*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a> CDockSite :: OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Paramètres

dans *rectAvailable*<br/>

dans *nSide*<br/>

dans à *développer*<br/>

dans *nOffset*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a> CDockSite :: OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

dans *pWndInsertAfter*<br/>

dans *rectWnd*<br/>

dans *nFlags*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a> CDockSite :: OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

dans *pos*<br/>

dans *bShow*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a> CDockSite ::P aneFromPoint

Retourne un volet ancré dans le site d'ancrage au point spécifié par le paramètre donné.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
dans Point, en coordonnées d’écran, du volet à récupérer.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le volet situé au point spécifié ou NULL si aucun volet n’était présent au point spécifié.

### <a name="remarks"></a>Notes

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a> CDockSite :: RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

dans *point*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteremovepane"></a><a name="removepane"></a> CDockSite :: RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

dans *pwnd*<br/>

dans *dockMethod*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteremoverow"></a><a name="removerow"></a> CDockSite :: RemoveRow

```cpp
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Paramètres

dans *Prow*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a> CDockSite :: ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Paramètres

dans *pOldBar*<br/>

dans *pNewBar*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a> CDockSite :: RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Paramètres

dans *rectNewClientArea*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a> CDockSite :: ResizeDockSite

```cpp
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Paramètres

dans *nNewWidth*<br/>

dans *nNewHeight*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a> CDockSite :: ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *Prow*<br/>

dans *nNewSize*<br/>

dans *bAdjustLayout*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdocksiteshowpane"></a><a name="showpane"></a> CDockSite :: ShowPane

Affiche le volet.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in, out] Pointeur vers le volet à afficher ou à masquer.

*bShow*<br/>
dans TRUE pour spécifier que le volet doit être affiché. FALSe pour spécifier que le volet doit être masqué.

*bDelay*<br/>
dans TRUE pour spécifier que la disposition du volet doit être retardée jusqu’à ce que le volet soit affiché ; Sinon, FALSe.

*bActivate*<br/>
dans Ce paramètre n’est pas utilisé.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le volet a été affiché ou masqué avec succès. FALSe si le volet spécifié n’appartient pas à ce site d’ancrage.

### <a name="remarks"></a>Notes

Appelez cette méthode pour afficher ou masquer les volets ancrés. Normalement, il n’est pas nécessaire d’appeler `CDockSite::ShowPane` directement, car il est appelé par la fenêtre frame parente ou par le volet de base.

## <a name="cdocksiteshowrow"></a><a name="showrow"></a> CDockSite :: ShowRow

```cpp
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Paramètres

dans *Prow*<br/>

dans *bShow*<br/>

dans *bAdjustLayout*<br/>

### <a name="remarks"></a>Notes

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a> CDockSite :: SwapRows

```cpp
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Paramètres

dans *pFirstRow*<br/>

dans *pSecondRow*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane, classe](../../mfc/reference/cbasepane-class.md)
