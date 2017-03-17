---
title: Classe CMDIChildWndEx | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx::ActivateTopLevelFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AdjustDockingLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnMDITabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnTaskBarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnWindowsList
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPaneLeftOf
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableAutoHidePanes
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableDocking
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDockingManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDocumentName
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameIcon
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameText
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabProxyWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarPreviewWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetToolbarButtonToolTipText
- AFXMDICHILDWNDEX/CMDIChildWndEx::InsertPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::InvalidateIconicBitmaps
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsPointNearDockSite
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsReadOnly
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsRegisteredWithTaskbarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarTabsSupportEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicLivePreviewBitmap
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicThumbnail
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnMoveMiniFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnSetPreviewMode
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailStretch
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnUpdateFrameTitle
- AFXMDICHILDWNDEX/CMDIChildWndEx::PaneFromPoint
- AFXMDICHILDWNDEX/CMDIChildWndEx::RecalcLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::RegisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::RemovePaneFromDockManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabActive
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabOrder
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabProperties
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::ShowPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::UnregisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::UpdateTaskbarTabIcon
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWndEx class
- ActivateFrame method
- PreTranslateMessage method
- GetThisClass method
- CreateObject method
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: 35
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 016de8fdade75376f9f081539c0f160a6502bc37
ms.lasthandoff: 02/24/2017

