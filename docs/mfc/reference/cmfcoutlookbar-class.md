---
description: 'En savoir plus sur : classe CMFCOutlookBar'
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
ms.openlocfilehash: e54e44e702aaf8d6883ada6be9c127f63ecee97d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265036"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar, classe

Volet à onglets avec l'apparence visuelle du **Volet de navigation** dans Microsoft Outlook 2000 et Outlook 2003. L' `CMFCOutlookBar` objet contient un objet de [classe CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) et une série d’onglets. Les onglets peuvent être des objets de [classe CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) ou `CWnd` des objets dérivés de. Pour l'utilisateur, la barre Outlook apparaît comme un ensemble de boutons et une zone d'affichage. Lorsque l'utilisateur clique sur un bouton, le volet de contrôle ou de bouton correspondant s'affiche.

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
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Spécifie si un volet à onglets vide peut être détruit. (Substitue [CBaseTabbedPane :: AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar :: CanAcceptPane](#canacceptpane)|Détermine si un autre volet peut être ancré dans le volet de la barre Outlook. (Substitue CDockablePane :: CanAcceptPane.)|
|[CMFCOutlookBar :: CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Détermine si la légende du volet à onglets affiche le même texte que l’onglet actif. (Substitue [CBaseTabbedPane :: CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar :: Create](#create)|Crée le contrôle de barre Outlook.|
|[CMFCOutlookBar :: CreateCustomPage](#createcustompage)|Crée un onglet de barre Outlook personnalisé.|
|`CMFCOutlookBar::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCOutlookBar ::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|Détermine si un utilisateur peut ancrer une barre de contrôle sur le bord externe de la barre Outlook.|
|[CMFCOutlookBar :: FloatTab](#floattab)|Flotte un volet, mais uniquement si le volet se trouve actuellement dans un onglet détachable. (Substitue [CBaseTabbedPane :: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar :: GetButtonsFont](#getbuttonsfont)|Retourne la police du texte sur les boutons de la barre Outlook.|
|[CMFCOutlookBar :: GetTabArea](#gettabarea)|Retourne la taille et la position des onglets sur la barre Outlook. (Substitue [CBaseTabbedPane :: GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCOutlookBar :: IsMode2003](#ismode2003)|Détermine si le comportement de la barre Outlook imite celle de Microsoft Office Outlook 2003 (consultez la section Notes).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Appelé par [CMFCOutlookBarTabCtrl :: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) après que l’onglet actif a été défini à l’aide d’une animation.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Appelé par [CMFCOutlookBarTabCtrl :: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) avant qu’une page d’onglets ne soit définie comme l’onglet actif à l’aide de l’animation.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Appelé par le Framework si la barre Outlook est déroulante.|
|[CMFCOutlookBar :: RemoveCustomPage](#removecustompage)|Supprime un onglet de barre Outlook personnalisé.|
|[CMFCOutlookBar :: SetButtonsFont](#setbuttonsfont)|Définit la police du texte sur les boutons de la barre Outlook.|
|[CMFCOutlookBar :: SetMode2003](#setmode2003)|Spécifie si le comportement de la barre Outlook imite celui d’Outlook 2003 (consultez la section Notes).|

## <a name="remarks"></a>Notes

Pour obtenir un exemple de barre Outlook, consultez l' [exemple OutlookDemo : application MFC OutlookDemo](../../overview/visual-cpp-samples.md).

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

1. Lors du traitement du message d’WM_CREATE dans le frame principal, appelez la méthode [CMFCOutlookBar :: Create](#create) pour créer le contrôle onglet de barre Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Obtenez un pointeur vers le sous-jacent à `CMFCOutlookBarTabCtrl` l’aide de [CBaseTabbedPane :: GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Créez un objet de [classe CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) pour chaque onglet qui contient des boutons.

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

1. Appelez [CMFCOutlookBarTabCtrl :: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pour ajouter chaque nouvel onglet. Définissez le paramètre *bDetachable* sur false pour rendre une page non détachable. Vous pouvez utiliser [CMFCOutlookBarTabCtrl :: AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) pour ajouter des pages détachables.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Pour ajouter un `CWnd` contrôle dérivé de (par exemple, la [classe CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)) sous la forme d’un onglet, créez le contrôle et appelez [CMFCOutlookBarTabCtrl :: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pour l’ajouter à la barre Outlook.

> [!NOTE]
> Vous devez utiliser des ID de contrôle uniques pour chaque objet de [classe CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) et pour chaque `CWnd` objet dérivé de.

Pour ajouter ou supprimer dynamiquement de nouvelles pages au moment de l’exécution, utilisez [CMFCOutlookBar :: CreateCustomPage](#createcustompage) et [CMFCOutlookBar :: RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Mode Outlook 2003

En mode Outlook 2003, les boutons d’onglet sont positionnés en bas du volet barre Outlook. Lorsqu’il n’y a pas suffisamment d’espace pour afficher les boutons, ceux-ci sont affichés sous forme d’icônes dans une zone de type barre d’outils en bas du volet.

Utilisez [CMFCOutlookBar :: SetMode2003](#setmode2003) pour activer le mode Outlook 2003. Utilisez [CMFCOutlookBarTabCtrl :: SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) pour définir l’image bitmap qui contient les icônes affichées en bas de la barre Outlook. Les icônes de la bitmap doivent être classées par index de tabulation.

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

**En-tête :** afxoutlookbar. h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a> CMFCOutlookBar :: AllowDestroyEmptyTabbedPane

Spécifie si un volet à onglets vide peut être détruit.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si un volet à onglets vide peut être détruit ; Sinon, FALSe. L’implémentation par défaut retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Si un volet à onglets vide ne peut pas être détruit, le Framework le masque à la place.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a> CMFCOutlookBar :: CanAcceptPane

Détermine si un autre volet peut être ancré dans le volet de la barre Outlook.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
dans Pointeur vers un autre volet qui est ancré à ce volet.

### <a name="return-value"></a>Valeur renvoyée

TRUE si un autre volet peut être ancré dans le volet de barre Outlook ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si la barre Outlook est en mode Outlook 2003, l’ancrage n’est pas pris en charge, donc la valeur de retour est FALSe.

Si le paramètre *pBar* est null, cette méthode retourne false.

Dans le cas contraire, cette méthode se comporte comme la méthode de base [CBasePane :: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), sauf que même si l’ancrage n’est pas activé, une barre Outlook peut toujours permettre à une autre barre Outlook d’être ancrée sur elle.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a> CMFCOutlookBar :: CanSetCaptionTextToTabName

Détermine si la légende du volet à onglets affiche le même texte que l’onglet actif.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la légende de la fenêtre barre Outlook est automatiquement définie sur le texte de l’onglet actif ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez [CBaseTabbedPane :: EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) pour activer ou désactiver cette fonctionnalité.

En mode Outlook 2003, ce paramètre est toujours activé.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a> CMFCOutlookBar :: Create

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
dans Spécifie le titre de la fenêtre.

*pParentWnd*<br/>
dans Spécifie un pointeur vers une fenêtre parente. Il ne doit pas être NULL.

*rectangulaire*<br/>
dans Spécifie la taille et la position de la barre Outlook en pixels.

*nID*<br/>
dans Spécifie l’ID du contrôle. Doit être différent des autres ID de contrôle utilisés dans l’application.

*dwStyle*<br/>
dans Spécifie le style de barre de contrôle souhaité. Pour connaître les valeurs possibles, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
dans Spécifie les styles spéciaux définis par la bibliothèque.

*pContext*<br/>
dans Créer un contexte.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCOutlookBar` objet en deux étapes. Appelez d’abord le constructeur, puis appelez `Create` , qui crée le contrôle de barre Outlook et l’attache à l' `CMFCOutlookBar` objet.

Consultez [CBasePane :: CreateEx](../../mfc/reference/cbasepane-class.md#createex) pour obtenir la liste des styles définis par la bibliothèque disponibles à spécifier par *dwControlBarStyle*.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `Create` méthode de la `CMFCOutlookBar` classe. Cet extrait de code fait partie de l' [exemple Outlook multi views](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a> CMFCOutlookBar :: CreateCustomPage

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
dans Étiquette de page.

*bActivatePage*<br/>
dans Si la valeur est TRUE, la page devient active lors de la création.

*dwEnabledDocking*<br/>
dans Combinaison d’CBRS_ALIGN_ indicateurs qui spécifie les côtés d’ancrage activés lorsque la page est détachée.

*bEnableTextLabels*<br/>
dans Si la valeur est TRUE, les étiquettes de texte sont activées pour les boutons qui résident sur la page.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la page nouvellement créée, ou NULL si la création a échoué.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour permettre aux utilisateurs de créer des pages de barre Outlook personnalisées. Vous pouvez créer jusqu’à 100 pages par application. Les ID de contrôle de page démarrent à partir de 0xF000. La création échoue si le nombre total de pages de la barre Outlook personnalisées dépasse 100.

Utilisez [CMFCOutlookBar :: RemoveCustomPage](#removecustompage) pour supprimer des pages personnalisées.

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCOutlookBar ::D oesAllowDynInsertBefore

Spécifie si un utilisateur peut ancrer un volet sur le bord externe de la barre Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation par défaut retourne FALSe.

### <a name="remarks"></a>Notes

L’infrastructure appelle la `DoesAllowDynInsertBefore` méthode lorsqu’il recherche un emplacement pour ancrer un volet dynamique. Si la fonction retourne la valeur FALSe, le Framework n’autorise pas l’ancrage d’un volet dynamique sur les bords extérieurs du volet.

En règle générale, vous créez une barre Outlook en tant que contrôle non flottant statique. Vous pouvez remplacer cette fonction dans une classe dérivée et retourner TRUE pour modifier ce comportement.

> [!NOTE]
> Étant donné que les volets dynamiques vérifient l’état des volets statiques ancrés lors de l’ancrage, vous devez ancrer les volets dynamiques après les volets statiques chaque fois que cela est possible.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a> CMFCOutlookBar :: FloatTab

Flotte un volet.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
dans Pointeur vers le volet à flotter.

*nTabID*<br/>
dans Index de base zéro de l’onglet à détacher.

*dockMethod*<br/>
dans Spécifie la méthode à utiliser pour rendre le volet flottant.  Pour plus d’informations, consultez [CBaseTabbedPane :: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide*<br/>
dans TRUE pour masquer le volet avant qu’il ne soit flottant ; Sinon, FALSe. Contrairement à la version de classe de base de cette méthode, ce paramètre n’a pas de valeur par défaut.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le volet est dissocié ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode est similaire à [CBaseTabbedPane :: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) , à ceci près qu’elle n’active pas le dernier onglet restant sur un contrôle de barre Outlook.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a> CMFCOutlookBar :: GetButtonsFont

Retourne la police du texte sur les onglets de bouton de page de la barre Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet de police utilisé pour afficher le texte dans les onglets du bouton de page de la barre Outlook.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour récupérer la police utilisée pour afficher le texte dans les onglets du bouton de page Outlook. Vous pouvez définir la police en appelant sur [CMFCOutlookBar :: SetButtonsFont](#setbuttonsfont).

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a> CMFCOutlookBar :: GetTabArea

Détermine la taille et la position des onglets sur la barre Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
à Contient la taille et la position (dans les coordonnées clientes) de la zone d’onglet supérieure lorsque la fonction retourne.

*rectTabAreaBottom*<br/>
à Contient la taille et la position (dans les coordonnées clientes) de la zone d’onglet inférieure lorsque la fonction est retournée.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour déterminer le type d’ancrage au volet cible. Lorsque le Framework détermine que l’utilisateur fait glisser le volet pour l’ancrer sur la zone d’onglet du volet cible, il tente d’ajouter le premier volet sous la forme d’un nouvel onglet du volet cible. Sinon, elle tente d’ancrer le premier volet à un côté approprié du volet cible. L’infrastructure crée un nouveau conteneur avec un curseur pour prendre en charge le volet ancré supplémentaire.

L’implémentation par défaut de `GetTabArea` retourne la totalité de la zone cliente de la barre Outlook si la barre Outlook est statique ; autrement dit, si la barre Outlook ne peut pas flotter. Sinon, elle retourne la zone que les boutons de page prennent en haut et en bas du contrôle de barre Outlook.

Substituez cette méthode dans la classe dérivée de `CMFCOutlookBar` pour modifier ce comportement.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a> CMFCOutlookBar :: IsMode2003

Spécifie si le comportement de la barre Outlook imite celle de Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la barre Outlook s’exécute en mode Microsoft Office 2003 ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez activer ce mode à l’aide de [CMFCOutlookBar :: SetMode2003](#setmode2003).

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a> CMFCOutlookBar :: OnAfterAnimation

Appelé par [CMFCOutlookBarTabCtrl :: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) après que l’onglet actif a été défini à l’aide d’une animation.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
dans Index de base zéro de la page d’onglets qui a été rendu actif.

### <a name="remarks"></a>Notes

L’effet visuel de la définition de l’onglet actif varie selon que vous avez activé l’animation. Pour plus d’informations, consultez [CMFCOutlookBarTabCtrl :: EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a> CMFCOutlookBar :: OnBeforeAnimation

Appelé par [CMFCOutlookBarTabCtrl :: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) avant qu’une page d’onglets ne soit définie comme l’onglet actif à l’aide de l’animation.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
dans Index de base zéro de la page d’onglets qui va être définie.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’animation doit être utilisée dans la définition de l’onglet actif, ou FALSe si l’animation doit être désactivée.

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a> CMFCOutlookBar :: OnScroll

Appelé par le Framework si la barre Outlook est déroulante.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Paramètres

*bDown*<br/>
dans TRUE si la barre Outlook défile vers le haut, ou FALSe si elle fait défiler vers le haut.

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a> CMFCOutlookBar :: RemoveCustomPage

Supprime une page d’onglets de la barre Outlook personnalisée.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Paramètres

*uiPage*<br/>
dans Index de base zéro de la page dans la fenêtre Outlook parente.

*pTargetWnd*<br/>
dans Pointerto la fenêtre parente d’Outlook.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la page personnalisée a été supprimée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction pour supprimer des pages personnalisées. Lorsque la page est supprimée, son ID de contrôle est renvoyé au pool d’ID disponibles.

Vous devez fournir un pointeur vers l’objet de [classe CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) dans lequel la page à supprimer se trouve actuellement. Notez qu’un utilisateur peut déplacer des pages détachables entre différentes barres Outlook, mais les informations relatives à une page personnalisée résident dans l’objet de la barre Outlook pour lequel vous avez appelé [CMFCOutlookBar :: CreateCustomPage](#createcustompage).

Utilisez [CBaseTabbedPane :: GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) pour obtenir un pointeur vers la fenêtre Outlook.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a> CMFCOutlookBar :: SetButtonsFont

Définit la police du texte sur les boutons de la barre Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
dans Spécifie la nouvelle police.

*bRedraw*<br/>
dans Si la valeur est TRUE, la barre Outlook est redessinée.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une police pour le texte affiché sur les boutons de la page d’onglets Outlook.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a> CMFCOutlookBar :: SetMode2003

Spécifie si le comportement de la barre Outlook imite celui d’Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Paramètres

*bMode2003*<br/>
dans Si la valeur est TRUE, le mode Office 2003 est activé.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour activer ou désactiver le mode Office 2003. Dans ce mode, la barre Outlook comporte une barre d’outils supplémentaire avec un bouton de personnalisation. Le comportement de la barre Outlook est conforme au comportement de la barre Outlook dans Microsoft Office 2003.

Par défaut, ce mode est désactivé.

> [!NOTE]
> Cette fonction doit être appelée avant [CMFCOutlookBar :: Create](#create).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane, classe](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md)
