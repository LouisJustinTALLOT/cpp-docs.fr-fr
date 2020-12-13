---
description: 'En savoir plus sur : classe CDockingPanesRow'
title: CDockingPanesRow, classe
ms.date: 10/18/2018
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
ms.openlocfilehash: bf031b19c25cde36705333feb3baa3af9e1932ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185009"
---
# <a name="cdockingpanesrow-class"></a>CDockingPanesRow, classe

Gère une liste de volets qui se trouvent sur la même ligne horizontale ou verticale (colonne) d'un site d'ancrage.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CDockingPanesRow : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CDockingPanesRow::CDockingPanesRow`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockingPanesRow::AddPane](#addpane)||
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||
|[CDockingPanesRow::ArrangePanes](#arrangepanes)|Dispose les volets dans une ligne en fonction des paramètres de marge et d'espacement spécifiés.|
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||
|[CDockingPanesRow::Create](#create)||
|[CDockingPanesRow::ExpandStretchedPanes](#expandstretchedpanes)||
|[CDockingPanesRow::ExpandStretchedPanesRect](#expandstretchedpanesrect)||
|[CDockingPanesRow::FixupVirtualRects](#fixupvirtualrects)||
|[CDockingPanesRow::GetAvailableLength](#getavailablelength)||
|[CDockingPanesRow::GetAvailableSpace](#getavailablespace)||
|[CDockingPanesRow::GetClientRect](#getclientrect)||
|[CDockingPanesRow::GetDockSite](#getdocksite)||
|[CDockingPanesRow::GetExtraSpace](#getextraspace)||
|[CDockingPanesRow::GetGroupFromPane](#getgroupfrompane)||
|[CDockingPanesRow::GetID](#getid)||
|[CDockingPanesRow::GetMaxPaneSize](#getmaxpanesize)||
|[CDockingPanesRow::GetPaneCount](#getpanecount)||
|[CDockingPanesRow::GetPaneList](#getpanelist)||
|[CDockingPanesRow::GetRowAlignment](#getrowalignment)||
|[CDockingPanesRow::GetRowHeight](#getrowheight)||
|[CDockingPanesRow::GetRowOffset](#getrowoffset)||
|[CDockingPanesRow::GetVisibleCount](#getvisiblecount)||
|[CDockingPanesRow::GetWindowRect](#getwindowrect)||
|[CDockingPanesRow::HasPane](#haspane)||
|[CDockingPanesRow::IsEmpty](#isempty)||
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||
|[CDockingPanesRow::IsHorizontal](#ishorizontal)||
|[CDockingPanesRow::IsVisible](#isvisible)||
|[CDockingPanesRow::Move](#move)||
|[CDockingPanesRow::MovePane](#movepane)||
|[CDockingPanesRow::OnResizePane](#onresizepane)||
|[CDockingPanesRow::RedrawAll](#redrawall)||
|[CDockingPanesRow::RemovePane](#removepane)||
|[CDockingPanesRow::ReplacePane](#replacepane)||
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||
|[CDockingPanesRow::Resize](#resize)||
|[CDockingPanesRow::ResizeByPaneDivider](#resizebypanedivider)||
|[CDockingPanesRow::ScreenToClient](#screentoclient)||
|[CDockingPanesRow::SetExtra](#setextra)||
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||
|[CDockingPanesRow::ShowPane](#showpane)||
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||

## <a name="remarks"></a>Notes

Les objets `CDockingPanesRow` sont créés en interne par des objets de site d'ancrage.

## <a name="example"></a>Exemple

L'exemple suivant montre comment obtenir un objet `CDockingPanesRow` à partir d'un objet `CMFCAutoHideBar`.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDockingPanesRow. h

## <a name="cdockingpanesrowaddpane"></a><a name="addpane"></a> CDockingPanesRow::AddPane

```
virtual void AddPane(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL,
    BOOL bAddLast = FALSE);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

dans *dockMethod*<br/>

dans *lpRect*<br/>

dans *bAddLast*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowaddpanefromrow"></a><a name="addpanefromrow"></a> CDockingPanesRow::AddPaneFromRow

```
virtual void AddPaneFromRow(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

dans *dockMethod*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowarrangepanes"></a><a name="arrangepanes"></a> CDockingPanesRow::ArrangePanes

Organise les volets d’ancrage d’une ligne en fonction des paramètres de marge et d’espacement spécifiés.

```
virtual void ArrangePanes(
    int nMargin,
    int nSpacing);
