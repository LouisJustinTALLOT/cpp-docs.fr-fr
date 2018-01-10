---
title: Classe de CMFCMenuBar | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 56e8e97645d4baa74033af07ba08ab2eae0a3557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcmenubar-class"></a>Classe de CMFCMenuBar
Barre de menus qui implémente l'ancrage.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Substitue `CMFCToolBar::AdjustLocations`.)|  
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Spécifie si les étiquettes de texte peuvent être affichées sous les images sur les boutons de barre d’outils. (Substitue [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Calcule la taille horizontale de la barre d’outils. (Substitue [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|  
|[CMFCMenuBar::CalcLayout](#calclayout)|(Substitue `CMFCToolBar::CalcLayout`.)|  
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Calcule la hauteur maximale des boutons de la barre d’outils. (Substitue [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|  
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Spécifie si un utilisateur peut fermer la barre d’outils. (Substitue [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|  
|[CMFCMenuBar::CanBeRestored](#canberestored)|Détermine si le système peut restaurer une barre d’outils à son état d’origine après la personnalisation. (Substitue [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCMenuBar::Create](#create)|Crée un contrôle de menu et l’attache à un `CMFCMenuBar` objet.|  
|[CMFCMenuBar::CreateEx](#createex)|Crée un `CMFCMenuBar` objet avec les options de style supplémentaires.|  
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Initialise un `CMFCMenuBar` objet. Accepte un `HMENU` paramètre qui agit en tant que modèle pour un remplis `CMFCMenuBar`.|  
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Permet à un **aide** zone de liste déroulante qui se trouve sur le côté droit de la barre de menus.|  
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Spécifie s’il faut afficher les ombres pour les menus contextuels.|  
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Substitue [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|  
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Retourne la largeur des boutons de barre d’outils. (Substitue [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|  
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Retourne un handle vers le menu d’origine dans le fichier de ressources.|  
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Retourne l’identificateur de ressource pour le menu d’origine dans le fichier de ressources.|  
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||  
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||  
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Retourne un pointeur vers le **aide** zone de liste déroulante.|  
|[CMFCMenuBar::GetHMenu](#gethmenu)|Retourne le handle vers le menu qui est attaché à la `CMFCMenuBar` objet.|  
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Retourne la police actuelle globale pour les objets de menu.|  
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Retourne le bouton de barre d’outils associé à l’index de l’élément fourni.|  
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Retourne la hauteur des boutons de barre d’outils. (Substitue [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||  
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||  
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||  
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Indique si les éléments de menu désactivés sont mis en surbrillance.|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Détermine si la barre d’outils peut afficher des boutons que vous avez étendu les bordures. (Substitue [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Indique si les éléments désactivés sont mis en surbrillance.|  
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Indique si les ombres sont dessinées pour les menus contextuels.|  
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Indique si les commandes de menu utilisés récemment sont affichées dans la barre de menus.|  
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Indique si les menus contextuels affichent toutes les commandes.|  
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Indique si les menus affichent toutes les commandes après un court délai.|  
|[CMFCMenuBar::LoadState](#loadstate)|Charge l’état de la `CMFCMenuBar` objet à partir du Registre.|  
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Appelé par l’infrastructure lorsqu’un utilisateur sélectionne un bouton dans la barre d’outils. (Substitue [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Appelée par l’infrastructure quand une fenêtre frame charge le menu par défaut du fichier de ressources.|  
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Substitue `CMFCToolBar::OnSendCommand`.)|  
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Appelé par l’infrastructure quand un menu est en mode de personnalisation et l’utilisateur modifie le texte de l’élément de menu.|  
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Substitue `CMFCToolBar::OnToolHitTest`.)|  
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Substitue `CMFCToolBar::PreTranslateMessage`.)|  
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Appelé par l’infrastructure lorsqu’un menu est en mode de personnalisation et de l’utilisateur sélectionne **réinitialiser** pour une barre de menus.|  
|[CMFCMenuBar::SaveState](#savestate)|Enregistre l’état de le `CMFCMenuBar` l’objet dans le Registre.|  
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Définit le menu d’origine dans le fichier de ressources.|  
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||  
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Appelé par l’infrastructure quand une fenêtre enfant MDI change son mode d’affichage. Si la fenêtre enfant MDI est agrandie qui vient d’être ou n’est plus agrandie, cette méthode met à jour la barre de menus.|  
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Définit les informations de classe runtime qui sont générées lorsque l’utilisateur crée dynamiquement des boutons de menu.|  
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Définit la police pour tous les menus de l’application.|  
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Spécifie si une barre de menus affiche les commandes de menu récemment utilisés.|  
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Spécifie si la barre de menus affiche toutes les commandes.|  
  
## <a name="remarks"></a>Notes  
 La `CMFCMenuBar` classe est une barre de menus qui implémente la fonctionnalité d’ancrage. Il s’apparente à une barre d’outils, bien qu’il ne peut pas être fermé, il est toujours affiché.  
  
 `CMFCMenuBar`prend en charge l’option d’affichage des objets d’élément de menu récemment utilisés. Si cette option est activée, la `CMFCMenuBar` affiche uniquement un sous-ensemble des commandes disponibles à première vue. Par la suite, les commandes utilisées récemment sont affichés avec le sous-ensemble d’origine des commandes. En outre, l’utilisateur peut développer toujours le menu pour afficher toutes les commandes disponibles. Par conséquent, chaque commande disponible est configuré pour afficher en permanence, ou pour afficher uniquement s’il a été récemment sélectionné.  
  
 Pour utiliser un `CMFCMenuBar` d’objet, incorporer dans l’objet de frame de fenêtre principale. Lors du traitement de la `WM_CREATE` de message, appelez `CMFCMenuBar::Create` ou `CMFCMenuBar::CreateEx`. Indépendamment de laquelle créer la fonction que vous utilisez, passer un pointeur vers la fenêtre frame principale. Activation de l’ancrage en appelant [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Ancrez ce menu en appelant [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCMenuBar` classe. L’exemple montre comment définir le style du volet, activer le bouton Personnaliser, activer une zone de l’aide, activer des ombres pour les menus contextuels et mettre à jour de la barre de menus. Cet extrait de code fait partie de la [exemple de démonstration d’insertion/éjection](../../visual-cpp-samples.md).  
  
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
 **En-tête :** afxmenubar.h  
  
##  <a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations  
 Ajuste les positions des éléments de menu dans la barre de menus.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels  
 Détermine si les étiquettes de texte sont autorisés sous les images dans la barre de menus.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si l’utilisateur peut choisir d’afficher les étiquettes de texte sous les images.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="calclayout"></a>CMFCMenuBar::CalcLayout  

  
```  
virtual CSize CalcLayout(
    DWORD dwMode,  
    int nLength = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwMode`  
 [in] `nLength`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight  

  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed  

  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canberestored"></a>CMFCMenuBar::CanBeRestored  

  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="create"></a>CMFCMenuBar::Create  
 Crée un contrôle de menu et l’attache à un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID = AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pParentWnd`  
 Pointeur vers la fenêtre parente pour le nouveau `CMFCMenuBar` objet.  
  
 [in] `dwStyle`  
 Style de la nouvelle barre de menus.  
  
 [in] `nID`  
 L’ID de la fenêtre enfant de la barre de menus.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` en cas de réussite ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Après avoir construit un `CMFCMenuBar` de l’objet, vous devez appeler `Create`. Cette méthode crée le `CMFCMenuBar` de contrôle et l’attache à le `CMFCMenuBar` objet.  
  
 Pour plus d’informations sur les styles de barre d’outils, consultez [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).  
  
##  <a name="createex"></a>CMFCMenuBar::CreateEx  
 Crée un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet avec les styles étendus spécifiés.  
  
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
 [in] `pParentWnd`  
 Pointeur vers la fenêtre parente de la nouvelle `CMFCMenuBar` objet.  
  
 [in] `dwCtrlStyle`  
 Styles supplémentaires pour la nouvelle barre de menus.  
  
 [in] `dwStyle`  
 Style de la nouvelle barre de menus principal.  
  
 [in] `rcBorders`  
 A `CRect` paramètre qui spécifie les tailles pour les bordures de la `CMFCMenuBar` objet.  
  
 [in] `nID`  
 L’ID de la fenêtre enfant de la barre de menus.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous devez utiliser cette fonction au lieu de [CMFCMenuBar::Create](#create) lorsque vous souhaitez spécifier des styles, outre le style de la barre d’outils. Certains styles supplémentaires fréquemment utilisées sont `TBSTYLE_TRANSPARENT` et `CBRS_TOP`.  
  
 Pour les listes de styles supplémentaires, consultez [contrôle de barre d’outils et les Styles de bouton](http://msdn.microsoft.com/library/windows/desktop/bb760439), [des styles de contrôle courants](http://msdn.microsoft.com/library/windows/desktop/bb775498), et [les styles de fenêtre courants](http://msdn.microsoft.com/library/windows/desktop/ms632600).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `CreateEx` méthode de la `CMFCMenuBar` classe. Cet extrait de code fait partie de la [exemple de démonstration d’insertion/éjection](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]  
  
##  <a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu  
 Initialise un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet. Les modèles de cette méthode le `CMFCMenuBar` de l’objet après un `HMENU` paramètre.  
  
```  
virtual void CreateFromMenu(
    HMENU hMenu,  
    BOOL bDefaultMenu = FALSE,  
    BOOL bForceUpdate = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hMenu`  
 Handle vers une ressource de menu. `CreateFromMenu`utilise cette ressource en tant que modèle pour le `CMFCMenuBar`.  
  
 [in] `bDefaultMenu`  
 Valeur booléenne qui indique si le nouveau menu est le menu par défaut.  
  
 [in] `bForceUpdate`  
 Valeur booléenne qui indique si cette méthode force une mise à jour de menu.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode si vous souhaitez un contrôle menu ont les mêmes éléments de menu en tant qu’une ressource de menu. Vous appelez cette méthode une fois que vous appelez [CMFCMenuBar::Create](#create) ou [CMFCMenuBar::CreateEx](#createex).  
  
##  <a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox  
 Permet à un **aide** zone de liste déroulante qui se trouve sur le côté droit de la barre de menus.  
  
```  
void EnableHelpCombobox(
    UINT uiID,  
    LPCTSTR lpszPrompt = NULL,  
    int nComboBoxWidth = 150);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiID`  
 L’ID de commande pour le bouton de la **aide** zone de liste déroulante.  
  
 [in] `lpszPrompt`  
 Chaîne qui contient le texte que le framework affiche dans la zone de liste déroulante s’il est vide et non active. Par exemple, « entrez le texte ici ».  
  
 [in] `nComboBoxWidth`  
 La largeur du bouton de la zone de liste déroulante en pixels.  
  
### <a name="remarks"></a>Notes  
 Le **aide** zone de liste modifiable ressemble à la **aide** zone de liste déroulante dans la barre de menus de [!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)].  
  
 Lorsque vous appelez cette méthode avec `uiID` définie sur 0, cette méthode masque la zone de liste déroulante. Sinon, cette méthode affiche automatiquement la zone de liste déroulante située à droite de la barre de menus. Après avoir appelé cette méthode, appelez [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) pour obtenir un pointeur vers le texte inséré [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objet.  
  
##  <a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows  
 Permet d’ombres pour les menus contextuels.  
  
```  
static void EnableMenuShadows(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 Un paramètre booléen qui indique si les ombres doivent être activés pour les menus contextuels.  
  
### <a name="remarks"></a>Notes  
 L’algorithme utilisé par cette méthode est complexe et peut diminuer les performances de votre application sur des systèmes plus lents.  
  
##  <a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize  

  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth  

  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu  
 Récupère un handle vers le menu d’origine. Le framework charge le menu d’origine du fichier de ressources.  
  
```  
HMENU GetDefaultMenu() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers une ressource de menu.  
  
### <a name="remarks"></a>Notes  
 Si votre application personnalise un menu, vous pouvez utiliser cette méthode pour récupérer un handle vers le menu d’origine.  
  
##  <a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId  
 Récupère l’identificateur de ressource pour le menu par défaut.  
  
```  
UINT GetDefaultMenuResId() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur de ressource de menu.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure charge le menu par défaut pour le `CMFCMenuBar` objet à partir du fichier de ressources.  
  
##  <a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection  

  
```  
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pButton`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows  

  
```  
BOOL GetForceDownArrows();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox  
 Retourne un pointeur vers le **aide** zone de liste déroulante.  
  
```  
CMFCToolBarComboBoxButton* GetHelpCombobox();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le **aide** zone de liste déroulante. `NULL`Si le **aide** zone de liste déroulante est masqué ou non activé.  
  
### <a name="remarks"></a>Notes  
 Le **aide** zone de liste déroulante se trouve sur le côté droit de la barre de menus. Appelez la méthode [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) pour activer cette zone de liste déroulante.  
  
##  <a name="gethmenu"></a>CMFCMenuBar::GetHMenu  
 Récupère le handle du menu attaché à la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet.  
  
```  
HMENU GetHMenu() const;  
```  
  
##  <a name="getmenufont"></a>CMFCMenuBar::GetMenuFont  
 Récupère la police du menu actuel.  
  
```  
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bHorz`  
 Un paramètre booléen qui spécifie s’il faut retourner la police horizontale ou verticale. `TRUE`Indique la police horizontale.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [CFont](../../mfc/reference/cfont-class.md) paramètre qui contient la police de barre de menu actuel.  
  
### <a name="remarks"></a>Notes  
 La police retournée est un paramètre global pour l’application. Deux polices sont conservées pour toutes les `CMFCMenuBar` objets. Ces polices distincts sont utilisés pour les barres de menus horizontale et verticale.  
  
##  <a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem  
 Récupère un [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objet sur une barre de menus en fonction de l’index de l’élément.  
  
```  
CMFCToolBarButton* GetMenuItem(int iItem) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iItem`  
 Index de l’élément de menu à retourner.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CMFCToolBarButton` objet qui correspond à l’index spécifié par `iItem`. `NULL`Si l’index n’est pas valide.  
  
##  <a name="getrowheight"></a>CMFCMenuBar::GetRowHeight  

  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton  

  
```  
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,  
    BOOL bByCommand = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiBtn`  
 [in] `bByCommand`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount  

  
```  
int GetSystemButtonsCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu  

  
```  
CMFCToolBarSystemMenuButton* GetSystemMenu() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems  
 Contrôle si le framework met en surbrillance les éléments de menu désactivé.  
  
```  
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bHighlight`  
 Un paramètre booléen qui indique si le framework met en surbrillance les éléments de menu non disponible.  
  
### <a name="remarks"></a>Notes  
 Par défaut, le framework ne met pas en surbrillance des éléments de menu non disponible lorsque l’utilisateur place le pointeur de la souris au-dessus d’eux.  
  
##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeAvailable  

  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems  
 Indique si le framework met en surbrillance les éléments de menu non disponible.  
  
```  
static BOOL IsHighlightDisabledItems();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si les éléments de menu non disponibles sont mis en surbrillance ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, le framework ne met pas en surbrillance des éléments de menu non disponible lorsque l’utilisateur place le pointeur de la souris au-dessus d’eux. Utilisez le [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) méthode pour activer cette fonctionnalité.  
  
##  <a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows  
 Indique si le framework dessine des ombres pour les menus contextuels.  
  
```  
static BOOL IsMenuShadows();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le framework dessine des ombres du menu. dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) méthode pour activer ou désactiver cette fonctionnalité.  
  
##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus  
 Indique si les commandes de menu utilisés récemment sont affichées dans la barre de menus.  
  
```  
static BOOL IsRecentlyUsedMenus();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la `CMFCMenuBar` objet montre récemment utilisé des commandes de menu ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez la fonction [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) pour contrôler si la barre de menus affiche récemment utilisé les commandes de menu.  
  
##  <a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands  
 Indique si les menus affichent toutes les commandes.  
  
```  
static BOOL IsShowAllCommands();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la `CMFCMenuBar` affiche toutes les commandes, sinon 0.  
  
### <a name="remarks"></a>Notes  
 A `CMFCMenuBar` objet peut être configuré pour afficher toutes les commandes ou afficher uniquement un sous-ensemble de commandes. Pour plus d’informations sur cette fonctionnalité, consultez [CMFCMenuBar classe](../../mfc/reference/cmfcmenubar-class.md).  
  
 `IsShowAllCommands`vous indiquera comment cette fonctionnalité est configurée pour la `CMFCMenuBar` objet. Pour contrôler les commandes de menu affichées, utilisez les méthodes [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) et [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).  
  
##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay  
 Indique si le [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet affiche toutes les commandes après un court délai.  
  
```  
static BOOL IsShowAllCommandsDelay();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la barre de menus affiche des menus entiers après un court délai ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous configurez une barre de menus aux éléments d’affichage utilisé récemment, la barre de menus affiche le menu complet de l’une des deux façons :  
  
-   Afficher le menu complet après un délai programmé de lorsque l’utilisateur place le curseur sur la flèche vers le bas du menu.  
  
-   Afficher le menu complet une fois que l’utilisateur clique sur la flèche du bas du menu.  
  
 Par défaut, tous les `CMFCMenuBar` objets utilisent l’option pour afficher le menu complet après un bref délai. Cette option ne peut pas être modifiée par programmation dans le `CMFCMenuBar` classe. Toutefois, un utilisateur peut modifier le comportement pendant la personnalisation de la barre d’outils à l’aide de la **personnaliser** boîte de dialogue...  
  
##  <a name="loadstate"></a>CMFCMenuBar::LoadState  
 Charge l’état de la barre de menus à partir du Registre Windows.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszProfileName`  
 Chaîne qui contient le chemin d’accès d’une clé de Registre Windows.  
  
 [in] `nIndex`  
 L’ID de contrôle de la barre de menus.  
  
 [in] `uiID`  
 Une valeur réservée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CMFCMenuBar::SaveState](#savestate) méthode pour enregistrer l’état de la barre de menus dans le Registre. Les informations enregistrées incluent les éléments de menu, l’état d’ancrage et la position de la barre de menus.  
  
 Dans la plupart des cas votre application n’appelle pas `LoadState`. L’infrastructure appelle cette méthode lors de l’initialisation de l’espace de travail.  
  
##  <a name="onchangehot"></a>CMFCMenuBar::OnChangeHot  

  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iHot`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded  
 L’infrastructure appelle cette méthode lorsqu’il charge la ressource de menu à partir du fichier de ressources.  
  
```  
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hMenu`  
 Le handle pour le menu attaché à la `CMFCMenuBar` objet.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour exécuter du code personnalisé une fois l’infrastructure charge une ressource de menu à partir du fichier de ressources.  
  
##  <a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pButton`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText  
 L’infrastructure appelle cette méthode lorsque l’utilisateur modifie le texte d’un élément sur la barre de menus.  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pButton`  
 Un pointeur vers le [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objet que l’utilisateur peut personnaliser.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’infrastructure applique les modifications de l’utilisateur à la barre de menus ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette méthode modifie le texte du bouton au texte fournies par l’utilisateur.  
  
##  <a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 [in] `pTI`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage  

  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate  
 Appelé par le framework lorsque l’utilisateur sélectionne **réinitialiser** à partir de la **personnaliser** boîte de dialogue.  
  
```  
virtual BOOL RestoreOriginalstate();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque l’utilisateur sélectionne **réinitialiser** à partir du menu de personnalisation. Vous pouvez également appeler cette méthode pour réinitialiser par programme l’état de la barre de menus. Cette méthode charge l’état d’origine du fichier de ressources.  
  
 Substituez cette méthode si vous souhaitez effectuer tout traitement lorsque l’utilisateur sélectionne le **réinitialiser** option.  
  
##  <a name="savestate"></a>CMFCMenuBar::SaveState  
 Enregistre l’état de la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet dans le Registre Windows.  
  
```  
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszProfileName`  
 Chaîne qui contient le chemin d’accès d’une clé de Registre Windows.  
  
 [in] `nIndex`  
 L’ID de contrôle de la barre de menus.  
  
 [in] `uiID`  
 Une valeur réservée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`en cas de réussite ; dans le cas contraire `FALSE`;  
  
### <a name="remarks"></a>Notes  
 En règle générale, votre application n’appelle pas `SaveState`. L’infrastructure appelle cette méthode lorsque l’espace de travail est sérialisé. Pour plus d’informations, consultez [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
 Les informations enregistrées incluent les éléments de menu, l’état d’ancrage et la position de la barre de menus.  
  
##  <a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId  
 Définit le menu par défaut pour un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objet basé sur l’ID de ressource.  
  
```  
void SetDefaultMenuResId(UINT uiResId);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiResId`  
 L’ID de ressource pour le nouveau menu par défaut.  
  
### <a name="remarks"></a>Notes  
 Le [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) méthode restaure le menu par défaut du fichier de ressources.  
  
 Utilisez le [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) pour récupérer le menu par défaut sans être restauré.  
  
##  <a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows  

  
```  
void SetForceDownArrows(BOOL bValue);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bValue`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode  
 L’infrastructure appelle cette méthode lorsqu’une MDI modifie son mode d’affichage et la barre de menus doit être mis à jour.  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bMax`  
 Valeur booléenne qui spécifie le mode. Pour plus d'informations, consultez la section Notes.  
  
 [in] `pWnd`  
 Pointeur vers la fenêtre MDI enfant qui est en cours de modification.  
  
 [in] `bRecalcLayout`  
 Valeur booléenne qui spécifie si la disposition de la barre de menus doit être recalculée immédiatement.  
  
### <a name="remarks"></a>Notes  
 Quand une fenêtre enfant MDI est agrandie, une barre de menus attachée à la fenêtre frame principale MDI affiche le menu système et le **réduire**, **agrandir** et **fermer** boutons. Si `bMax` est `TRUE` et `pWnd` n’est pas `NULL`, la fenêtre enfant MDI est agrandie et la barre de menus doit intégrer les contrôles supplémentaires. Sinon, la barre de menus retourne à son état normal.  
  
##  <a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC  
 Définit les informations de classe runtime par le framework lorsque l’utilisateur crée des boutons de menu.  
  
```  
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMenuButtonRTC`  
 Le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) informations pour une classe dérivée de la [cmfcmenubutton, classe](../../mfc/reference/cmfcmenubutton-class.md).  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un utilisateur ajoute de nouveaux boutons à la barre de menus, l’infrastructure crée les boutons dynamiquement. Par défaut, il crée `CMFCMenuButton` objets. Substituez cette méthode pour modifier le type d’objets de bouton l’infrastructure crée.  
  
##  <a name="setmenufont"></a>CMFCMenuBar::SetMenuFont  
 Définit la police pour toutes les barres de menus dans votre application.  
  
```  
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpLogFont`  
 Un pointeur vers un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/bb773327) structure qui définit la police à définir.  
  
 [in] `bHorz`  
 TRUE si vous voulez le `lpLogFont` paramètre à utiliser pour la police verticale, et FALSE si vous souhaitez pouvoir être utilisé pour les polices horizontales.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Deux polices sont utilisées pour tous les `CMFCMenuBar` objets. Ces polices distincts sont utilisés pour les barres de menus horizontale et verticale.  
  
 Les paramètres de police sont des variables globales et affectent toutes les `CMFCMenuBar` objets.  
  
##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus  
 Contrôle si une barre de menus affiche récemment utilisé les commandes de menu.  
  
```  
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bOn`  
 Valeur booléenne qui contrôle si les commandes de menu utilisés récemment sont affichés.  
  
##  <a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands  
 Contrôle si un menu s’affiche toutes les commandes disponibles.  
  
```  
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bShowAllCommands`  
 Un paramètre booléen qui spécifie si le menu contextuel affiche les commandes de menu.  
  
### <a name="remarks"></a>Notes  
 Si un menu ne s’affiche pas toutes les commandes de menu, elle masque les commandes qui sont rarement utilisées. Pour plus d’informations sur l’affichage des commandes de menu, consultez [CMFCMenuBar classe](../../mfc/reference/cmfcmenubar-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
