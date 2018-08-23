---
title: Cdocksite, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d3af5911cac27a0ac2bb65e9ee0cdb7b714b41d
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540826"
---
# <a name="cdocksite-class"></a>CDockSite Class
Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
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
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Substitue [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|  
|[CDockSite::AdjustLayout](#adjustlayout)|(Substitue [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|  
|[CDockSite::AlignDockSite](#aligndocksite)||  
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CDockSite::CanAcceptPane](#canacceptpane)|(Substitue [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|  
|[CDockSite::CreateEx](#createex)|(Substitue [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|  
|[CDockSite::CreateRow](#createrow)||  
|[CDockSite::DockPane](#dockpane)|(Substitue [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|  
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Substitue [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CDockSite::FindRowIndex](#findrowindex)||  
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||  
|[CDockSite::GetDockSiteID](#getdocksiteid)||  
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||  
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Substitue `CBasePane::IsAccessibilityCompatible`.)|  
|[CDockSite::IsDragMode](#isdragmode)||  
|[CDockSite::IsLastRow](#islastrow)||  
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||  
|[CDockSite::IsResizable](#isresizable)|(Substitue [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|  
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
 L’infrastructure crée `CDockSite` automatiquement des objets lorsque vous appelez [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Les fenêtres du site d'ancrage sont positionnées à l'extrémité de la zone cliente de la fenêtre frame principale.  
  
 Généralement pas avoir à appeler les services fournis par le site d’ancrage car [cframewndex, classe](../../mfc/reference/cframewndex-class.md) gère ces services.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer un objet de la classe `CDockSite`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxDockSite.h  
  
##  <a name="addrow"></a>  CDockSite::AddRow  

  
```  
CDockingPanesRow* AddRow(
    POSITION pos,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pos*  
 [in] *nHeight*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout  

  
```  
virtual void AdjustDockingLayout();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout  

  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite  

  
```  
void AlignDockSite(
    const CRect& rectToAlignBy,  
    CRect& rectResult,  
    BOOL bMoveImmediately);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rectToAlignBy*  
 [in] *rectResult*  
 [in] *bMoveImmediately*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bStretch*  
 [in] *bHorz*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane  

  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pBar*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="createex"></a>  CDockSite::CreateEx  

  
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
 [in] *dwStyleEx*  
 [in] *dwStyle*  
 [in] *rect*  
 [in] *pParentWnd*  
 [in] *dwControlBarStyle*  
 [in] *pContext*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="createrow"></a>  CDockSite::CreateRow  

  
```  
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,  
    int nOffset,  
    int nRowHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pParentDockBar*  
 [in] *nOffset*  
 [in] *nRowHeight*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="dockpane"></a>  CDockSite::DockPane  

  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
 [in] *dockMethod*  
 [in] *lpRect*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf  
 Ancre un volet à gauche d'un autre volet.  
  
```  
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pBarToDock*  
 Un pointeur vers le volet pour être ancré à gauche de *pTargetBar*.  
  
 [in] [out] *pTargetBar*  
 Pointeur vers le volet cible.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet est ancré avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore  

  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="findpanebyid"></a>  CDockSite::FindPaneByID  
 Retourne le volet avec l’ID donné.  
  
```  
CPane* FindPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nID*  
 ID de commande du volet à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le volet avec l’ID de commande spécifié, ou NULL si le volet est introuvable.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="findrowindex"></a>  CDockSite::FindRowIndex  

  
```  
int FindRowIndex(CDockingPanesRow* pRow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pRow*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects  

  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID  

  
```  
virtual UINT GetDockSiteID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList  

  
```  
const CObList& GetDockSiteRowsList() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpanelist"></a>  CDockSite::GetPaneList  
 Retourne une liste de volets qui sont ancrées dans le site d’ancrage.  
  
```  
const CObList& GetPaneList() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence en lecture seule à la liste des volets est actuellement ancré dans la barre d’ancrage.  
  
##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible  

  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isdragmode"></a>  CDockSite::IsDragMode  

  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="islastrow"></a>  CDockSite::IsLastRow  

  
```  
bool IsLastRow(CDockingPanesRow* pRow) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pRow*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite  

  
```  
BOOL IsRectWithinDockSite(
    CRect rect,  
    CPoint& ptDelta);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
 [in] *ptDelta*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isresizable"></a>  CDockSite::IsResizable  

  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="movepane"></a>  CDockSite::MovePane  

  
```  
virtual BOOL MovePane(
    CPane* pWnd,  
    UINT nFlags,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
 [in] *nIndicateurs*  
 [in] *ptOffset*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow  

  
```  
virtual void OnInsertRow(POSITION pos);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pos*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow  

  
```  
virtual void OnRemoveRow(
    POSITION pos,  
    BOOL bByShow = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pos*  
 [in] *bByShow*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onresizerow"></a>  CDockSite::OnResizeRow  

  
```  
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,  
    int nOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pRowToResize*  
 [in] *nOffset*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onsizeparent"></a>  CDockSite::OnSizeParent  

  
```  
virtual void OnSizeParent(
    CRect& rectAvailable,  
    UINT nSide,  
    BOOL bExpand,  
    int nOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rectAvailable*  
 [in] *nSide*  
 [in] *bExpand*  
 [in] *nOffset*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos  

  
```  
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,  
    const CRect& rectWnd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndInsertAfter*  
 [in] *rectWnd*  
 [in] *nIndicateurs*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onshowrow"></a>  CDockSite::OnShowRow  

  
```  
virtual void OnShowRow(
    POSITION pos,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pos*  
 [in] *bShow*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint  
 Retourne un volet ancré dans le site d'ancrage au point spécifié par le paramètre donné.  
  
```  
virtual CPane* PaneFromPoint(CPoint pt);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pt*  
 Un point, en coordonnées d’écran, pour le volet à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le volet situé dans le point spécifié ou NULL si aucun volet n’était présent au point spécifié.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint  

  
```  
static int __stdcall RectSideFromPoint(
    const CRect& rect,  
    const CPoint& point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
 [in] *point*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="removepane"></a>  CDockSite::RemovePane  

  
```  
virtual void RemovePane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
 [in] *dockMethod*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="removerow"></a>  CDockSite::RemoveRow  

  
```  
void RemoveRow(CDockingPanesRow* pRow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pRow*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="replacepane"></a>  CDockSite::ReplacePane  

  
```  
BOOL ReplacePane(
    CPane* pOldBar,  
    CPane* pNewBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pOldBar*  
 [in] *pNewBar*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes  

  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rectNewClientArea*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite  

  
```  
void ResizeDockSite(
    int nNewWidth,  
    int nNewHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nNewWidth*  
 [in] *nNewHeight*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="resizerow"></a>  CDockSite::ResizeRow  

  
```  
int ResizeRow(
    CDockingPanesRow* pRow,  
    int nNewSize,  
    BOOL bAdjustLayout = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pRow*  
 [in] *nNewSize*  
 [in] *bAdjustLayout*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="showpane"></a>  CDockSite::ShowPane  
 Affiche le volet.  
  
```  
virtual BOOL ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pBar*  
 Un pointeur vers le volet pour être affichée ou masquée.  
  
 [in] *bShow*  
 TRUE pour spécifier que le volet doit être affichée ; FALSE pour indiquer que le volet doit être masqué.  
  
 [in] *bDelay*  
 TRUE pour spécifier que la disposition du volet doit être différée jusqu'à une fois que le volet est affiché ; Sinon, FALSE.  
  
 [in] *bActivate*  
 Ce paramètre n'est pas utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet a été affiché ou masqué avec succès. FALSE si le volet spécifié n’appartient pas à ce site d’ancrage.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour afficher ou masquer des volets ancrés. Normalement, vous n’avez pas à appeler `CDockSite::ShowPane` directement, car elle est appelée par la fenêtre frame parente ou par le volet de base.  
  
##  <a name="showrow"></a>  CDockSite::ShowRow  

  
```  
void ShowRow(
    CDockingPanesRow* pRow,  
    BOOL bShow,  
    BOOL bAdjustLayout);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pRow*  
 [in] *bShow*  
 [in] *bAdjustLayout*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="swaprows"></a>  CDockSite::SwapRows  

  
```  
void SwapRows(
    CDockingPanesRow* pFirstRow,  
    CDockingPanesRow* pSecondRow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pFirstRow*  
 [in] *pSecondRow*  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CBasePane, classe](../../mfc/reference/cbasepane-class.md)