```

### <a name="parameters"></a>Paramètres

*nMargin*<br/>
dans Spécifie le décalage, en pixels, du premier volet à partir du coin supérieur gauche de la ligne.

*nSpacing*<br/>
dans Spécifie l’espacement, en pixels, entre les volets.

### <a name="remarks"></a>Notes

Appelez cette méthode pour organiser les volets dans la ligne où ils seront ancrés. Après avoir appelé cette méthode, vous devez appeler `CDockingPanesRow::FixupVirtualRects(FALSE, NULL)` .

## <a name="cdockingpanesrowcalcfixedlayout"></a><a name="calcfixedlayout"></a> CDockingPanesRow::CalcFixedLayout

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

## <a name="cdockingpanesrowcdockingpanesrow"></a><a name="cdockingpanesrow"></a> CDockingPanesRow::CDockingPanesRow

```
CDockingPanesRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

dans *pParentDockBar*<br/>

dans *nOffset*<br/>

dans *nHeight*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowcreate"></a><a name="create"></a> CDockingPanesRow :: Create

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowexpandstretchedpanes"></a><a name="expandstretchedpanes"></a> CDockingPanesRow::ExpandStretchedPanes

```cpp
void ExpandStretchedPanes();
```

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowexpandstretchedpanesrect"></a><a name="expandstretchedpanesrect"></a> CDockingPanesRow::ExpandStretchedPanesRect

```cpp
void ExpandStretchedPanesRect();
```

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowfixupvirtualrects"></a><a name="fixupvirtualrects"></a> CDockingPanesRow::FixupVirtualRects

```cpp
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,
    CPane* pBarToExclude = NULL);
```

### <a name="parameters"></a>Paramètres

dans *bMoveBackToVirtualRect*<br/>

dans *pBarToExclude*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetavailablelength"></a><a name="getavailablelength"></a> CDockingPanesRow::GetAvailableLength

```
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;
```

### <a name="parameters"></a>Paramètres

dans *bUseVirtualRect*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetavailablespace"></a><a name="getavailablespace"></a> CDockingPanesRow::GetAvailableSpace

```
virtual void GetAvailableSpace(CRect& rect);
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetclientrect"></a><a name="getclientrect"></a> CDockingPanesRow::GetClientRect

```cpp
void GetClientRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetdocksite"></a><a name="getdocksite"></a> CDockingPanesRow::GetDockSite

```
CDockSite* GetDockSite() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetextraspace"></a><a name="getextraspace"></a> CDockingPanesRow::GetExtraSpace

```
int GetExtraSpace() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetgroupfrompane"></a><a name="getgroupfrompane"></a> CDockingPanesRow::GetGroupFromPane

```cpp
void GetGroupFromPane(
    CPane* pBar,
    CObList& lst);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

dans *LST*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetid"></a><a name="getid"></a> CDockingPanesRow :: GetID

```
int GetID() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetmaxpanesize"></a><a name="getmaxpanesize"></a> CDockingPanesRow::GetMaxPaneSize

```
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;
```

### <a name="parameters"></a>Paramètres

dans *bSkipHiddenBars*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetpanecount"></a><a name="getpanecount"></a> CDockingPanesRow::GetPaneCount

```
int GetPaneCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetpanelist"></a><a name="getpanelist"></a> CDockingPanesRow::GetPaneList

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetrowalignment"></a><a name="getrowalignment"></a> CDockingPanesRow::GetRowAlignment

```
DWORD GetRowAlignment() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetrowheight"></a><a name="getrowheight"></a> CDockingPanesRow::GetRowHeight

```
int GetRowHeight() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetrowoffset"></a><a name="getrowoffset"></a> CDockingPanesRow::GetRowOffset

```
int GetRowOffset() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetvisiblecount"></a><a name="getvisiblecount"></a> CDockingPanesRow::GetVisibleCount

```
virtual int GetVisibleCount();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowgetwindowrect"></a><a name="getwindowrect"></a> CDockingPanesRow :: GetWindowRect

```cpp
void GetWindowRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowhaspane"></a><a name="haspane"></a> CDockingPanesRow::HasPane

