---
title: CMFCOutlookBar, classe
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369650"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar, classe

Volet à onglets avec l'apparence visuelle du **Volet de navigation** dans Microsoft Outlook 2000 et Outlook 2003. L’objet `CMFCOutlookBar` contient un objet [cmFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) et une série d’onglets. Les onglets peuvent être soit des objets de `CWnd`classe [CMFCOutlookBarPane,](../../mfc/reference/cmfcoutlookbarpane-class.md) soit des objets dérivés. Pour l'utilisateur, la barre Outlook apparaît comme un ensemble de boutons et une zone d'affichage. Lorsque l'utilisateur clique sur un bouton, le volet de contrôle ou de bouton correspondant s'affiche.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Constructeur par défaut.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Précise si une vitre vide peut être détruite. (Overrides [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Détermine si une autre vitre peut être amarré à la vitre de barre Outlook. (Overrides CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Détermine si la légende de la vitre tabbed affiche le même texte que l’onglet actif. (Overrides [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Créer](#create)|Crée le contrôle de barre Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Crée un onglet de barre Outlook personnalisé.|
|`CMFCOutlookBar::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Détermine si un utilisateur peut amarrer une barre de contrôle au bord extérieur de la barre Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Flotte une vitre, mais seulement si le volet réside actuellement dans un onglet amovible. (Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Retourne la police du texte sur les boutons de la barre Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Retourne la taille et la position des zones d’onglets sur la barre Outlook. (Overrides [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Détermine si le comportement de la barre Outlook imite celui de Microsoft Office Outlook 2003 (voir Remarques).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) après l’onglet actif a été réglé à l’aide de l’animation.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) avant qu’une page d’onglet ne soit définie comme onglet actif à l’aide de l’animation.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Appelé par le cadre si la barre Outlook fait défiler vers le haut ou vers le bas.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Supprime un onglet De barre Outlook personnalisé.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Définit la police du texte sur les boutons de la barre Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Précise si le comportement de la barre Outlook imite celui d’Outlook 2003 (voir Remarques).|

## <a name="remarks"></a>Notes

Par exemple, consultez [l’exemple OutlookDemo : MFC OutlookDemo Application](../../overview/visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Mise en œuvre de la barre Outlook

Pour utiliser le contrôle `CMFCOutlookBar` dans votre application, procédez comme suit :

1. Incorporez un objet `CMFCOutlookBar` dans la classe de fenêtre frame principale.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Lors du traitement du message WM_CREATE dans le cadre principal, appelez le [CMFCOutlookBar : : Créez](#create) la méthode pour créer le contrôle de l’onglet barre Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Obtenir un pointeur `CMFCOutlookBarTabCtrl` à la sous-jacente en utilisant [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Créez un objet [cmFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) pour chaque onglet contenant des boutons.

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. Appelez [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pour ajouter chaque nouvel onglet. Définissez le paramètre *bDetachable* à FALSE pour rendre une page non amovible. Ou, utilisez [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) pour ajouter des pages amovibles.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Pour ajouter `CWnd`un contrôle dérivé (par exemple, [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)) comme onglet, créez le contrôle et appelez [CMFCOutlookBarTabCtrl ::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pour l’ajouter à la barre Outlook.

> [!NOTE]
> Vous devez utiliser des pièces d’ID de contrôle uniques pour `CWnd`chaque objet [cmFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) et pour chaque objet dérivé.

Pour ajouter ou supprimer dynamiquement de nouvelles pages au moment de l’exécution, utilisez [CMFCOutlookBar::CreateCustomPage](#createcustompage) et [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Mode Perspectives 2003

En mode Outlook 2003, les boutons de l’onglet sont positionnés au bas de la vitre de la barre Outlook. Lorsqu’il n’y a pas assez d’espace pour afficher les boutons, ils sont affichés comme des icônes dans une zone de forme de barre d’outils le long du bas de la vitre.

Utilisez [CMFCOutlookBar::SetMode2003](#setmode2003) pour activer le mode Outlook 2003. Utilisez [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) pour définir le bitmap qui contient les icônes qui s’affichent au bas de la barre Outlook. Les icônes dans la bitmap doivent être commandées par index d’onglet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxoutlookbar.h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Précise si une vitre vide peut être détruite.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si une vitre tabbed vide peut être détruite; autrement, FALSE. L’implémentation par défaut renvoie toujours TRUE.

### <a name="remarks"></a>Notes

Si un volet tabbed vide ne peut pas être détruit, le cadre le cache à la place.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane

Détermine si une autre vitre peut être amarré à la vitre de barre Outlook.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans] Un pointeur à une autre vitre qui est amarré à cette vitre.

### <a name="return-value"></a>Valeur de retour

VRAI si une autre vitre peut être amarré à la vitre de barre Outlook; autrement FALSE.

### <a name="remarks"></a>Notes

Si la barre Outlook est en mode Outlook 2003, l’amarrage n’est pas pris en charge, de sorte que la valeur de retour est FALSE.

Si le paramètre *pBar* est NULL, cette méthode renvoie FALSE.

Sinon, cette méthode se comporte comme la méthode de base [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), sauf que même si l’amarrage n’est pas activé, une barre Outlook peut encore permettre à une autre barre Outlook d’être amarré sur elle.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName

Détermine si la légende de la vitre tabbed affiche le même texte que l’onglet actif.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la légende de la fenêtre de barre Outlook est automatiquement réglée sur le texte de l’onglet actif ; autrement FALSE.

### <a name="remarks"></a>Notes

Utilisez [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) pour activer ou désactiver cette fonctionnalité.

En mode Outlook 2003, ce paramètre est toujours activé.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar::Créer

Crée le contrôle de barre Outlook.

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszCaption*<br/>
[dans] Spécifie la légende de la fenêtre.

*pParentWnd*<br/>
[dans] Spécifie un pointeur vers une fenêtre parent. Ce ne doit pas être NULL.

*Rect*<br/>
[dans] Spécifie la taille de la barre de perspective et la position dans les pixels.

*nID*<br/>
[dans] Spécifie l’ID de contrôle. Doit être distinct des autres ID de contrôle utilisés dans l’application.

*dwStyle (en)*<br/>
[dans] Spécifie le style de barre de contrôle désiré. Pour les valeurs possibles, voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle (en)*<br/>
[dans] Spécifie les styles spéciaux définis par la bibliothèque.

*pContext*<br/>
[dans] Créez un contexte.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCOutlookBar` objet en deux étapes. Appelez d’abord le constructeur, puis appelez, `Create`ce qui crée `CMFCOutlookBar` le contrôle de barre de perspective et le fixe à l’objet.

