---
description: 'En savoir plus sur : classe CPaneDivider'
title: CPaneDivider, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: f2541483f7881ab0b303750e69af776c2c3bc7a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301514"
---
# <a name="cpanedivider-class"></a>CPaneDivider, classe

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

La `CPaneDivider` classe divise deux volets, divise deux groupes de volets ou sépare un groupe de volets de la zone cliente de la fenêtre frame principale.

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
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane :: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider :: CreateEx](#createex)|(Substitue [CBasePane :: CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider ::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Substitue [CBasePane ::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider ::D oesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider :: GetWidth](#getwidth)||
|[CPaneDivider :: init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Substitue [CBasePane :: IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[CPaneDivider :: IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Substitue [CBasePane :: IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
|[CPaneDivider :: Move](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider :: Serialize](#serialize)|(Substitue `CBasePane::Serialize`.)|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider :: ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Retourne la liste des volets qui résident dans la [classe CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Retourne la liste des diviseurs de volet qui résident dans la [classe CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CPaneDivider :: m_nDefaultWidth](#m_ndefaultwidth)|Spécifie la largeur par défaut en pixels de tous les diviseurs de volet de l’application.|
|[CPaneDivider :: m_pSliderRTC](#m_psliderrtc)|Contient un pointeur vers les informations de la classe Runtime à propos d’un `CPaneDivider` objet dérivé de.|

## <a name="remarks"></a>Notes

L’infrastructure crée `CPaneDivider` automatiquement des objets lorsqu’un volet est ancré.

Il existe deux types de diviseurs de volets :

- un diviseur de volet par défaut est créé lorsqu’un groupe de volets est ancré à un côté de la fenêtre frame principale. Le diviseur de volet par défaut contient un pointeur vers la [classe CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) et redirige la plupart des opérations sur le groupe de volets (telles que le redimensionnement d’un volet ou l’ancrage d’un autre volet ou conteneur) au gestionnaire de conteneurs. Chaque volet d’ancrage conserve un pointeur vers son séparateur de volet par défaut.

- Un diviseur de volet normal divise simplement deux volets dans un conteneur. Pour plus d’informations, consultez [CPaneContainer, classe](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment obtenir un objet `CPaneDivider` à partir d'un objet `CWorkspaceBar`. Cet extrait de code fait partie de l' [exemple de démonstration MDI Tabs](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxPaneDivider. h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a> CPaneDivider::SetAutoHideMode

```cpp
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Paramètres

dans *bMode*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a> CPaneDivider::SetPaneContainerManager

```cpp
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Paramètres

dans *p*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedivideraddpane"></a><a name="addpane"></a> CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a> CPaneDivider::AddPaneContainer

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

dans *barContainerManager*<br/>
dans *bOuterEdge*<br/>
dans *pTargetBar*<br/>
dans *dwAlignment*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a> CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a> CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Paramètres

dans *pWndToDock*<br/>
dans *ptMouse*<br/>
dans *rectResult*<br/>
dans *bDrawTab*<br/>
dans *ppTargetBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a> CPaneDivider::CalcFixedLayout

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

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a> CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a> CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Paramètres

dans *bDefaultSlider*<br/>
dans *pParent*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividercreateex"></a><a name="createex"></a> CPaneDivider :: CreateEx

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

dans *dwStyleEx*<br/>
dans *dwStyle*<br/>
dans *Rect*<br/>
dans *pParentWnd*<br/>
dans *nid*<br/>
dans *pContext*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CPaneDivider ::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a> CPaneDivider ::D oesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a> CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>
dans *bLeftBar*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a> CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Paramètres

dans *nid*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a> CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a> CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a> CPaneDivider::GetPaneDividers

Retourne la liste des diviseurs de volet qui résident dans la [classe CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut.

```cpp
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Paramètres

*lstSliders*<br/>
à Contient la liste des diviseurs de volet qui se trouvent dans le conteneur du volet.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut. Un diviseur de volet par défaut est un séparateur qui redimensionne le conteneur entier du volet.

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a> CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a> CPaneDivider::GetPanes

Retourne la liste des volets qui résident dans la [classe CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Cette méthode doit être appelée uniquement pour récupérer les diviseurs de volet par défaut.

```cpp
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Paramètres

*lstBars*<br/>
à Contient la liste des volets qui se trouvent dans le conteneur du volet.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée uniquement pour les diviseurs de volet par défaut. Un diviseur de volet par défaut est un séparateur qui redimensionne le conteneur entier du volet.

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a> CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a> CPaneDivider :: GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerinit"></a><a name="init"></a> CPaneDivider :: init

```cpp
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Paramètres

dans *bDefaultSlider*<br/>
dans *pParent*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a> CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

dans *pBarToInsert*<br/>
dans *pTargetBar*<br/>
dans *dwAlignment*<br/>
dans *lpRect*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a> CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a> CPaneDivider :: IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a> CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a> CPaneDivider :: m_nDefaultWidth

Spécifie la largeur par défaut, en pixels, de tous les diviseurs de volets de l’application.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a> CPaneDivider :: Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *ptOffset*<br/>
dans *bAdjustLayout*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a> CPaneDivider :: m_pSliderRTC

Contient un pointeur vers les informations de la classe Runtime à propos d’un `CPaneDivider` objet dérivé de.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Notes

Définissez cette variable membre si vous créez un diviseur de volet personnalisé. Cela permet à l’infrastructure de créer votre séparateur de volets lorsque le volet est dessiné.

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir la `m_pSliderRTC` variable de membre :

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a> CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Notes

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a> CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>
dans *bShow*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a> CPaneDivider::ReleaseEmptyPaneContainers

```cpp
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Notes

## <a name="cpanedividerremovepane"></a><a name="removepane"></a> CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a> CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Paramètres

dans *pBarToReplace*<br/>
dans *pBarToReplaceWith*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a> CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Paramètres

dans *rectNew*<br/>
dans *hdwp*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerserialize"></a><a name="serialize"></a> CPaneDivider :: Serialize

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

dans *AR*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a> CPaneDivider :: ShowWindow

```cpp
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Paramètres

dans *nCmdShow*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a> CPaneDivider::StoreRecentDockSiteInfo

```cpp
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a> CPaneDivider::StoreRecentTabRelatedInfo

```cpp
void StoreRecentTabRelatedInfo(
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
[CPaneContainerManager, classe](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer, classe](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager, classe](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane, classe](../../mfc/reference/cbasepane-class.md)