```
BOOL HasPane(CBasePane* pControlBar);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowisempty"></a><a name="isempty"></a> CDockingPanesRow :: IsEmpty

```
virtual BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowisexclusiverow"></a><a name="isexclusiverow"></a> CDockingPanesRow::IsExclusiveRow

```
virtual BOOL IsExclusiveRow() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowishorizontal"></a><a name="ishorizontal"></a> CDockingPanesRow::IsHorizontal

```
bool IsHorizontal() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowisvisible"></a><a name="isvisible"></a> CDockingPanesRow :: IsVisible

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowmove"></a><a name="move"></a> CDockingPanesRow :: Move

```
virtual void Move(int nOffset);
```

### <a name="parameters"></a>Paramètres

dans *nOffset*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowmovepane"></a><a name="movepane"></a> CDockingPanesRow::MovePane

```cpp
void MovePane(
    CPane* pControlBar,
    CPoint ptOffset,
    BOOL bSwapControlBars,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    CRect rectTarget,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nOffset,
    bool bForward,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nAbsolutOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

dans *ptOffset*<br/>

dans *bSwapControlBars*<br/>

dans *hdwp*<br/>

dans *rectTarget*<br/>

dans *nOffset*<br/>

dans *bForward*<br/>

dans *nAbsolutOffset*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowonresizepane"></a><a name="onresizepane"></a> CDockingPanesRow::OnResizePane

```
virtual void OnResizePane(CBasePane* pControlBar);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowredrawall"></a><a name="redrawall"></a> CDockingPanesRow::RedrawAll

```cpp
void RedrawAll();
```

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowremovepane"></a><a name="removepane"></a> CDockingPanesRow::RemovePane

```
virtual void RemovePane(CPane* pControlBar);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowreplacepane"></a><a name="replacepane"></a> CDockingPanesRow::ReplacePane

```
virtual BOOL ReplacePane(
    CPane* pBarOld,
    CPane* pBarNew);
```

### <a name="parameters"></a>Paramètres

dans *pBarOld*<br/>

dans *pBarNew*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowrepositionpanes"></a><a name="repositionpanes"></a> CDockingPanesRow::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,
    UINT nSide = (UINT)-1,
    BOOL bExpand = FALSE,
    int nOffset = 0);
```

### <a name="parameters"></a>Paramètres

dans *rectNewParentBarArea*<br/>

dans *nSide*<br/>

dans à *développer*<br/>

dans *nOffset*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowresize"></a><a name="resize"></a> CDockingPanesRow :: Resize

```
virtual int Resize(int nOffset);
```

### <a name="parameters"></a>Paramètres

dans *nOffset*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowresizebypanedivider"></a><a name="resizebypanedivider"></a> CDockingPanesRow::ResizeByPaneDivider

```
virtual int ResizeByPaneDivider(int /*ignored*/);
```

### <a name="parameters"></a>Paramètres

dans *ignoré*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowscreentoclient"></a><a name="screentoclient"></a> CDockingPanesRow::ScreenToClient

```cpp
void ScreenToClient(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowsetextra"></a><a name="setextra"></a> CDockingPanesRow::SetExtra

```cpp
void SetExtra(
    int nExtraSpace,
    AFX_ROW_ALIGNMENT rowExtraAlign);
```

### <a name="parameters"></a>Paramètres

dans *nExtraSpace*<br/>

dans *rowExtraAlign*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowshowdocksiterow"></a><a name="showdocksiterow"></a> CDockingPanesRow::ShowDockSiteRow

```
virtual void ShowDockSiteRow(
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Paramètres

dans *bShow*<br/>

dans *bDelay*<br/>

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowshowpane"></a><a name="showpane"></a> CDockingPanesRow :: ShowPane

```
virtual BOOL ShowPane(
    CPane* pControlBar,
    BOOL bShow,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Paramètres

dans *pControlBar*<br/>

dans *bShow*<br/>

dans *bDelay*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cdockingpanesrowupdatevisiblestate"></a><a name="updatevisiblestate"></a> CDockingPanesRow::UpdateVisibleState

```
virtual void UpdateVisibleState(BOOL bDelay);
```

### <a name="parameters"></a>Paramètres

dans *bDelay*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[CDockSite, classe](../../mfc/reference/cdocksite-class.md)<br/>
[CPane, classe](../../mfc/reference/cpane-class.md)
