---
description: 'En savoir plus sur : classe CTabbedPane'
title: CTabbedPane, classe
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
ms.openlocfilehash: a337a68cdeadfec229b24e10a615ba49145ec1ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264477"
---
# <a name="ctabbedpane-class"></a>CTabbedPane, classe

Implémente les fonctionnalités d'un volet à onglets détachables.

ou plus de détails, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

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
|[CTabbedPane::DetachPane](#detachpane)|(Substitue [CBaseTabbedPane ::D etachpane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Active ou désactive la coloration automatique des onglets.|
|[CTabbedPane::FloatTab](#floattab)|Flotte un volet, mais uniquement si le volet se trouve actuellement dans un onglet détachable. (Substitue [CBaseTabbedPane :: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Retourne la taille et la position de la zone d'onglet dans la fenêtre à onglets.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Détermine si le volet à onglets peut passer en mode masquage automatique. (Substitue [CBaseTabbedPane :: HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Détermine si les onglets sont situés au bas de la fenêtre.|
|[CTabbedPane::ResetTabs](#resettabs)|Rétablit l'état par défaut de tous les volets à onglets.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Définit une liste de couleurs personnalisées qui peuvent être utilisées quand la fonctionnalité de couleur automatique est activée.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Emplacement par défaut des onglets dans l'application.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informations de classe runtime pour un objet dérivé de `CMFCTabCtrl` personnalisé.|

## <a name="remarks"></a>Notes

L'infrastructure crée automatiquement une instance de cette classe quand un utilisateur attache un volet à un autre en pointant vers la légende du deuxième volet. Tous les volets à onglets créés par l'infrastructure ont un ID égal à -1.

Pour spécifier des onglets normaux à la place des onglets de style Outlook, transmettez le style AFX_CBRS_REGULAR_TABS à la méthode [CDockablePane :: CreateEx](../../mfc/reference/cdockablepane-class.md#createex) .

Si vous créez un volet à onglets avec des onglets détachables, le volet risque d’être détruit automatiquement par l’infrastructure. Il est donc déconseillé de stocker le pointeur. Pour obtenir un pointeur vers le volet à onglets, appelez la méthode `CBasePane::GetParentTabbedPane`.

## <a name="examples"></a>Exemples

Dans cet exemple, nous créons un objet `CTabbedPane`. Ensuite, nous utilisons [CBaseTabbedPane :: addTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) pour attacher d’autres onglets.

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

Une autre façon de créer un objet de barre de contrôle avec onglet consiste à utiliser [CDockablePane :: AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). La `AttachToTabWnd` méthode crée dynamiquement un objet volet à onglets à l’aide des informations de classe Runtime définies par [CDockablePane :: SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

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

**En-tête :** afxTabbedPane. h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a> CTabbedPane ::D etachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

dans *bHide*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a> CTabbedPane::EnableTabAutoColor

Active ou désactive la coloration automatique des onglets.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer la coloration automatique des onglets ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode statique pour activer ou désactiver la coloration automatique des onglets dans tous les volets à onglets de l’application. Lorsque cette fonctionnalité est activée, chaque onglet est rempli par sa propre couleur. Vous pouvez trouver la liste des couleurs utilisées pour colorier les onglets en appelant la méthode [CMFCBaseTabCtrl :: GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) .

Vous pouvez spécifier la liste des couleurs qui seront utilisées pour les onglets en appelant [CTabbedPane :: SetTabAutoColors](#settabautocolors).

Par défaut, cette option est désactivée.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a> CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>
dans *nTabID*<br/>
dans *dockMethod*<br/>
dans *bHide*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a> CTabbedPane::GetTabArea

Retourne la taille et la position de la zone d’onglet dans la fenêtre à onglets.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
à Contient la taille et la position, en coordonnées d’écran, de la zone d’onglet supérieure.

*rectTabAreaBottom*<br/>
à Contient la taille et la position, en coordonnées d’écran, de la zone d’onglet inférieure.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour déterminer comment ancrer un volet qu’un utilisateur fait glisser. Quand l’utilisateur fait glisser un volet sur la zone d’onglet du volet cible, le Framework tente de l’ajouter en tant que nouvel onglet du volet cible. Sinon, elle tente d’ancrer le volet sur le côté du volet cible, ce qui implique la création d’un nouveau conteneur de volets avec un séparateur de volet qui sépare les deux volets.

Substituez cette méthode dans une `CTabbedPane` classe dérivée de pour modifier ce comportement.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a> CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a> CTabbedPane::IsTabLocationBottom

Détermine si les onglets sont situés au bas de la fenêtre.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la zone d’onglet est située en bas de la fenêtre à onglets ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a> CTabbedPane :: m_bTabsAlwaysTop

Emplacement par défaut des onglets dans l'application.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre statique pour forcer l’affichage de tous les onglets de l’application en haut du volet à onglets.

Vous devez définir cette valeur avant la création d’un volet à onglets.

La valeur par défaut est FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a> CTabbedPane :: m_pTabWndRTC

Informations de classe runtime pour un objet dérivé de `CMFCTabCtrl` personnalisé.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Notes

Affectez à cette variable membre statique un pointeur vers les informations de classe d’exécution d’un `CMFCTabCtrl` objet dérivé de si vous utilisez une fenêtre à onglets personnalisée à l’intérieur d’un volet à onglets.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a> CTabbedPane::ResetTabs

Rétablit l'état par défaut de tous les volets à onglets.

```
static void ResetTabs();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour rétablir l’État par défaut de tous les volets à onglets. Lorsqu’elle est appelée, cette méthode réinitialise les tailles des bordures et l’état de couleur automatique de tous les volets à onglets.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a> CTabbedPane::SetTabAutoColors

Définit une liste de couleurs personnalisées qui sont utilisées lorsque la fonctionnalité de couleur automatique est activée.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Paramètres

*arColors*<br/>
dans Contient le tableau de couleurs à définir.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour personnaliser la liste des couleurs utilisées lorsque la fonctionnalité de couleur automatique est activée. Il s’agit d’une fonction statique qui affecte tous les volets à onglets dans votre application.

Utilisez [CTabbedPane :: EnableTabAutoColor](#enabletabautocolor) pour activer ou désactiver la fonctionnalité de couleur automatique.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane, classe](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)
