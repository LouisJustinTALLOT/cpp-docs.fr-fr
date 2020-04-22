---
title: Classe CMFCMenuBar
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: f25bff9564eb7a4290f958f0b7810cac8ef7e238
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749615"
---
# <a name="cmfcmenubar-class"></a>Classe CMFCMenuBar

Barre de menus qui implémente l'ancrage.
Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Substitue `CMFCToolBar::AdjustLocations`.)|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Précise si les étiquettes de texte peuvent être affichées sous les images sur les boutons de la barre d’outils. (Overrides [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Calcule la taille horizontale de la barre d’outils. (Overrides [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Substitue `CMFCToolBar::CalcLayout`.)|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Calcule la hauteur maximale des boutons dans la barre d’outils. (Overrides [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar:CanBeClosed](#canbeclosed)|Précise si un utilisateur peut fermer la barre d’outils. (Overrides [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar:CanBeRestored](#canberestored)|Détermine si le système peut restaurer une barre d’outils à son état d’origine après la personnalisation. (Overrides [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenuBar::Créer](#create)|Crée un contrôle de menu `CMFCMenuBar` et l’attache à un objet.|
|[CMFCMenuBar::CreateEx](#createex)|Crée `CMFCMenuBar` un objet avec des options de style supplémentaires.|
|[CMFCMenuBar::CreateDeMenu](#createfrommenu)|Initialise un objet `CMFCMenuBar`. Accepte un paramètre HMENU qui agit comme `CMFCMenuBar`un modèle pour un peuplé .|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Permet une boîte combo **Help** qui se trouve sur le côté droit de la barre de menu.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Précise s’il faut afficher des ombres pour des menus pop-up.|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Overrides [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Retourne la largeur des boutons de la barre d’outils. (Overrides [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Retourne une poignée au menu original dans le fichier des ressources.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Retourne l’identifiant de ressource pour le menu original dans le fichier de ressources.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Retourne un pointeur à la boîte combo **Help.**|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Retourne la poignée au menu qui `CMFCMenuBar` est attaché à l’objet.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Retourne la police globale actuelle pour les objets de menu.|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Retourne le bouton de la barre d’outils associé à l’index d’article fourni.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Retourne la hauteur des boutons de barre d’outils. (Overrides [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Indique si les éléments de menu désactivés sont mis en évidence.|
|[CMFCMenuBar::IsButtonExtrasizeAvailable](#isbuttonextrasizeavailable)|Détermine si la barre d’outils peut afficher les boutons qui ont des bordures étendues. (Overrides [CMFCToolBar::IsButtonExtrasizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Indique si les éléments désactivés sont mis en évidence.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Indique si les ombres sont dessinées pour les menus pop-up.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Indique si les commandes de menu récemment utilisées sont affichées sur la barre de menu.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Indique si les menus contextuels affichent toutes les commandes.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Indique si les menus affichent toutes les commandes après un court délai.|
|[CMFCMenuBar::LoadState](#loadstate)|Charge l’état `CMFCMenuBar` de l’objet du registre.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Appelé par le cadre quand un utilisateur sélectionne un bouton sur la barre d’outils. (Overrides [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Appelé par le cadre quand une fenêtre de cadre charge le menu par défaut du fichier de ressources.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Substitue `CMFCToolBar::OnSendCommand`.)|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Appelé par le cadre quand un menu est en mode personnalisation et l’utilisateur change le texte d’un élément de menu.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Substitue `CMFCToolBar::OnToolHitTest`.)|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Substitue `CMFCToolBar::PreTranslateMessage`.)|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Appelé par le cadre quand un menu est en mode personnalisation et l’utilisateur sélectionne **Reset** pour une barre de menu.|
|[CMFCMenuBar::SaveState](#savestate)|Enregistre l’état `CMFCMenuBar` de l’objet au registre.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Définit le menu original dans le fichier des ressources.|
|[CMFCMenuBar:SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Appelé par le cadre quand une fenêtre d’enfant MDI change son mode d’affichage. Si la fenêtre de l’enfant MDI est nouvellement maximisée ou n’est plus maximisée, cette méthode met à jour la barre de menu.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Définit les informations de classe de temps d’exécution qui sont générées lorsque l’utilisateur crée dynamiquement des boutons de menu.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Définit la police pour tous les menus de l’application.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Précise si une barre de menu affiche les commandes de menu récemment utilisées.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Précise si la barre de menu affiche toutes les commandes.|

## <a name="remarks"></a>Notes

La `CMFCMenuBar` classe est une barre de menu qui implémente la fonctionnalité d’amarrage. Il ressemble à une barre d’outils, bien qu’il ne puisse pas être fermé - il est toujours affiché.

`CMFCMenuBar`prend en charge la possibilité d’afficher des objets de menu récemment utilisés. Si cette option est `CMFCMenuBar` activée, l’affichage n’est qu’un sous-ensemble des commandes disponibles lors de la première visualisation. Par la suite, les commandes récemment utilisées sont affichées avec le sous-ensemble original de commandes. En outre, l’utilisateur peut toujours élargir le menu pour afficher toutes les commandes disponibles. Ainsi, chaque commande disponible est configurée pour afficher constamment, ou pour afficher seulement si elle a été récemment sélectionnée.

Pour utiliser `CMFCMenuBar` un objet, l’intégrer dans l’objet de cadre de fenêtre principale. Lors du `WM_CREATE` traitement `CMFCMenuBar::Create` du `CMFCMenuBar::CreateEx`message, appelez ou . Indépendamment de la fonction de créer que vous utilisez, passez dans un pointeur à la fenêtre de cadre principale. Ensuite, activez l’amarrage en appelant [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Amarrez ce menu en appelant [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCMenuBar` . L’exemple montre comment définir le style de la vitre, activer le bouton personnaliser, activer une boîte d’aide, activer les ombres pour les menus pop-up, et mettre à jour la barre de menu. Cet extrait de code fait partie de [l’échantillon de démonstration IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmenubar.h

## <a name="cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations

Ajuste les positions des éléments du menu sur la barre de menu.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels

Détermine si les étiquettes de texte sont autorisées sous les images dans la barre de menu.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’utilisateur peut choisir d’afficher des étiquettes de texte sous des images.

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

[dans] *bStretch*<br/>

[dans] *bHorz (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Paramètres

[dans] *dwMode dwMode*<br/>

[dans] *nLength (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFCMenuBar:CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFCMenuBar:CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarcreate"></a><a name="create"></a>CMFCMenuBar::Créer

Crée un contrôle de menu et le fixe à un objet [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md)

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[dans] Pointeur vers la fenêtre `CMFCMenuBar` parente pour le nouvel objet.

*dwStyle (en)*<br/>
[dans] Le style du nouveau bar de menu.

*nID*<br/>
[dans] L’ID pour la fenêtre enfant de la barre de menu.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Après avoir `CMFCMenuBar` construit un objet, vous devez appeler `Create`. Cette méthode `CMFCMenuBar` crée le contrôle et `CMFCMenuBar` l’attache à l’objet.

Pour plus d’informations sur les styles de barres d’outils, voir [CBasePane:SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

## <a name="cmfcmenubarcreateex"></a><a name="createex"></a>CMFCMenuBar::CreateEx

Crée un objet [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) avec des styles étendus spécifiés.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[dans] Pointeur vers la fenêtre `CMFCMenuBar` parente du nouvel objet.

*dwCtrlStyle (en)*<br/>
[dans] Styles supplémentaires pour la nouvelle barre de menu.

*dwStyle (en)*<br/>
[dans] Le style principal du nouveau bar de menu.

*rcBorders*<br/>
[dans] Un `CRect` paramètre qui spécifie les `CMFCMenuBar` tailles des bordures de l’objet.

*nID*<br/>
[dans] L’ID pour la fenêtre enfant de la barre de menu.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

Vous devez utiliser cette fonction au lieu de [CMFCMenuBar::Créer](#create) lorsque vous voulez spécifier des styles en plus du style barre d’outils. Certains modèles supplémentaires fréquemment utilisés sont TBSTYLE_TRANSPARENT et CBRS_TOP.

Pour les listes de styles supplémentaires, voir [Toolbar Control et Button Styles](/windows/win32/Controls/toolbar-control-and-button-styles), styles de contrôle [communs](/windows/win32/Controls/common-control-styles), et les styles de [fenêtre commune](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Exemple

L’exemple suivant montre comment `CreateEx` utiliser `CMFCMenuBar` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon de démonstration IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

## <a name="cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFCMenuBar::CreateDeMenu

Initialise un objet [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md) Cette méthode `CMFCMenuBar` modélise l’objet d’après un paramètre HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
[dans] Une poignée à une ressource de menu. `CreateFromMenu`utilise cette ressource comme `CMFCMenuBar`un modèle pour le .

*bDefaultMenu (en)*<br/>
[dans] Un Boolean qui indique si le nouveau menu est le menu par défaut.

*bForceUpdate (en)*<br/>
[dans] Un Boolean qui indique si cette méthode force une mise à jour du menu.

### <a name="remarks"></a>Notes

Utilisez cette méthode si vous voulez un contrôle de menu pour avoir les mêmes éléments de menu qu’une ressource de menu. Vous appelez cette méthode après avoir appelé [CMFCMenuBar::Créer](#create) ou [CMFCMenuBar::CreateEx](#createex).

## <a name="cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox

Permet une boîte combo **Help** qui se trouve sur le côté droit de la barre de menu.

```cpp
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] L’ID de commande pour le bouton de la boîte combo **Help.**

*lpszPrompt*<br/>
[dans] Une chaîne qui contient le texte que le cadre affiche dans la boîte combo si elle est vide et non active. Par exemple, "Entrez le texte ici".

*nComboBoxWidth (en)*<br/>
[dans] La largeur du bouton pour la boîte combo en pixels.

### <a name="remarks"></a>Notes

La boîte combo **Help** ressemble à la boîte combo **Help** dans la barre de menu de Microsoft Word.

Lorsque vous appelez cette méthode avec *uiID* réglé à 0, cette méthode cache la boîte combo. Sinon, cette méthode affiche automatiquement la boîte combo sur le côté droit de votre barre de menu. Après avoir appelé cette méthode, appelez [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) pour obtenir un pointeur à l’objet [inséré CMFCToolBarComboBoxButton.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows

Permet des ombres pour les menus pop-up.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Un paramètre Boolean qui indique si les ombres doivent être activées pour les menus pop-up.

### <a name="remarks"></a>Notes

L’algorithme que cette méthode utilise est complexe et peut diminuer les performances de votre application sur des systèmes plus lents.

## <a name="cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu

Récupère une poignée au menu original. Le cadre charge le menu original à partir du fichier des ressources.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée à une ressource de menu.

### <a name="remarks"></a>Notes

Si votre application personnalise un menu, vous pouvez utiliser cette méthode pour récupérer une poignée sur le menu original.

## <a name="cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId

Récupère l’identifiant de ressource pour le menu par défaut.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Valeur de retour

Un identificateur de ressources de menu.

### <a name="remarks"></a>Notes

Le cadre charge le menu `CMFCMenuBar` par défaut pour l’objet à partir du fichier de ressources.

## <a name="cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Paramètres

[dans] *pButton*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox

Retourne un pointeur à la boîte combo **Help.**

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la boîte combo **Help.** NULL si la boîte combo **Help** est cachée ou non activée.

### <a name="remarks"></a>Notes

La boîte combo **Help** est située sur le côté droit de la barre de menu. Appelez la méthode [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) pour activer cette boîte combo.

## <a name="cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFCMenuBar::GetHMenu

Récupère la poignée du menu attaché à l’objet [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md)

```
HMENU GetHMenu() const;
```

## <a name="cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFCMenuBar::GetMenuFont

Récupère la police de menu actuelle.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*bHorz (en)*<br/>
[dans] Un paramètre Boolean qui précise s’il faut retourner la police horizontale ou verticale. TRUE indique la police horizontale.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un paramètre [CFont](../../mfc/reference/cfont-class.md) qui contient la police de barre de menu actuelle.

### <a name="remarks"></a>Notes

La police retournée est un paramètre global pour l’application. Deux polices globales sont `CMFCMenuBar` maintenues pour tous les objets. Ces polices séparées sont utilisées pour les barres de menu horizontales et verticales.

## <a name="cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem

Récupère un objet [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) sur une barre de menu en fonction de l’index de l’élément.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
[dans] L’index de l’élément de menu à revenir.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CMFCToolBarButton` à l’objet qui correspond à l’index spécifié par *iItem*. NULL si l’indice est invalide.

## <a name="cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Paramètres

[dans] *uiBtn uiBtn*<br/>

[dans] *bByCommand (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems

Contrôle si le cadre met en évidence les éléments de menu désactivés.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Paramètres

*bHighlight (en)*<br/>
[dans] Un paramètre Boolean qui indique si le cadre met en évidence les éléments de menu indisponibles.

### <a name="remarks"></a>Notes

Par défaut, le cadre ne met pas en évidence les éléments de menu indisponibles lorsque l’utilisateur positionne le pointeur de la souris sur eux.

## <a name="cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtrasizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems

Indique si le cadre met en évidence les éléments de menu indisponibles.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Valeur de retour

VRAI si les éléments de menu indisponibles sont mis en surbrillance; autrement FALSE.

### <a name="remarks"></a>Notes

Par défaut, le cadre ne met pas en évidence les éléments de menu indisponibles lorsque l’utilisateur positionne le pointeur de la souris sur eux. Utilisez la méthode [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) pour activer cette fonctionnalité.

## <a name="cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows

Indique si le cadre dessine des ombres pour les menus pop-up.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Valeur de retour

VRAI si le cadre dessine des ombres de menu; autrement FALSE.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) pour activer ou désactiver cette fonctionnalité.

## <a name="cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus

Indique si les commandes de menu récemment utilisées sont affichées sur la barre de menu.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CMFCMenuBar` l’objet montre des commandes de menu récemment utilisé; sinon 0.

### <a name="remarks"></a>Notes

Utilisez la fonction [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) pour contrôler si la barre de menu montre les commandes de menu récemment utilisé.

## <a name="cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands

Indique si les menus affichent toutes les commandes.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CMFCMenuBar` les affiches toutes les commandes; sinon 0.

### <a name="remarks"></a>Notes

Un `CMFCMenuBar` objet peut être configuré pour afficher toutes les commandes ou afficher seulement un sous-ensemble de commandes. Pour plus d’informations sur cette fonctionnalité, voir [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands`vous indiquera comment cette fonctionnalité `CMFCMenuBar` est configurée pour l’objet. Pour contrôler les commandes de menu, utilisez les méthodes [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) et [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).

## <a name="cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay

Indique si l’objet [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) affiche toutes les commandes après un court délai.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la barre de menu affiche des menus complets après un court délai; sinon 0.

### <a name="remarks"></a>Notes

Lorsque vous configurez une barre de menu pour afficher des éléments récemment utilisés, la barre de menu affiche le menu complet de deux façons :

- Affichez le menu complet après un délai programmé à partir du moment où l’utilisateur plane le curseur sur la flèche au bas du menu.

- Affichez le menu complet après que l’utilisateur clique sur la flèche au bas du menu.

Par défaut, `CMFCMenuBar` tous les objets utilisent l’option pour afficher le menu complet après un court délai. Cette option ne peut pas `CMFCMenuBar` être modifiée de façon programmatique dans la classe. Cependant, un utilisateur peut modifier le comportement lors de la personnalisation de la barre d’outils en utilisant la boîte de dialogue **Customize.**

## <a name="cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFCMenuBar::LoadState

Charge l’état de la barre de menu du registre Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Une chaîne qui contient le chemin d’une clé de registre Windows.

*nIndex*<br/>
[dans] L’ID de contrôle pour la barre de menu.

*uiID*<br/>
[dans] Une valeur réservée.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCMenuBar:SaveState](#savestate) pour enregistrer l’état de la barre de menu au registre. Les informations enregistrées comprennent les éléments du menu, l’état du quai et la position de la barre de menu.

Dans la plupart des `LoadState`cas, votre demande n’appelle pas . Le cadre appelle cette méthode lorsqu’elle est para parasorisée l’espace de travail.

## <a name="cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Paramètres

[dans] *iHot (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded

Le cadre appelle cette méthode lorsqu’elle charge la ressource de menu à partir du fichier de ressources.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
[dans] La poignée pour le `CMFCMenuBar` menu attaché à l’objet.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacer cette fonction pour exécuter le code personnalisé après que le cadre charge une ressource de menu à partir du fichier de ressources.

## <a name="cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

[dans] *pButton*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText

Le cadre appelle cette méthode lorsque l’utilisateur modifie le texte d’un élément sur la barre du menu.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[dans] Un pointeur à l’objet [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) que l’utilisateur veut personnaliser.

### <a name="return-value"></a>Valeur de retour

VRAI si le cadre applique les modifications de l’utilisateur à la barre de menu; autrement FALSE.

### <a name="remarks"></a>Notes

La implémentation par défaut de cette méthode modifie le texte du bouton sur le texte que l’utilisateur fournit.

## <a name="cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Paramètres

[dans] *point*<br/>

[dans] *pTI (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

[dans] *pMsg*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate

Appelé par le cadre lorsque l’utilisateur sélectionne **Reset** à partir de la boîte de dialogue **Customize.**

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode s’appelle lorsque l’utilisateur sélectionne **Reset** à partir du menu de personnalisation. Vous pouvez également appeler manuellement cette méthode pour réinitialiser programmatiquement l’état de la barre de menu. Cette méthode charge l’état d’origine à partir du fichier de ressources.

Remplacez cette méthode si vous souhaitez effectuer un traitement lorsque l’utilisateur choisit **l’option Reset.**

## <a name="cmfcmenubarsavestate"></a><a name="savestate"></a>CMFCMenuBar::SaveState

Enregistre l’état de l’objet [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) au registre Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Une chaîne qui contient le chemin d’une clé de registre Windows.

*nIndex*<br/>
[dans] L’ID de contrôle pour la barre de menu.

*uiID*<br/>
[dans] Une valeur réservée.

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès; autrement FALSE;

### <a name="remarks"></a>Notes

Habituellement, votre demande `SaveState`n’appelle pas . Le cadre appelle cette méthode lorsque l’espace de travail est sérialisé. Pour plus d’informations, voir [CWinAppEx:SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Les informations enregistrées comprennent les éléments du menu, l’état du quai et la position de la barre de menu.

## <a name="cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId

Définit le menu par défaut d’un objet [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) en fonction de l’ID de ressources.

```cpp
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Paramètres

*uiResId*<br/>
[dans] L’ID de ressource pour le nouveau menu par défaut.

### <a name="remarks"></a>Notes

La [méthode CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) restaure le menu par défaut du fichier de ressources.

Utilisez la méthode [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) pour récupérer le menu par défaut sans le restaurer.

## <a name="cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFCMenuBar:SetForceDownArrows

```cpp
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Paramètres

[dans] *bValue (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode

Le cadre appelle cette méthode lorsqu’un MDI modifie son mode d’affichage et que la barre de menu doit être mise à jour.

```cpp
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Paramètres

*bMax (en)*<br/>
[dans] Un Boolean qui spécifie le mode. Pour plus d'informations, consultez la section Remarques.

*Pwnd*<br/>
[dans] Un pointeur à la fenêtre de l’enfant MDI qui change.

*bRecalcLayout (en)*<br/>
[dans] Un Boolean qui précise si la disposition de la barre de menu doit être recalculée immédiatement.

### <a name="remarks"></a>Notes

Lorsqu’une fenêtre pour enfants MDI est maximisée, une barre de menu fixée à la fenêtre du cadre principal MDI affiche le menu du système et les boutons **Minimize,** **Maximisez** et **Fermez.** Si *bMax* est VRAI et *pWnd n’est* pas NULL, la fenêtre pour enfant MDI est maximisée et la barre de menu doit incorporer les contrôles supplémentaires. Sinon, la barre de menu revient à son état régulier.

## <a name="cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC

Définit les informations de classe de temps d’exécution que le cadre utilise lorsque l’utilisateur crée des boutons de menu.

```cpp
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Paramètres

*pMenuButtonRTC*<br/>
[dans] Les informations [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pour une classe dérivée de la [classe CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur ajoute de nouveaux boutons à la barre de menu, le cadre crée les boutons de manière dynamique. Par défaut, `CMFCMenuButton` il crée des objets. Remplacer cette méthode pour modifier le type d’objets boutonné que le cadre crée.

## <a name="cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCMenuBar::SetMenuFont

Définit la police pour toutes les barres de menu dans votre application.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
[dans] Un pointeur vers une structure [LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta) qui définit la police à définir.

*bHorz (en)*<br/>
[dans] VRAI si vous voulez que le *paramètre lpLogFont* soit utilisé pour la police verticale, FALSE si vous voulez qu’il soit utilisé pour la police horizontale.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Deux polices sont `CMFCMenuBar` utilisées pour tous les objets. Ces polices séparées sont utilisées pour les barres de menu horizontales et verticales.

Les paramètres de police sont `CMFCMenuBar` des variables globales et affectent tous les objets.

## <a name="cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus

Contrôle si une barre de menu affiche les commandes de menu récemment utilisées.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
[dans] Un Boolean qui contrôle si les commandes de menu récemment utilisées sont affichées.

## <a name="cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands

Contrôle si un menu affiche toutes les commandes disponibles.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShowAllCommands (en)*<br/>
[dans] Un paramètre Boolean qui précise si le menu pop-up affiche toutes les commandes du menu.

### <a name="remarks"></a>Notes

Si un menu n’affiche pas toutes les commandes de menu, il cache les commandes qui sont rarement utilisées. Pour plus d’informations sur l’affichage des commandes de menu, voir [CMFCMenuBar Classe](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
