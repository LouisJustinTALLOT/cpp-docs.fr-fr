---
title: Ctabbedpane, classe
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: af9c65e51f7230b0fc6a59d0eed42eca08d24837
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263349"
---
# <a name="ctabbedpane-class"></a>Ctabbedpane, classe

Implémente les fonctionnalités d'un volet à onglets détachables.

ou plus de détails, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(Substitue [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Active ou désactive la coloration automatique des onglets.|
|[CTabbedPane::FloatTab](#floattab)|Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable. (Substitue [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Retourne la taille et la position de la zone d'onglet dans la fenêtre à onglets.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Détermine si le volet à onglets peut passer en mode masquage automatique. (Substitue [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Détermine si les onglets sont situés au bas de la fenêtre.|
|[CTabbedPane::ResetTabs](#resettabs)|Rétablit l'état par défaut de tous les volets à onglets.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Définit une liste de couleurs personnalisées qui peuvent être utilisées quand la fonctionnalité de couleur automatique est activée.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Emplacement par défaut des onglets dans l'application.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informations de classe runtime pour un objet dérivé de `CMFCTabCtrl` personnalisé.|

## <a name="remarks"></a>Notes

L'infrastructure crée automatiquement une instance de cette classe quand un utilisateur attache un volet à un autre en pointant vers la légende du deuxième volet. Tous les volets à onglets créés par l'infrastructure ont un ID égal à -1.

Pour spécifier des onglets normaux au lieu des onglets de style Outlook, passez le style AFX_CBRS_REGULAR_TABS à la [CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex) (méthode).

Si vous créez un volet à onglets avec des onglets détachables, le volet risque d’être détruit automatiquement par l’infrastructure. Il est donc déconseillé de stocker le pointeur. Pour obtenir un pointeur vers le volet à onglets, appelez la méthode `CBasePane::GetParentTabbedPane`.

## <a name="example"></a>Exemple

Dans cet exemple, nous créons un objet `CTabbedPane`. Ensuite, nous utilisons [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) à attacher des onglets supplémentaires.

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

## <a name="example"></a>Exemple

Une autre façon de créer un objet de barre de contrôle à onglets consiste à utiliser [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). Le `AttachToTabWnd` méthode crée dynamiquement un objet de volet à onglets à l’aide des informations de classe runtime définies par [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

Dans cet exemple, nous créons un volet à onglets de façon dynamique, joignons les deux onglets et rendons le deuxième onglet non détachable.

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxTabbedPane.h

##  <a name="detachpane"></a>  CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

[in] *pBar*<br/>

[in] *bHide*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="enabletabautocolor"></a>  CTabbedPane::EnableTabAutoColor

Active ou désactive la coloration automatique des onglets.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[in] TRUE pour activer la coloration automatique des onglets ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode statique pour activer ou désactiver la coloration automatique des onglets dans tous les volets à onglets dans l’application. Lorsque cette fonctionnalité est activée, chaque onglet est rempli par sa propre couleur. Vous trouverez la liste de couleurs qui sont utilisés pour colorer les onglets en appelant le [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) (méthode).

Vous pouvez spécifier la liste des couleurs qui sera utilisé pour les onglets en appelant [CTabbedPane::SetTabAutoColors](#settabautocolors).

Par défaut, cette option est désactivée.

##  <a name="floattab"></a>  CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

[in] *pBar*<br/>
[in] *nTabID*<br/>
[in] *dockMethod*<br/>
[in] *bHide*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="gettabarea"></a>  CTabbedPane::GetTabArea

Retourne la taille et la position de la zone d’onglet dans la fenêtre à onglets.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
[out] Contient la taille et position, en coordonnées d’écran, de la zone d’onglet supérieur.

*rectTabAreaBottom*<br/>
[out] Contient la taille et position, en coordonnées d’écran, de la zone d’onglet en bas.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour déterminer comment un utilisateur fait glisser un volet d’ancrage. Lorsque l’utilisateur fait glisser un volet sur la zone d’onglet du volet cible, le framework tente d’ajouter comme un nouvel onglet du volet cible. Sinon, il essaie d’ancrer le volet vers le côté du volet cible, ce qui implique la création d’un conteneur de volet par un diviseur de volet qui sépare les deux volets.

Substituez cette méthode dans un `CTabbedPane`-classe pour modifier ce comportement dérivée.

##  <a name="gettabwnd"></a>  CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="hasautohidemode"></a>  CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="istablocationbottom"></a>  CTabbedPane::IsTabLocationBottom

Détermine si les onglets sont situés au bas de la fenêtre.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la zone d’onglet se trouve en bas de la fenêtre à onglets. Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="m_btabsalwaystop"></a>  CTabbedPane::m_bTabsAlwaysTop

Emplacement par défaut des onglets dans l'application.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Notes

Définissez ce membre statique à True pour forcer tous les onglets dans l’application à afficher en haut du volet à onglets.

Vous devez définir cette valeur avant la création d’un volet à onglets.

La valeur par défaut est FALSE.

##  <a name="m_ptabwndrtc"></a>  CTabbedPane::m_pTabWndRTC

Informations de classe runtime pour un objet dérivé de `CMFCTabCtrl` personnalisé.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Notes

Définissez cette variable de membre statique à un pointeur vers les informations de classe runtime un `CMFCTabCtrl`-objet dérivé si vous utilisez une fenêtre à onglets personnalisée à l’intérieur d’un volet à onglets.

##  <a name="resettabs"></a>  CTabbedPane::ResetTabs

Rétablit l'état par défaut de tous les volets à onglets.

```
static void ResetTabs();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour annuler tous les volets à onglets à leur état par défaut. Lorsqu’elle est appelée, cette méthode réinitialise les tailles de bordure et l’état de couleur automatique de tous les volets à onglets.

##  <a name="settabautocolors"></a>  CTabbedPane::SetTabAutoColors

Définit une liste de couleurs personnalisées qui sont utilisées lors de la fonctionnalité de couleur automatique est activée.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Paramètres

*arColors*<br/>
[in] Contient le tableau de couleurs à définir.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour personnaliser la liste des couleurs qui sont utilisées lorsque la fonctionnalité de couleur automatique est activée. Ceci est une fonction statique et affecte à tous les onglets des volets dans votre application.

Utilisez [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) pour activer ou désactiver la fonctionnalité de couleur automatique.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane, classe](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)