Voir [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) pour la liste des styles définis par la bibliothèque disponibles à préciser par *dwControlBarStyle*.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `Create` utiliser `CMFCOutlookBar` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon Outlook Multi Views](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage

Crée un onglet de barre Outlook personnalisé.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszPageName*<br/>
[dans] L’étiquette de page.

*bActivatePage*<br/>
[dans] Si VRAI, la page devient active lors de la création.

*dwEnabledDocking*<br/>
[dans] Une combinaison de drapeaux CBRS_ALIGN_ qui spécifie les côtés d’amarrage activés lorsque la page est détachée.

*bEnableTextLabels*<br/>
[dans] Si VRAI, les étiquettes de texte sont activées pour les boutons qui résident sur la page.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la page nouvellement créée, ou NULL si la création a échoué.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour permettre aux utilisateurs de créer des pages de barres Outlook personnalisées. Vous pouvez créer jusqu’à 100 pages par application. Les ID de contrôle de page commencent à partir de 0xF000. La création échoue si le nombre total de pages de barres Outlook personnalisées dépasse 100.

Utilisez [CMFCOutlookBar::RemoveCustomPage](#removecustompage) pour supprimer les pages personnalisées.

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore

Précise si un utilisateur peut amarrer une vitre au bord extérieur de la barre Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

La implémentation par défaut renvoie FALSE.

### <a name="remarks"></a>Notes

Le cadre `DoesAllowDynInsertBefore` appelle la méthode lorsqu’elle cherche un emplacement pour amarrer une vitre dynamique. Si la fonction renvoie FALSE, le cadre ne permet pas l’amarrage d’une vitre dynamique sur les bords extérieurs de la vitre.

Habituellement, vous créez une barre Outlook comme un contrôle statique non flottant. Vous pouvez remplacer cette fonction dans une classe dérivée et retourner VRAI pour changer ce comportement.

> [!NOTE]
> Étant donné que les vitres dynamiques vérifient l’état des vitres statiques amarrés lors de l’amarrage, vous devez amarrer des vitres dynamiques après des vitres statiques chaque fois que possible.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar::FloatTab

Flotte une vitre.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans] Un pointeur à la vitre pour flotter.

*nTabID (en)*<br/>
[dans] L’indice zéro de l’onglet à flotter.

*dockMethod*<br/>
[dans] Spécifie la méthode à utiliser pour faire flotter la vitre.  Pour plus d’informations, voir [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide (en)*<br/>
[dans] VRAI pour cacher la vitre avant de flotter; autrement, FALSE. Contrairement à la version de classe de base de cette méthode, ce paramètre n’a pas de valeur par défaut.

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre flottait; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est comme [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) sauf qu’il ne permet pas le dernier onglet restant sur un contrôle de barre Outlook de flotter.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont

Retourne la police du texte sur les onglets bouton de page de la barre Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de l’objet de police qui est utilisé pour afficher du texte sur les onglets de bouton de page de barre Outlook.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour récupérer la police qui est utilisée pour afficher le texte sur les onglets de bouton de page Outlook. Vous pouvez définir la police en faisant appel à [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar::GetTabArea

Détermine la taille et la position des zones d’onglets sur la barre Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
[out] Contient la taille et la position (dans les coordonnées du client) de la zone de l’onglet supérieur lorsque la fonction revient.

*rectTabAreaBottom*<br/>
[out] Contient la taille et la position (dans les coordonnées du client) de la zone de l’onglet inférieur lorsque la fonction revient.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode pour déterminer le type d’amarrage à la vitre cible. Lorsque le cadre détermine que l’utilisateur fait glisser la vitre à amarrée sur la zone de l’onglet de la vitre cible, il essaie d’ajouter le premier volet comme nouvel onglet de la vitre cible. Sinon, il tente d’amarrer la première vitre à un côté approprié de la vitre cible. Le cadre crée un nouveau conteneur avec un curseur pour accueillir la vitre amarrée supplémentaire.

La mise `GetTabArea` en œuvre par défaut des retours de l’ensemble de la zone client de la barre Outlook si la barre Outlook est statique; c’est-à-dire, si la barre Outlook ne peut pas flotter. Sinon, il renvoie la zone que les boutons de page prennent en haut et en bas du contrôle de barre Outlook.

Remplacer cette méthode en `CMFCOutlookBar` classe dérivée pour changer ce comportement.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar::IsMode2003

Précise si le comportement de la barre Outlook imite celui de Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la barre Outlook est en cours d’exécution en mode Microsoft Office 2003; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez activer ce mode en utilisant [CMFCOutlookBar::SetMode2003](#setmode2003).

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation

Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) après l’onglet actif a été réglé à l’aide de l’animation.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
[dans] L’index zéro de la page d’onglet qui a été rendu actif.

### <a name="remarks"></a>Notes

L’effet visuel du réglage de l’onglet actif dépend de si vous avez activé l’animation. Pour plus d’informations, voir [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation

Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) avant qu’une page d’onglet ne soit définie comme onglet actif à l’aide de l’animation.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
[dans] L’index zéro de la page d’onglet qui est sur le point d’être mis en activité.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’animation doit être utilisée dans la configuration du nouvel onglet actif, ou FALSE si l’animation doit être désactivée.

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookBar::OnScroll

Appelé par le cadre si la barre Outlook fait défiler vers le haut ou vers le bas.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Paramètres

*bDown (en)*<br/>
[dans] VRAI si la barre Outlook fait défiler vers le bas, ou FALSE si elle fait défiler vers le haut.

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage

Supprime une page d’onglet à barres Outlook personnalisée.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Paramètres

*uiPage (uiPage)*<br/>
[dans] Indice zéro de la page dans la fenêtre Outlook parent.

*pTargetWnd*<br/>
[dans] Pointer à la fenêtre Outlook parent.

### <a name="return-value"></a>Valeur de retour

Nonzero si la page personnalisée a été supprimée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction pour supprimer les pages personnalisées. Lorsque la page est supprimée, son ID de contrôle est retourné au pool d’IDENTIFIANTs disponibles.

Vous devez fournir un pointeur à [l’objet cmFCOutlookBarTabCtrl Classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md) dans lequel la page à supprimer réside actuellement. Notez qu’un utilisateur peut déplacer des pages amovibles entre les différentes barres Outlook, mais les informations sur une page personnalisée réside dans l’objet barreUrier Outlook pour lequel vous avez appelé [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Utilisez [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) pour obtenir un pointeur à la fenêtre Outlook.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont

Définit la police du texte sur les boutons de la barre Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[dans] Spécifie la nouvelle police.

*bRedraw (en)*<br/>
[dans] Si TRUE, la barre Outlook sera redessinée.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une police pour le texte affiché sur les boutons de page d’onglet d’affichage.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar::SetMode2003

Précise si le comportement de la barre Outlook imite celui d’Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Paramètres

*bMode2003*<br/>
[dans] Si VRAI, le mode Office 2003 est activé.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour activer ou désactiver le mode Office 2003. Dans ce mode, la barre Outlook dispose d’une barre d’outils supplémentaire avec un bouton de personnalisation. Le comportement de la barre Outlook est conforme au comportement de la barre Outlook dans Microsoft Office 2003.

Par défaut, ce mode est désactivé.

> [!NOTE]
> Cette fonction doit être appelée avant [CMFCOutlookBar::Créer](#create).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane, classe](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[Classe CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