---
# <a name="cmdichildwndex-class"></a>Classe CMDIChildWndEx
La `CMDIChildWndEx` classe fournit les fonctionnalités de Windows fenêtre interface multidocument (MDI) enfant. Il étend les fonctionnalités de [CMDIChildWnd (classe)](../../mfc/reference/cmdichildwnd-class.md). L'infrastructure requiert cette classe lorsqu'une application MDI utilise certaines classes MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](#activatetoplevelframe)|Appelée en interne par l’infrastructure pour activer le frame de niveau supérieur lorsque l’application doit être activée à partir d’un onglet de la barre des tâches.|  
|`CMDIChildWndEx::AddDockSite`|Cette méthode n’est pas utilisée ou implémentée.|  
|[CMDIChildWndEx::AddPane](#addpane)|Ajoute un volet.|  
|[CMDIChildWndEx::AddTabbedPane](#addtabbedpane)|Ajoute un volet à onglets.|  
|[CMDIChildWndEx::AdjustDockingLayout](#adjustdockinglayout)|Ajuste la disposition d’ancrage.|  
|[CMDIChildWndEx::CanShowOnMDITabs](#canshowonmditabs)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](#canshowontaskbartabs)|Indique à l’infrastructure indique si cet enfant MDI peut être affiché sur les onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::CanShowOnWindowsList](#canshowonwindowslist)|Retourne `TRUE` si le nom de fenêtre enfant MDI peut être affiché dans le [CMFCWindowsManagerDialog classe](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) boîte de dialogue. Sinon, retourne `FALSE`.|  
|`CMDIChildWndEx::CreateObject`|Appelé par l’infrastructure pour créer une instance de ce type de classe dynamique.|  
|[CMDIChildWndEx::DockPane](#dockpane)|Ancre un volet.|  
|[CMDIChildWndEx::DockPaneLeftOf](#dockpaneleftof)|Ancre un volet à gauche d’un autre volet.|  
|[CMDIChildWndEx::EnableAutoHidePanes](#enableautohidepanes)|Permet de masquer le mode des volets lorsqu’elles sont ancrées sur les côtés de la fenêtre spécifiées.|  
|[CMDIChildWndEx::EnableDocking](#enabledocking)|L’ancrage de la fenêtre enfant active vers le frame principal.|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](#enabletaskbarthumbnailcliprect)|Active ou désactive la sélection automatique d’une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches.|  
|[CMDIChildWndEx::GetDockingManager](#getdockingmanager)||  
|[CMDIChildWndEx::GetDocumentName](#getdocumentname)|Retourne le nom du document qui s’affiche dans la fenêtre enfant MDI.|  
|[CMDIChildWndEx::GetFrameIcon](#getframeicon)|Appelé par l’infrastructure pour extraire l’icône de fenêtre enfant MDI.|  
|[CMDIChildWndEx::GetFrameText](#getframetext)|Appelée par l’infrastructure pour récupérer le texte de la fenêtre enfant MDI.|  
|[CMDIChildWndEx::GetPane](#getpane)|Recherche d’un volet à l’ID du contrôle spécifié.|  
|[CMDIChildWndEx::GetRelatedTabGroup](#getrelatedtabgroup)||  
|[CMDIChildWndEx::GetTabbedPane](#gettabbedpane)|Retourne un pointeur vers un volet d’ancrage incorporé qui a été converti en un document à onglets.|  
|[CMDIChildWndEx::GetTabProxyWnd](#gettabproxywnd)|Retourne onglet fenêtre proxy inscrit en fait avec les onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](#gettaskbarpreviewwnd)|Appelé par l’infrastructure lorsqu’il doit obtenir une fenêtre enfant (généralement une fenêtre de l’affichage ou le séparateur) à afficher sur la miniature d’onglet barre des tâches Windows 7.|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](#gettaskbarthumbnailcliprect)|Appelé par l’infrastructure lorsqu’il a besoin sélectionner une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches.|  
|`CMDIChildWndEx::GetThisClass`|Appelé par le framework d’obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet associé à ce type de classe.|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Appelé par l’infrastructure pour récupérer une info-bulle pour un bouton de barre d’outils.|  
|[CMDIChildWndEx::InsertPane](#insertpane)|Enregistre le volet spécifié avec le Gestionnaire d’ancrage.|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](#invalidateiconicbitmaps)|Invalide la représentation sous forme de bitmap sous forme d’icône de l’enfant MDI.|  
|[CMDIChildWndEx::IsPointNearDockSite](#ispointneardocksite)|Détermine si un point spécifié est proche du site d’ancrage.|  
|[CMDIChildWndEx::IsReadOnly](#isreadonly)|Retourne `TRUE` si le document est affiché dans la fenêtre enfant est en lecture seule. Sinon, retourne `FALSE`.|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](#isregisteredwithtaskbartabs)|Retourne TRUE si l’enfant MDI a été inscrit avec onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::IsTabbedPane](#istabbedpane)|Retourne `TRUE` si la fenêtre MDI enfant contient un volet d’ancrage. Sinon, retourne `FALSE`.|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](#istaskbartabssupportenabled)|Indique si l’enfant MDI peut apparaître sur les onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](#istaskbarthumbnailcliprectenabled)|Indique si la sélection automatique d’une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches est activée ou désactivée.|  
|[CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags](#m_dwdefaulttaskbartabpropertyflags)|Combinaison d’indicateurs, qui est passée par l’infrastructure à la méthode SetTaskbarTabProperties, lorsqu’un onglet (enfant MDI) est enregistré avec les onglets de la barre des tâches Windows 7. La combinaison de la valeur par défaut est STPF_USEAPPTHUMBNAILWHENACTIVE | STPF_USEAPPPEEKWHENACTIVE.|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](#ongeticoniclivepreviewbitmap)|Appelé par l’infrastructure lorsqu’il doit obtenir une image bitmap pour l’aperçu de l’enfant MDI.|  
|[CMDIChildWndEx::OnGetIconicThumbnail](#ongeticonicthumbnail)|Appelé par l’infrastructure lorsqu’il doit obtenir une image bitmap de miniature sous forme d’icône de l’enfant MDI.|  
|[CMDIChildWndEx::OnMoveMiniFrame](#onmoveminiframe)|Appelé par l’infrastructure pour déplacer une fenêtre mini-frame.|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](#onpresstaskbarthmbnailclosebutton)|Appelé par l’infrastructure lorsque l’utilisateur appuie sur le bouton de fermeture sur la vignette d’onglet de la barre des tâches...|  
|[CMDIChildWndEx::OnSetPreviewMode](#onsetpreviewmode)|Appelé par l’infrastructure pour entrer ou quitter le mode Aperçu avant impression.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](#ontaskbartabthumbnailactivate)|Appelé par l’infrastructure lors de la miniature d’onglet de la barre des tâches doit traiter le message WM_ACTIVATE.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](#ontaskbartabthumbnailmouseactivate)|Appelé par l’infrastructure lors de la miniature d’onglet de la barre des tâches doit traiter le message WM_MOUSEACTIVATE.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](#ontaskbartabthumbnailstretch)|Appelé par l’infrastructure lorsqu’il a besoin d’étendre un bitmap d’aperçu miniatures onglet barre des tâches Windows 7 de l’enfant MDI.|  
|[CMDIChildWndEx::OnUpdateFrameTitle](#onupdateframetitle)|Appelé par l’infrastructure pour mettre à jour le titre du frame. (Substitue `CMDIChildWnd::OnUpdateFrameTitle`.)|  
|[CMDIChildWndEx::PaneFromPoint](#panefrompoint)|Retourne le volet qui contient le point donné.|  
|`CMDIChildWndEx::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour convertir des messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) fonctions de Windows. (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMDIChildWndEx::RecalcLayout](#recalclayout)|Recalcule la disposition de la fenêtre.|  
|[CMDIChildWndEx::RegisterTaskbarTab](#registertaskbartab)|Enregistre l’enfant MDI avec onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|Supprime un volet à partir du Gestionnaire d’ancrage.|  
|[CMDIChildWndEx::SetRelatedTabGroup](#setrelatedtabgroup)||  
|[CMDIChildWndEx::SetTaskbarTabActive](#settaskbartabactive)|Active l’onglet de la barre des tâches Windows 7 correspondant.|  
|[CMDIChildWndEx::SetTaskbarTabOrder](#settaskbartaborder)|Insère l’enfant MDI avant de la fenêtre spécifiée sur les onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabProperties](#settaskbartabproperties)|Définit les propriétés d’un onglet de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](#settaskbarthumbnailcliprect)|Appelé en interne par l’infrastructure pour définir le rectangle de découpage pour sélectionner une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches.|  
|[CMDIChildWndEx::ShowPane](#showpane)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](#unregistertaskbartab)|Supprime l’enfant MDI à partir des onglets de la barre des tâches Windows 7.|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](#updatetaskbartabicon)|Icône de l’onglet barre des tâches Windows 7 des mises à jour.|  
  
## <a name="remarks"></a>Remarques  
 Pour tirer parti des fonctionnalités d’ancrage étendues dans les applications MDI, dérivez la classe de fenêtre enfant MDI de votre application à partir de `CMDIChildWndEx` au lieu de [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant dérive une classe de `CMDIChildWndEx`. Cet extrait de code provient de la [exemple VisualStudioDemo : Application MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo n °&3;](../../mfc/codesnippet/cpp/cmdichildwndex-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxMDIChildWndEx.h  
  
##  <a name="addpane"></a>CMDIChildWndEx::AddPane  
 Ajoute un volet.  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pControlBar`  
 Pointeur vers le volet.  
  
 [in] `bTail`  
 `TRUE`Pour ajouter le volet à la fin de la liste des volets pour le Gestionnaire d’ancrage ; dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet a été inscrit avec le Gestionnaire d’ancrage ; dans le cas contraire, `FALSE`.  
  
##  <a name="addtabbedpane"></a>CMDIChildWndEx::AddTabbedPane  
 Ajoute un volet à onglets.  
  
```  
void AddTabbedPane(CDockablePane* pControlBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pControlBar`  
 Pointeur vers le volet.  
  
##  <a name="adjustdockinglayout"></a>CMDIChildWndEx::AdjustDockingLayout  
 Ajuste la disposition d’ancrage.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hdwp`  
 Handle vers une structure de fenêtre différée.  
  
##  <a name="canshowonmditabs"></a>CMDIChildWndEx::CanShowOnMDITabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanShowOnMDITabs();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="canshowonwindowslist"></a>CMDIChildWndEx::CanShowOnWindowsList  
 Spécifie si le nom de fenêtre enfant MDI peut être affiché dans le [CMFCWindowsManagerDialog classe](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) boîte de dialogue.  
  
```  
virtual BOOL CanShowOnWindowsList();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre peut être affichée dans le **Windows** boîte de dialogue ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée et retourner `FALSE` si la fenêtre ne doit pas être affichée dans le **Windows** boîte de dialogue. Cette fonction est appelée à partir de `CMFCWindowsManagerDialog`.  
  
##  <a name="dockpane"></a>CMDIChildWndEx::DockPane  
 Ancre un volet.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBar`  
 Pointeur vers le volet.  
  
 [in] `nDockBarID`  
 L’ID du volet.  
  
 [in] `lpRect`  
 Pointeur vers un rectangle.  
  
### <a name="remarks"></a>Remarques  
 Le `lpRect` paramètre n’est pas utilisé.  
  
##  <a name="dockpaneleftof"></a>CMDIChildWndEx::DockPaneLeftOf  
 Ancre un volet à gauche d’un autre volet.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBar`  
 Pointeur vers le volet est ancrée.  
  
 `pLeftOf`  
 Pointeur vers le volet qui sert de point de référence.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`en cas de réussite, `FALSE` en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode prend le volet spécifié par `pBar` et s’ancre sur le côté gauche du volet spécifié par `pLeftOf`.  
  
 Appelez cette méthode lorsque vous souhaitez ancrer plusieurs volets dans un ordre prédéfini.  
  
##  <a name="enableautohidepanes"></a>CMDIChildWndEx::EnableAutoHidePanes  
 Permet de masquer le mode des volets lorsqu’elles sont ancrées sur les côtés de la fenêtre spécifiées.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwDockStyle`  
 Spécifie les côtés de la fenêtre frame principale qui est activée. Utiliser une ou plusieurs des indicateurs suivants.  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode réussit ; dans le cas contraire `FALSE`.  
  
##  <a name="enabledocking"></a>CMDIChildWndEx::EnableDocking  
 L’ancrage de la fenêtre enfant active vers le frame principal.  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwDockStyle`  
 Spécifie l’alignement d’ancrage à activer.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode réussit ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour permettre l’alignement d’ancrage au frame principal. Vous pouvez passer d’une combinaison d’indicateurs CBRS_ALIGN_ (pour plus d’informations, consultez [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)).  
  
##  <a name="getdockingmanager"></a>CMDIChildWndEx::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getdocumentname"></a>CMDIChildWndEx::GetDocumentName  
 Retourne le nom du document qui s’affiche dans la fenêtre enfant MDI.  
  
```  
virtual LPCTSTR GetDocumentName(CObject** pObj);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une chaîne qui contient le nom d’un document.  
  
### <a name="remarks"></a>Remarques  
 Un document est ce qu’affiche la fenêtre enfant MDI. En règle générale, la fenêtre affiche les données chargées à partir d’ou enregistrées dans un fichier. Par conséquent, le nom du document est le nom du fichier. L’implémentation par défaut de `GetDocumentName` renvoie une chaîne obtenue à partir de `CDocument::GetPathName`.  
  
 Si la fenêtre affiche un document qui n’est pas chargé à partir d’un fichier, remplacez cette méthode dans une classe dérivée et renvoyer un identificateur de document unique.  
  
 `GetDocumentName`est appelé par l’infrastructure lorsqu’il enregistre l’état de tous les documents ouverts. La chaîne retournée est écrit dans le Registre.  
  
 Lorsque l’infrastructure est état de restauration plus tard, le nom du document est lu à partir du Registre et passé à [CMDIFrameWndEx::CreateDocumentWindow](../../mfc/reference/cmdiframewndex-class.md#createdocumentwindow). Substituez cette méthode dans un [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)-classe dérivée et créer ou ouvrir un document qui porte ce nom et lire le fichier qui porte ce nom. Si le document n’est pas basé sur un fichier, créer le document en fonction de l’identificateur de document proprement dit. Vous devez effectuer les actions précédentes uniquement si vous souhaitez enregistrer et restaurer des documents.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `GetDocumentName`. Cet extrait de code provient de la [exemple VisualStudioDemo : Application MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#17;](../../mfc/codesnippet/cpp/cmdichildwndex-class_2.cpp)]  
  
##  <a name="getframeicon"></a>CMDIChildWndEx::GetFrameIcon  
 Appelé par l’infrastructure pour extraire l’icône de la fenêtre enfant MDI.  
  
```  
virtual HICON GetFrameIcon() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle de l’icône de fenêtre.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure pour déterminer que l’icône à afficher sur l’onglet MDI qui contient la fenêtre frame MDI enfant.  
  
 Par défaut, cette méthode retourne l’icône de fenêtre. Substituer `GetFrameIcon` dans un `CMDIChildWndEx`-personnaliser le comportement de cet classe dérivée.  
  
##  <a name="getframetext"></a>CMDIChildWndEx::GetFrameText  
 Appelée par l’infrastructure pour récupérer le texte de la fenêtre enfant MDI.  
  
```  
virtual CString GetFrameText() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Chaîne qui contient le texte de la fenêtre frame.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure pour déterminer le texte à afficher sous l’onglet MDI qui contient la fenêtre frame MDI enfant.  
  
 Par défaut, cette méthode retourne le texte de la fenêtre. Substituer `GetFrameText` dans un `CMDIChildWndEx`-personnaliser le comportement de cet classe dérivée.  
  
##  <a name="getpane"></a>CMDIChildWndEx::GetPane  
 Recherche d’un volet à l’ID du contrôle spécifié.  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 L’ID de contrôle du volet de recherche.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le volet si trouvée, sinon `NULL`.  
  
##  <a name="getrelatedtabgroup"></a>CMDIChildWndEx::GetRelatedTabGroup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCTabCtrl* GetRelatedTabGroup();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gettabbedpane"></a>CMDIChildWndEx::GetTabbedPane  
 Retourne un pointeur vers un volet d’ancrage qui fait partie d’un groupe de MDI avec onglets de documents.  
  
```  
CDockablePane* GetTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un volet d’ancrage qui fait partie d’un groupe de MDI avec onglets de documents.  
  
##  <a name="gettoolbarbuttontooltiptext"></a>CMDIChildWndEx::GetToolbarButtonToolTipText  
 Appelé par l’infrastructure pour récupérer une info-bulle pour un bouton de barre d’outils.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton*, 
    CString&);
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’info-bulle s’affiche. L'implémentation par défaut retourne la valeur `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Substituez cette méthode si vous souhaitez afficher les astuces personnalisées pour les boutons de barre d’outils.  
  
##  <a name="insertpane"></a>CMDIChildWndEx::InsertPane  
 Enregistre le volet spécifié avec le Gestionnaire d’ancrage.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pControlBar`  
 Pointeur vers le volet à insérer.  
  
 [in] `pTarget`  
 Pointeur vers le volet adjacent.  
  
 [in] `bAfter`  
 Si `TRUE`, `pControlBar` est inséré après `pTarget`. Si `FALSE`, `pControlBar` est inséré avant `pTarget`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode réussit, `FALSE` dans le cas contraire.  
  
##  <a name="ispointneardocksite"></a>CMDIChildWndEx::IsPointNearDockSite  
 Détermine si un point spécifié est proche du site d’ancrage.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Le point spécifié.  
  
 [in] `dwBarAlignment`  
 Spécifie le bord le point est proche. Les valeurs possibles sont `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, et`CBRS_ALIGN_BOTTOM`  
  
 [in] `bOuterEdge`  
 `TRUE`Si le point est proche de la bordure externe du site d’ancrage ; `FALSE` dans le cas contraire.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le point est proche du site d’ancrage ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Le point est proche du site d’ancrage lorsqu’il se trouve dans le respect de la définir dans le Gestionnaire d’ancrage. Le respect de la valeur par défaut est de 15 pixels.  
  
##  <a name="isreadonly"></a>CMDIChildWndEx::IsReadOnly  
 Spécifie si le document est affiché dans la fenêtre enfant est en lecture seule.  
  
```  
virtual BOOL IsReadOnly();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le document est en lecture seule ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction est utilisée pour empêcher l’enregistrement de documents en lecture seule.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre la substitution de la `IsReadOnly` méthode. Cet extrait de code provient de la [exemple VisualStudioDemo : Application MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo n °&2;](../../mfc/codesnippet/cpp/cmdichildwndex-class_3.cpp)]  
  
##  <a name="istabbedpane"></a>CMDIChildWndEx::IsTabbedPane  
 Spécifie si la fenêtre MDI enfant contient un volet d’ancrage.  
  
```  
BOOL IsTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre MDI enfant contient un volet d’ancrage qui a été converti en un document à onglets. dans le cas contraire `FALSE`.  
  
##  <a name="onmoveminiframe"></a>CMDIChildWndEx::OnMoveMiniFrame  
 Appelé par l’infrastructure pour déplacer une fenêtre mini-frame.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pFrame`  
 Pointeur vers une fenêtre mini-frame.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode réussit, sinon `FALSE`.  
  
##  <a name="onsetpreviewmode"></a>CMDIChildWndEx::OnSetPreviewMode  
 Appelé par l’infrastructure pour entrer ou quitter le mode Aperçu avant impression.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bPreview`  
 Si `TRUE`, passer en mode Aperçu avant impression. Si `FALSE`, quitter le mode Aperçu avant impression.  
  
 [in] `pState`  
 Pointeur vers la structure d’état de l’aperçu avant impression.  
  
##  <a name="onupdateframetitle"></a>CMDIChildWndEx::OnUpdateFrameTitle  
 Appelé par l’infrastructure pour mettre à jour le titre du frame.  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bAddToTitle`  
 Si `TRUE`, ajoutez le nom du document au titre.  
  
##  <a name="panefrompoint"></a>CMDIChildWndEx::PaneFromPoint  
 Retourne le volet qui contient le point donné.  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar,  
    CRuntimeClass* pRTCBarType) const;  
  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Spécifie le point, en coordonnées d’écran, à vérifier.  
  
 [in] `nSensitivity`  
 Augmenter la zone de recherche de ce montant. Un volet satisfait les critères de recherche si le point donné se trouve dans la zone accrue.  
  
 [in] `bExactBar`  
 `TRUE`pour ignorer les `nSensitivity` paramètre ; sinon, `FALSE`.  
  
 [in] `pRTCBarType`  
 Si ce n’est pas `NULL`, la méthode recherche uniquement les volets du type spécifié.  
  
 [in] `dwAlignment`  
 Si un volet se trouve au point spécifié, ce paramètre contient le côté du volet qui a été le plus proche du point spécifié. Pour plus d'informations, consultez la section Remarques.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CBasePane`-objet qui contient le point donné, dérivé ou `NULL` si aucun volet a été trouvé.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour déterminer si un volet contient le point spécifié en fonction des conditions spécifiées comme classe d’exécution et la visibilité.  
  
 Lorsque la fonction retourne et un volet a été trouvé, `dwAlignment` contient l’alignement du point spécifié. Par exemple, si le point est la plus proche de la partie supérieure du volet, `dwAlignment` est défini sur `CBRS_ALIGN_TOP`.  
  
##  <a name="recalclayout"></a>CMDIChildWndEx::RecalcLayout  
 Recalcule la disposition de la fenêtre.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bNotify`  
 Si `TRUE`, l’élément actif de la place de la fenêtre reçoit la notification de la modification de la disposition.  
  
##  <a name="removepanefromdockmanager"></a>CMDIChildWndEx::RemovePaneFromDockManager  
 Supprime un volet à partir du Gestionnaire d’ancrage.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pControlBar`  
 Pointeur vers le volet à supprimer.  
  
 [in] `bDestroy`  
 Si `TRUE`, le volet supprimé est détruit.  
  
 [in] `bAdjustLayout`  
 Si `TRUE`, ajuster la disposition d’ancrage immédiatement.  
  
 [in] `bAutoHide`  
 Si `TRUE`, la mise en page d’accueil est liée à la liste des barres de masquage automatique. Si `FALSE`, la mise en page d’accueil est liée à la liste des volets régulières.  
  
 [in] `pBarReplacement`  
 Pointeur vers un volet qui remplace le volet supprimé.  
  
##  <a name="setrelatedtabgroup"></a>CMDIChildWndEx::SetRelatedTabGroup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetRelatedTabGroup(CMFCTabCtrl* p);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `p`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="showpane"></a>CMDIChildWndEx::ShowPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBar`  
 [in] `bShow`  
 [in] `bDelay`  
 [in] `bActivate`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="updatetaskbartabicon"></a>CMDIChildWndEx::UpdateTaskbarTabIcon  
 Met à jour l’icône de tabulation de la barre des tâches Windows 7.  
  
```  
virtual void UpdateTaskbarTabIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 `hIcon`  
 Handle d’une icône à afficher sur l’onglet de la barre des tâches Windows 7.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="unregistertaskbartab"></a>CMDIChildWndEx::UnregisterTaskbarTab  
 Supprime l’enfant MDI d’onglets de la barre des tâches Windows 7.  
  
```  
void UnregisterTaskbarTab(BOOL bCheckRegisteredMDIChildCount = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bCheckRegisteredMDIChildCount`  
 Spécifie si cette fonction doit vérifier le nombre d’enfants MDI enregistré avec les onglets MDI. Si ce nombre est 0, cette fonction supprime le rectangle de découpage de miniature de la barre des tâches de l’application.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="settaskbarthumbnailcliprect"></a>CMDIChildWndEx::SetTaskbarThumbnailClipRect  
 Appelé par l’infrastructure pour définir le rectangle de découpage pour sélectionner une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches.  
  
```  
virtual BOOL SetTaskbarThumbnailClipRect(CRect rect);
```  
  
### <a name="parameters"></a>Paramètres  
 `rect`  
 Spécifie le nouveau rectangle de découpage. Si le rectangle est vide ou null, la capture est supprimée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` en cas de réussite ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settaskbartabproperties"></a>CMDIChildWndEx::SetTaskbarTabProperties  
 Définit les propriétés d’un onglet de la barre des tâches Windows 7.  
  
```  
void SetTaskbarTabProperties(DWORD dwFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Combinaison de valeurs STPFLAG. Pour plus d’informations, consultez [ITaskbarList4::SetTabProperties](http://msdn.microsoft.com/library/dd562049\(vs.85\).aspx).  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="settaskbartaborder"></a>CMDIChildWndEx::SetTaskbarTabOrder  
 Insère l’enfant MDI avant que la fenêtre spécifiée sur les onglets de la barre des tâches Windows 7.  
  
```  
void SetTaskbarTabOrder(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWndBefore`  
 Pointeur vers la fenêtre MDI enfant dont la miniature est insérée à gauche. Cette fenêtre doit être déjà inscrit via `RegisterTaskbarTab`. Si cette valeur est `NULL`, la nouvelle miniature est ajoutée à la fin de la liste.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settaskbartabactive"></a>CMDIChildWndEx::SetTaskbarTabActive  
 Active l’onglet de la barre des tâches Windows 7 correspondant.  
  
```  
void SetTaskbarTabActive();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="registertaskbartab"></a>CMDIChildWndEx::RegisterTaskbarTab  
 Enregistre l’enfant MDI avec onglets de la barre des tâches Windows 7.  
  
```  
virtual void RegisterTaskbarTab(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWndBefore`  
 Pointeur vers la fenêtre MDI enfant dont la miniature est insérée à gauche. Cette fenêtre doit être déjà inscrit via `RegisterTaskbarTab`. Si cette valeur est `NULL`, la nouvelle miniature est ajoutée à la fin de la liste.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ontaskbartabthumbnailstretch"></a>CMDIChildWndEx::OnTaskbarTabThumbnailStretch  
 Appelé par l’infrastructure lorsqu’il a besoin d’étendre une bitmap pour un aperçu de miniature d’onglet barre des tâches de Windows 7 de l’enfant MDI.  
  
```  
virtual BOOL OnTaskbarTabThumbnailStretch(
    HBITMAP hBmpDst,  
    const CRect& rectDst,  
    HBITMAP hBmpSrc,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 `hBmpDst`  
 Handle vers un bitmap de destination.  
  
 `rectDst`  
 Spécifie le rectangle de destination.  
  
 `hBmpSrc`  
 Handle vers une bitmap source.  
  
 `rectSrc`  
 Spécifie le rectangle source.  
  
### <a name="remarks"></a>Notes  
 Requirementher ou lui lui lui lui lui lui lui **:** afxmdichildwndex.h  
  
##  <a name="ontaskbartabthumbnailmouseactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate  
 Appelé par l’infrastructure lors de la miniature d’onglet de la barre des tâches doit traiter le message WM_MOUSEACTIVATE.  
  
```  
virtual int OnTaskbarTabThumbnailMouseActivate(
    CWnd* pDesktopWnd,  
    UINT nHitTest,  
    UINT message);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDesktopWnd`  
 Spécifie un pointeur vers la fenêtre parente de niveau supérieur de la fenêtre en cours d’activation. Le pointeur peut être temporaire et ne doit pas être stocké.  
  
 `nHitTest`  
 Spécifie le code de la zone de test de positionnement. Un test de positionnement est un test qui détermine l’emplacement du curseur.  
  
 `message`  
 Spécifie le nombre de messages de la souris.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut active l’enfant MDI connexe.  
  
##  <a name="ontaskbartabthumbnailactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailActivate  
 Appelé par l’infrastructure lors de la miniature d’onglet de la barre des tâches doit traiter le message WM_ACTIVATE.  
  
```  
virtual void OnTaskbarTabThumbnailActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>Paramètres  
 `nState`  
 Spécifie si la `CWnd` est activé ou désactivé.  
  
 `pWndOther`  
 Pointeur vers le `CWnd` est activée ou désactivée. Le pointeur peut être `NULL`, et il peut être temporaire.  
  
 `bMinimized`  
 Spécifie l’état réduit de la `CWnd` est activée ou désactivée. Valeur `TRUE` indique la fenêtre est réduite.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut active l’enfant MDI connexe.  
  
##  <a name="onpresstaskbarthmbnailclosebutton"></a>CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton  
 Appelé par l’infrastructure lorsque l’utilisateur appuie sur le bouton Fermer sur la miniature d’onglet de la barre des tâches.  
  
```  
virtual void OnPressTaskbarThmbnailCloseButton();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="ongeticonicthumbnail"></a>CMDIChildWndEx::OnGetIconicThumbnail  
 Appelé par l’infrastructure lorsqu’il doit obtenir une image bitmap de la miniature sous forme d’icône de l’enfant MDI.  
  
```  
virtual HBITMAP OnGetIconicThumbnail(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 `nWidth`  
 Spécifie la largeur de la bitmap requise.  
  
 `nHeight`  
 Spécifie la hauteur de la bitmap requise.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ongeticoniclivepreviewbitmap"></a>CMDIChildWndEx::OnGetIconicLivePreviewBitmap  
 Appelé par l’infrastructure lorsqu’il doit obtenir une image bitmap pour l’aperçu de l’enfant MDI.  
  
```  
virtual HBITMAP OnGetIconicLivePreviewBitmap(
    BOOL bIsMDIChildActive,  
    CPoint& ptLocation);
```  
  
### <a name="parameters"></a>Paramètres  
 `bIsMDIChildActive`  
 Ce paramètre est `TRUE` si la bitmap est demandée pour l’enfant MDI, qui est actuellement actif et la fenêtre principale n’est pas réduit. La valeur par défaut dans ce cas de traitement prend un instantané de la fenêtre principale.  
  
 `ptLocation`  
 Spécifie l’emplacement de la bitmap dans le principal (niveau supérieur) coordonnées clientes de fenêtre. Ce point doit être fourni par l’appelé.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le traitement, retourne un handle vers une bitmap 32 BPP valide, sinon `NULL`.  
  
### <a name="remarks"></a>Remarques  
 Substituez cette méthode dans une classe dérivée et retourner une bitmap 32 BPP valide pour l’aperçu de l’enfant MDI. Cette méthode est appelée uniquement lorsque l’enfant MDI est affiché sur les onglets de la barre des tâches Windows 7. Si vous retournez `NULL`, MFC appelle les gestionnaires par défaut et obtient à l’aide de bitmaps `PrintClient` ou `PrintWindow`.  
  
##  <a name="m_dwdefaulttaskbartabpropertyflags"></a>CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags  
 Une combinaison d’indicateurs, qui est passée par l’infrastructure pour le `SetTaskbarTabProperties` la méthode en cours d’enregistrement un onglet (enfant MDI) avec onglets de la barre des tâches Windows 7.  
  
```  
AFX_IMPORT_DATA static DWORD m_dwDefaultTaskbarTabPropertyFlags;  
```  
  
### <a name="remarks"></a>Remarques  
 La combinaison de la valeur par défaut est STPF_USEAPPTHUMBNAILWHENACTIVE | STPF_USEAPPPEEKWHENACTIVE.  
  
##  <a name="istaskbarthumbnailcliprectenabled"></a>CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled  
 Indique si la sélection automatique d’une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches est activée ou désactivée.  
  
```  
BOOL IsTaskbarThumbnailClipRectEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si une partie de la zone du client d’une fenêtre pour afficher la sélection automatique est activée ; sinon `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="istaskbartabssupportenabled"></a>CMDIChildWndEx::IsTaskbarTabsSupportEnabled  
 Indique si l’enfant MDI peut apparaître sur les onglets de la barre des tâches Windows 7.  
  
```  
BOOL IsTaskbarTabsSupportEnabled();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’enfant MDI peut apparaître sur les onglets de la barre des tâches Windows 7 ; `FALSE` si l’enfant MDI ne peut pas apparaître sur les onglets de la barre des tâches Windows 7.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="isregisteredwithtaskbartabs"></a>CMDIChildWndEx::IsRegisteredWithTaskbarTabs  
 Retourne `TRUE` si l’enfant MDI a été inscrit avec onglets de la barre des tâches Windows 7.  
  
```  
BOOL IsRegisteredWithTaskbarTabs();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’enfant MDI est enregistré avec les onglets de la barre des tâches Windows 7 ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="invalidateiconicbitmaps"></a>CMDIChildWndEx::InvalidateIconicBitmaps  
 Invalide une représentation sous forme d’icône bitmap d’un enfant MDI.  
  
```  
BOOL InvalidateIconicBitmaps();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `FALSE` si la prise en charge de la barre des tâches Windows 7 est désactivée ou l’enfant MDI n’est pas enregistré avec les onglets de la barre des tâches Windows 7 ; sinon, retourne `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Doit être appelée lorsque le contenu en direct ou la taille de l’enfant MDI a changé.  
  
##  <a name="gettaskbarthumbnailcliprect"></a>CMDIChildWndEx::GetTaskbarThumbnailClipRect  
 Appelé par l’infrastructure lorsqu’il a besoin sélectionner une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches.  
  
```  
virtual CRect GetTaskbarThumbnailClipRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un rectangle en coordonnées de windows. Ce rectangle est mappé à la zone cliente du frame de niveau supérieur. Le rectangle doit être vide pour effacer le rectangle de découpage.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gettaskbarpreviewwnd"></a>CMDIChildWndEx::GetTaskbarPreviewWnd  
 Appelé par l’infrastructure lorsqu’il doit obtenir une fenêtre enfant (généralement une fenêtre de l’affichage ou le séparateur) à afficher sur une miniature d’onglet de la barre des tâches Windows 7.  
  
```  
virtual CWnd* GetTaskbarPreviewWnd();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Doit retourner un pointeur valide vers une `CWnd` objet, dont aperçu doit être affiché sur un onglet de la barre des tâches Windows 7 lié à cet enfant MDI. L’implémentation par défaut retourne une fenêtre enfant de cet enfant MDI avec l’ID de contrôle AFX_IDW_PANE_FIRST (qui est généralement un `CView`-classe dérivée).  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="gettabproxywnd"></a>CMDIChildWndEx::GetTabProxyWnd  
 Renvoie la fenêtre de proxy onglet enregistrée avec les onglets de la barre des tâches Windows 7.  
  
```  
CMDITabProxyWnd* GetTabProxyWnd();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CMDITabProxyWnd` objet, qui est enregistré avec les onglets de la barre des tâches Windows 7.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="enabletaskbarthumbnailcliprect"></a>CMDIChildWndEx::EnableTaskbarThumbnailClipRect  
 Active ou désactive la sélection automatique d’une partie de la zone du client d’une fenêtre pour afficher en tant que miniature de cette fenêtre dans la barre des tâches.  
  
```  
void EnableTaskbarThumbnailClipRect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bEnable`  
 Spécifie s’il faut activer ( `TRUE`), ou désactiver ( `FALSE`) d’une partie de la zone du client d’une fenêtre pour afficher la sélection automatique.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canshowontaskbartabs"></a>CMDIChildWndEx::CanShowOnTaskBarTabs  
 Indique à l’infrastructure indique si cet enfant MDI peut être affiché sur les onglets de la barre des tâches Windows 7.  
  
```  
virtual BOOL CanShowOnTaskBarTabs();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le contenu de l’enfant MDI peut être affiché sur les miniatures de la barre des tâches Windows 7.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée et retourner `FALSE` de désactiver l’apparence de cet enfant MDI à onglets de la barre des tâches Windows 7.  
  
##  <a name="activatetoplevelframe"></a>CMDIChildWndEx::ActivateTopLevelFrame  
 Appelé par l’infrastructure pour activer le frame de niveau supérieur lorsque l’application est activée à partir d’un onglet de la barre des tâches.  
  
```  
virtual void ActivateTopLevelFrame();
```  
  
### <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd (classe)](../../mfc/reference/cmdichildwnd-class.md)   
 [CMFCWindowsManagerDialog (classe)](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md)

