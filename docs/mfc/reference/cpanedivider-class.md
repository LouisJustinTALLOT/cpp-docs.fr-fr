---
title: Cpanedivider, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
dev_langs:
- C++
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b51eccb4c76a3888eaa9e46faccdf00d3c2ade39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441770"
---
# <a name="cpanedivider-class"></a>Cpanedivider, classe

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

Le `CPaneDivider` classe divise deux volets, divise deux groupes de volets ou sépare un groupe de volets de la zone cliente de la fenêtre frame principale.

## <a name="syntax"></a>Syntaxe

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Substitue [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Substitue [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Substitue [CBasePane::IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Substitue [CBasePane::IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
|[CPaneDivider::Move](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider::Serialize](#serialize)|(Substitue `CBasePane::Serialize`.)|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider::ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Retourne la liste des volets qui se trouvent dans le [cpanecontainer, classe](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Retourne la liste de diviseurs de volet qui résident dans le [cpanecontainer, classe](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Spécifie la largeur par défaut en pixels de tous les diviseurs de volet dans l’application.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Contient un pointeur vers les informations de classe runtime concernant un `CPaneDivider`-objet dérivé.|

## <a name="remarks"></a>Notes

L’infrastructure crée `CPaneDivider` objets automatiquement lorsqu’un volet est ancré.

Il existe deux types de diviseurs de volet :

- un diviseur de volet par défaut est créé lorsqu’un groupe de volets est ancré à un côté de la fenêtre frame principale. Le diviseur de volet par défaut conserve un pointeur vers le [cpanecontainermanager, classe](../../mfc/reference/cpanecontainermanager-class.md) et redirige la plupart des opérations sur le groupe de volets (telles que le redimensionnement d’un volet ou d’ancrage d’un autre volet ou conteneur) pour le Gestionnaire de conteneur. Chaque volet d’ancrage conserve un pointeur vers son diviseur de volet par défaut.

- Un diviseur de volet régulière divise juste deux volets dans un conteneur. Pour plus d’informations, consultez [cpanecontainer, classe](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment obtenir un objet `CPaneDivider` à partir d'un objet `CWorkspaceBar`. Cet extrait de code fait partie de la [exemple de démonstration des onglets MDI](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxPaneDivider.h

##  <a name="setautohidemode"></a>  CPaneDivider::SetAutoHideMode


```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Paramètres

[in] *bMode*

### <a name="remarks"></a>Notes

##  <a name="setpanecontainermanager"></a>  CPaneDivider::SetPaneContainerManager


```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Paramètres

[in] *p*

### <a name="remarks"></a>Notes

##  <a name="addpane"></a>  CPaneDivider::AddPane


```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

[in] *pBar*

### <a name="remarks"></a>Notes

##  <a name="addpanecontainer"></a>  CPaneDivider::AddPaneContainer


```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);


virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

*barContainerManager*<br/>
[in] [in] *bOuterEdge*
*pTargetBar*<br/>
[in] [in] *dwAlignment*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="addrecentpane"></a>  CPaneDivider::AddRecentPane


```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

[in] *pBar*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="calcexpecteddockedrect"></a>  CPaneDivider::CalcExpectedDockedRect


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
[in] [in] *ptMouse*
*rectResult*<br/>
[in] [in] *bDrawTab* [in] *ppTargetBar*

### <a name="remarks"></a>Notes

##  <a name="calcfixedlayout"></a>  CPaneDivider::CalcFixedLayout


```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*bStretch*<br/>
[in] [in] *bHorz*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="checkvisibility"></a>  CPaneDivider::CheckVisibility


```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="cpanedivider"></a>  CPaneDivider::CPaneDivider


```
CPaneDivider();


CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Paramètres

*bDefaultSlider*<br/>
[in] [in] *pParent*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="createex"></a>  CPaneDivider::CreateEx


```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Paramètres

*dwStyleEx*<br/>
[in] [in] *dwStyle*
*rect*<br/>
[in] [in] *pParentWnd*
*nID*<br/>
[in] [in] *pContext*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="doesallowdyninsertbefore"></a>  CPaneDivider::DoesAllowDynInsertBefore


```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="doescontainfloatingpane"></a>  CPaneDivider::DoesContainFloatingPane


```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="findpanecontainer"></a>  CPaneDivider::FindPaneContainer


```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] [in] *bLeftBar*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="findtabbedpane"></a>  CPaneDivider::FindTabbedPane


```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Paramètres

[in] *nID*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getdefaultwidth"></a>  CPaneDivider::GetDefaultWidth


```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getfirstpane"></a>  CPaneDivider::GetFirstPane


```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getpanedividers"></a>  CPaneDivider::GetPaneDividers

Retourne la liste de diviseurs de volet qui résident dans le [cpanecontainer, classe](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut.

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Paramètres

*lstSliders*<br/>
[out] Contient la liste de diviseurs de volet qui résident dans le conteneur de volet.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour diviseurs de volet par défaut uniquement. Un diviseur de volet par défaut est un séparateur qui redimensionne le conteneur de volet entière.

##  <a name="getpanedividerstyle"></a>  CPaneDivider::GetPaneDividerStyle


```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getpanes"></a>  CPaneDivider::GetPanes

Retourne la liste des volets qui se trouvent dans le [cpanecontainer, classe](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour récupérer des diviseurs de volet par défaut.

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Paramètres

*lstBars*<br/>
[out] Contient la liste des volets qui se trouvent dans le conteneur de volet.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour diviseurs de volet par défaut uniquement. Un diviseur de volet par défaut est un séparateur qui redimensionne le conteneur de volet entière.

##  <a name="getrootcontainerrect"></a>  CPaneDivider::GetRootContainerRect


```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getwidth"></a>  CPaneDivider::GetWidth


```
int GetWidth() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="init"></a>  CPaneDivider::Init


```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Paramètres

*bDefaultSlider*<br/>
[in] [in] *pParent*

### <a name="remarks"></a>Notes

##  <a name="insertpane"></a>  CPaneDivider::InsertPane


```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBarToInsert*<br/>
[in] [in] *pTargetBar*
*dwAlignment*<br/>
[in] [in] *lpRect*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isautohidemode"></a>  CPaneDivider::IsAutoHideMode


```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isdefault"></a>  CPaneDivider::IsDefault


```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ishorizontal"></a>  CPaneDivider::IsHorizontal


```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="m_ndefaultwidth"></a>  CPaneDivider::m_nDefaultWidth

Spécifie la largeur par défaut, en pixels, de tous les diviseurs de volet dans l’application.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

##  <a name="move"></a>  CPaneDivider::Move


```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Paramètres

*ptOffset*<br/>
[in] [in] *bAdjustLayout*

### <a name="remarks"></a>Notes

##  <a name="m_psliderrtc"></a>  CPaneDivider::m_pSliderRTC

Contient un pointeur vers les informations de classe runtime concernant un `CPaneDivider`-objet dérivé.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Notes

Définissez cette variable de membre si vous créez un diviseur de volet personnalisé. Ainsi, l’infrastructure pour créer votre diviseur de volet lorsque le volet est dessiné.

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir le `m_pSliderRTC` variable membre :

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

##  <a name="notifyaboutrelease"></a>  CPaneDivider::NotifyAboutRelease


```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Notes

##  <a name="onshowpane"></a>  CPaneDivider::OnShowPane


```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] [in] *bShow*

### <a name="remarks"></a>Notes

##  <a name="releaseemptypanecontainers"></a>  CPaneDivider::ReleaseEmptyPaneContainers


```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Notes

##  <a name="removepane"></a>  CPaneDivider::RemovePane


```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

[in] *pBar*

### <a name="remarks"></a>Notes

##  <a name="replacepane"></a>  CPaneDivider::ReplacePane


```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Paramètres

*pBarToReplace*<br/>
[in] [in] *pBarToReplaceWith*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="repositionpanes"></a>  CPaneDivider::RepositionPanes


```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Paramètres

*rectNew*<br/>
[in] [in] *hdwp*

### <a name="remarks"></a>Notes

##  <a name="serialize"></a>  CPaneDivider::Serialize


```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

[in] *ar*

### <a name="remarks"></a>Notes

##  <a name="showwindow"></a>  CPaneDivider::ShowWindow


```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Paramètres

[in] *nCmdShow*

### <a name="remarks"></a>Notes

##  <a name="storerecentdocksiteinfo"></a>  CPaneDivider::StoreRecentDockSiteInfo


```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

[in] *pBar*

### <a name="remarks"></a>Notes

##  <a name="storerecenttabrelatedinfo"></a>  CPaneDivider::StoreRecentTabRelatedInfo


```
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Paramètres

*pDockingBar*<br/>
[in] [in] *pTabbedBar*

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPaneContainerManager, classe](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer, classe](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager, classe](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane, classe](../../mfc/reference/cbasepane-class.md)
