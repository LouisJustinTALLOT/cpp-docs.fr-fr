---
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
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365953"
---
# <a name="ctabbedpane-class"></a>CTabbedPane, classe

Implémente les fonctionnalités d'un volet à onglets détachables.

ou plus de détails voir le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

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
|[CTabbedPane::DetachPane](#detachpane)|(Overrides [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Active ou désactive la coloration automatique des onglets.|
|[CTabbedPane::FloatTab](#floattab)|Flotte une vitre, mais seulement si le volet réside actuellement dans un onglet amovible. (Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Retourne la taille et la position de la zone d'onglet dans la fenêtre à onglets.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Détermine si le volet à onglets peut passer en mode masquage automatique. (Overrides [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
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

Pour spécifier des onglets réguliers au lieu d’onglets de style Outlook, passez le style AFX_CBRS_REGULAR_TABS à la méthode [CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex) méthode.

Si vous créez un volet à onglets avec des onglets détachables, le volet risque d’être détruit automatiquement par l’infrastructure. Il est donc déconseillé de stocker le pointeur. Pour obtenir un pointeur vers le volet à onglets, appelez la méthode `CBasePane::GetParentTabbedPane`.

## <a name="example"></a>Exemple

Dans cet exemple, nous créons un objet `CTabbedPane`. Ensuite, nous utilisons [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) pour attacher des onglets supplémentaires.

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

Une autre façon de créer un objet de barre de commande tabbed est d’utiliser [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). La `AttachToTabWnd` méthode crée dynamiquement un objet de vitres onglets à l’aide d’informations de classe runtime définies par [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

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

**En-tête:** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>

[dans] *bHide (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor

Active ou désactive la coloration automatique des onglets.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour permettre la coloration automatique des onglets; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode statique pour activer ou désactiver la coloration automatique des onglets dans toutes les vitres onglets de l’application. Lorsque cette fonctionnalité est activée, chaque onglet est rempli par sa propre couleur. Vous pouvez trouver la liste des couleurs qui sont utilisées pour colorer les onglets en appelant la [méthode CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) méthode.

Vous pouvez spécifier la liste des couleurs qui seront utilisées pour les onglets en appelant [CTabbedPane::SetTabAutoColors](#settabautocolors).

Par défaut, cette option est désactivée.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

[dans] *pBar (pBar)*<br/>
[dans] *nTabID (en)*<br/>
[dans] *dockMethod*<br/>
[dans] *bHide (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbedPane::GetTabArea

Retourne la taille et la position de la zone de l’onglet dans la fenêtre tabbed.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
[out] Contient la taille et la position, dans les coordonnées de l’écran, de la zone de l’onglet supérieur.

*rectTabAreaBottom*<br/>
[out] Contient la taille et la position, dans les coordonnées de l’écran, de la zone de l’onglet inférieur.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode pour déterminer comment amarrer une vitre qu’un utilisateur traîne. Lorsque l’utilisateur traîne une vitre sur la zone de l’onglet de la vitre cible, le cadre tente de l’ajouter comme un nouvel onglet de la vitre cible. Sinon, il tente d’amarrer la vitre sur le côté de la vitre cible, ce qui implique la création d’un nouveau récipient de vitre avec un diviseur de vitre qui sépare les deux vitres.

Remplacer cette méthode `CTabbedPane`dans une classe dérivée pour changer ce comportement.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom

Détermine si les onglets sont situés au bas de la fenêtre.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la zone de l’onglet est située au bas de la fenêtre tabbed; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop

Emplacement par défaut des onglets dans l'application.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Notes

Définissez ce membre statique à TRUE pour forcer tous les onglets de l’application à être affichés en haut de la vitre tabbed.

Vous devez définir cette valeur avant qu’une vitre tabbed a été créée.

La valeur par défaut est FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC

Informations de classe runtime pour un objet dérivé de `CMFCTabCtrl` personnalisé.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Notes

Définissez cette variable de membre statique à un `CMFCTabCtrl`pointeur aux informations de classe de temps d’exécution d’un objet dérivé si vous utilisez une fenêtre tabbed personnalisée à l’intérieur d’une vitre tabbed.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbedPane::ResetTabs

Rétablit l'état par défaut de tous les volets à onglets.

```
static void ResetTabs();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour retourner toutes les vitres onglets à leur état par défaut. Lorsqu’elle est appelée, cette méthode réinitialise la taille de la bordure et l’état de couleur automatique de toutes les vitres tablées.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors

Définit une liste de couleurs personnalisées qui sont utilisées lorsque la fonction de couleur automatique est activée.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Paramètres

*arColors (arColors)*<br/>
[dans] Contient la gamme de couleurs à définir.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour personnaliser la liste des couleurs qui sont utilisées lorsque la fonction de couleur automatique est activée. Il s’agit d’une fonction statique et affecte toutes les vitres tabbed dans votre application.

Utilisez [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) pour activer ou désactiver la fonction couleur automatique.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane, classe](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
