---
title: CMFCOutlookBar, classe | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0597cc6dd2c52792f583d23a45bbafe8bc996ffd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374501"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar, classe

Volet à onglets avec l'apparence visuelle du **Volet de navigation** dans Microsoft Outlook 2000 et Outlook 2003. Le `CMFCOutlookBar` objet contient un [cmfcoutlookbartabctrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md) et une série d’onglets. Les onglets peuvent être soit [cmfcoutlookbarpane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md) objets ou `CWnd`-objets dérivés. Pour l'utilisateur, la barre Outlook apparaît comme un ensemble de boutons et une zone d'affichage. Lorsque l'utilisateur clique sur un bouton, le volet de contrôle ou de bouton correspondant s'affiche.

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
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Spécifie si un volet à onglets vide peut être détruit. (Substitue [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Détermine si un autre volet peut être ancré dans le volet de barre Outlook. (Substitue CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Détermine si la légende pour le volet à onglets affiche le même texte sous l’onglet actif. (Substitue [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Create](#create)|Crée le contrôle de barre Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Crée un onglet de barre Outlook personnalisé.|
|`CMFCOutlookBar::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Détermine si un utilisateur pouvez ancrer une barre de contrôle sur le bord externe de la barre Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable. (Substitue [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Retourne la police du texte sur les boutons de la barre Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Retourne la taille et la position des zones d’onglet dans la barre Outlook. (Substitue [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Détermine si le comportement de la barre Outlook imite celui de Microsoft Office Outlook 2003 (voir Remarques).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) une fois que l’onglet actif a été défini à l’aide de l’animation.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) avant un onglet de page est définie comme l’onglet actif à l’aide de l’animation.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Appelé par le framework si la barre Outlook effectue le défilement vers le haut ou vers le bas.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Supprime un onglet de barre Outlook personnalisé.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Définit la police du texte sur les boutons de la barre Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Spécifie si le comportement de la barre Outlook imite celui d’Outlook 2003 (voir Remarques).|

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’une barre Outlook, consultez le [exemple OutlookDemo : MFC OutlookDemo Application](../../visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implémentation de la barre Outlook

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

1. Lors du traitement du message WM_CREATE dans le frame principal, appelez le [CMFCOutlookBar::Create](#create) méthode pour créer un contrôle d’onglet de barre Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Obtenir un pointeur vers sous-jacent `CMFCOutlookBarTabCtrl` à l’aide de [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Créer un [cmfcoutlookbarpane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md) objet pour chaque onglet qui contient les boutons.

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

1. Appelez [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pour ajouter chaque nouvel onglet. Définir le *bDetachable* paramètre sur FALSE pour rendre une page non détachables. Ou, utilisez [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) pour ajouter des pages détachables.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Pour ajouter un `CWnd`-contrôle dérivé (par exemple, [CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md)) sous forme d’onglet, créer le contrôle et l’appel [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pour l’ajouter à la barre Outlook.

> [!NOTE]
>  Vous devez utiliser l’ID de contrôle unique pour chaque [cmfcoutlookbarpane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md) objet et pour chaque `CWnd`-objet dérivé.

Pour dynamiquement ajouter ou supprimer des pages lors de l’exécution, utilisez [CMFCOutlookBar::CreateCustomPage](#createcustompage) et [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Mode d’Outlook 2003

En mode de Outlook 2003, les boutons d’onglet sont positionnées en bas du volet de barre Outlook. Lorsqu’il n’est pas suffisamment de place pour afficher les boutons, ils sont affichés sous forme d’icônes dans une zone de barre d’outils dans la partie inférieure du volet.

Utilisez [CMFCOutlookBar::SetMode2003](#setmode2003) pour activer le mode d’Outlook 2003. Utilisez [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) pour définir l’image bitmap qui contient les icônes sont affichées en bas de la barre Outlook. Les icônes dans l’image bitmap doivent être triées par index de tabulation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxoutlookbar.h

##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Spécifie si un volet à onglets vide peut être détruit.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si un volet à onglets vide peut être détruit ; Sinon, FALSE. Toujours l’implémentation par défaut retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Si un volet à onglets vide ne peut pas être détruit, le framework le masque à la place.

##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane

Détermine si un autre volet peut être ancré dans le volet de barre Outlook.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Pointeur vers un autre volet est ancré vers ce volet.

### <a name="return-value"></a>Valeur de retour

TRUE si un autre volet peut être ancré dans le volet de barre Outlook ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Si la barre est en mode de Outlook 2003, ancrage de Outlook n’est pas pris en charge, par conséquent, la valeur de retour est FALSE.

Si le *pBar* paramètre est NULL, cette méthode retourne FALSE.

Sinon, cette méthode se comporte comme la méthode de base [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), sauf que même si d’ancrage n’est pas activée, une barre Outlook peut toujours activer une autre barre Outlook être ancré sur celui-ci.

##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName

Détermine si la légende pour le volet à onglets affiche le même texte sous l’onglet actif.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’Outlook à la barre de titre de la fenêtre est automatiquement défini sur le texte de l’onglet actif ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) pour activer ou désactiver cette fonctionnalité.

En mode de Outlook 2003, ce paramètre est toujours activé.

##  <a name="create"></a>  CMFCOutlookBar::Create

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
[in] Spécifie la légende de fenêtre.

*pParentWnd*<br/>
[in] Spécifie un pointeur vers une fenêtre parente. Il ne doit pas être NULL.

*Rect*<br/>
[in] Spécifie la taille et la position en pixels de la barre outlook.

*nID*<br/>
[in] Spécifie l’ID de contrôle. Doit être distinct des autres identificateurs utilisés dans l’application de contrôle.

*dwStyle*<br/>
[in] Spécifie le style de barre de contrôle souhaité. Pour connaître les valeurs possibles, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
[in] Spécifie les styles définis par la bibliothèque spéciales.

*pContext*<br/>
[in] Créer le contexte.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCOutlookBar` objet en deux étapes. Tout d’abord appeler le constructeur, puis appelez `Create`, ce qui crée le contrôle de barre outlook et l’attache à la `CMFCOutlookBar` objet.

Consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) pour obtenir la liste les styles définis par la bibliothèque disponibles pour être spécifié par *dwControlBarStyle*.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `Create` méthode de la `CMFCOutlookBar` classe. Cet extrait de code fait partie de la [Outlook plusieurs vues, exemple](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage

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
[in] L’étiquette de la page.

*bActivatePage*<br/>
[in] Si la valeur est TRUE, la page devient active lors de la création.

*dwEnabledDocking*<br/>
[in] Une combinaison d’indicateurs CBRS_ALIGN_ qui spécifie les côtés d’ancrage est activées lorsque la page est détachée.

*bEnableTextLabels*<br/>
[in] Si la valeur est TRUE, les étiquettes de texte sont activés pour les boutons qui se trouvent sur la page.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la page qui vient d’être créée, ou NULL si la création a échoué.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour permettre aux utilisateurs de créer des pages personnalisées de barre Outlook. Vous pouvez créer jusqu'à 100 pages par application. Le contrôle de page ID démarrent à partir de 0xF000. La création échoue si le nombre total de pages de la barre Outlook personnalisées est supérieure à 100.

Utilisez [CMFCOutlookBar::RemoveCustomPage](#removecustompage) pour supprimer des pages personnalisées.

##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore

Spécifie si un utilisateur pouvez ancrer un volet sur le bord externe de la barre Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut retourne FALSE.

### <a name="remarks"></a>Notes

Le framework appelle la `DoesAllowDynInsertBefore` méthode lorsqu’il recherche un emplacement ancrer un volet dynamique. Si la fonction retourne FALSE, le framework n’autorise pas l’ancrage de n’importe quel volet dynamique aux bords externes du volet.

En règle générale, vous créez une barre Outlook comme un contrôle statique non flottante. Vous pouvez remplacer cette fonction dans une classe dérivée et renvoie la valeur TRUE pour modifier ce comportement.

> [!NOTE]
>  Étant donné que les volets dynamiques vérifie l’état ancré volets statique lors de l’ancrage, vous devez volets d’ancrage dynamiques après statiques volets autant que possible.

##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab

Fait flotter un volet.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Un pointeur vers le volet pour float.

*nTabID*<br/>
[in] Index de base zéro de l’onglet en float.

*dockMethod*<br/>
[in] Spécifie la méthode à utiliser pour détacher le volet.  Pour plus d’informations, consultez [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide*<br/>
[in] TRUE pour masquer le volet avant flottante. Sinon, FALSE. Contrairement à la version de la classe de base de cette méthode, ce paramètre n’a pas de valeur par défaut.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet flottantes ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode est comparable à [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) , à ceci près qu’elles n’autorisent pas le dernier onglet restant sur un contrôle de barre Outlook pour float.

##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont

Retourne la police du texte dans la page d’onglets de bouton de la barre Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet de police qui est utilisé pour afficher le texte dans Outlook barre d’onglets de bouton de page.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour récupérer la police qui est utilisée pour afficher le texte sur les onglets de bouton de page Outlook. Vous pouvez définir la police en appelant sur [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea

Détermine la taille et la position des zones d’onglet dans la barre Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
[out] Lorsque la fonction retourne, contient la taille et la position (dans les coordonnées clientes) de la zone d’onglet supérieur.

*rectTabAreaBottom*<br/>
[out] Lorsque la fonction retourne une valeur, contient la taille et la position (dans les coordonnées clientes) de la zone d’onglet en bas.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour déterminer le type d’ancrage dans le volet cible. Lorsque le framework détermine que l’utilisateur fait glisser le volet pour être ancré sur la zone d’onglet du volet cible, il tente d’ajouter le premier volet en tant qu’un nouvel onglet du volet cible. Sinon, il essaie d’ancrer le premier volet à un côté du volet cible approprié. L’infrastructure crée un conteneur avec un curseur pour prendre en charge le volet ancré supplémentaire.

L’implémentation par défaut de `GetTabArea` retourne toute la zone cliente de la barre Outlook, si la barre Outlook est statique ; c'est-à-dire, si la barre Outlook ne peut pas float. Sinon, elle retourne la zone acceptant les boutons de page en haut et bas du contrôle de barre Outlook.

Substituez cette méthode dans une classe dérivée de `CMFCOutlookBar` pour modifier ce comportement.

##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003

Spécifie si le comportement de la barre Outlook imite celui de Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre Outlook est en cours d’exécution en mode de Microsoft Office 2003 ; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez activer ce mode à l’aide de [CMFCOutlookBar::SetMode2003](#setmode2003).

##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation

Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) une fois que l’onglet actif a été défini à l’aide de l’animation.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
[in] Index de base zéro de la page d’onglets est devenue active.

### <a name="remarks"></a>Notes

L’effet visuel de la définition de l’onglet actif varie selon que vous avez activé l’animation. Pour plus d’informations, consultez [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation

Appelé par [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) avant un onglet de page est définie comme l’onglet actif à l’aide de l’animation.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
[in] Index de base zéro de la page d’onglets qui doit être défini active.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si l’animation doit être utilisée lors de la définition du nouvel onglet actif, ou FALSE si l’animation doit être désactivée.

### <a name="remarks"></a>Notes

##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll

Appelé par le framework si la barre Outlook effectue le défilement vers le haut ou vers le bas.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Paramètres

*bDown*<br/>
[in] TRUE si la barre Outlook est défilement vers le bas, ou FALSE si elle défile des.

### <a name="remarks"></a>Notes

##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage

Supprime une page d’onglet de barre Outlook personnalisée.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Paramètres

*uiPage*<br/>
[in] Index de base zéro de la page dans la fenêtre parente d’Outlook.

*pTargetWnd*<br/>
[in] Pointerto la fenêtre parente d’Outlook.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la page personnalisée a été supprimée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction pour supprimer des pages personnalisées. Lorsque la page est supprimée, son ID de contrôle est retourné au pool d’ID disponibles.

Vous devez fournir un pointeur vers [cmfcoutlookbartabctrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md) de l’objet dans lequel réside la page doit être supprimé actuellement. Notez qu’un utilisateur peut déplacer des pages détachables entre les différentes barres Outlook, mais les informations sur une page personnalisée résident dans l’objet de barre Outlook pour lequel vous avez appelé [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Utilisez [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) pour obtenir un pointeur vers la fenêtre Outlook.

##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont

Définit la police du texte sur les boutons de la barre Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[in] Spécifie la nouvelle police.

*bRedraw*<br/>
[in] Si la valeur est TRUE, la barre Outlook est redessinée.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une police pour le texte affiché sur les boutons de page d’onglet outlook.

##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003

Spécifie si le comportement de la barre Outlook imite celui d’Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Paramètres

*bMode2003*<br/>
[in] Si la valeur est TRUE, le mode d’Office 2003 est activé.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour activer ou désactiver le mode d’Office 2003. Dans ce mode, la barre Outlook a une barre d’outils supplémentaire avec un bouton de personnalisation. Le comportement de la barre Outlook est conforme au comportement de la barre Outlook dans Microsoft Office 2003.

Par défaut, ce mode est désactivé.

> [!NOTE]
>  Cette fonction doit être appelée avant [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane, classe](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md)
