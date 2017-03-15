---
title: Classe de CMFCTasksPane | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTasksPane
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPane class
ms.assetid: b456328e-2525-4642-b78b-9edd1a1a7d3f
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2eb41c24b60bcaea7eadc361c23d5c2273217919
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctaskspane-class"></a>CMFCTasksPane (classe)
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 La classe `CMFCTasksPane` implémente une liste d'éléments interactifs (tâches).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTasksPane : public CDockablePane  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCTasksPane::CMFCTasksPane](#cmfctaskspane)|Construit un objet `CMFCTasksPane`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCTasksPane::AddGroup](#addgroup)|Ajoute un nouveau groupe de tâches au contrôle de volet des tâches.|  
|[CMFCTasksPane::AddLabel](#addlabel)|Ajoute une nouvelle étiquette statique dans le groupe de tâches spécifié.|  
|[CMFCTasksPane::AddMRUFilesList](#addmrufileslist)|Ajoute les tâches spécifiées par une liste de fichiers utilisés récemment (MRU) dans un groupe.|  
|[CMFCTasksPane::AddPage](#addpage)|Ajoute une nouvelle page au volet des tâches.|  
|[CMFCTasksPane::AddSeparator](#addseparator)||  
|[CMFCTasksPane::AddTask](#addtask)|Ajoute une nouvelle tâche au groupe de tâches spécifié.|  
|[CMFCTasksPane::AddWindow](#addwindow)|Ajoute une fenêtre enfant au volet des tâches.|  
|[CMFCTasksPane::CollapseAllGroups](#collapseallgroups)||  
|[CMFCTasksPane::CollapseGroup](#collapsegroup)|Réduit un groupe par programmation.|  
|[CMFCTasksPane::CreateDefaultMiniframe](#createdefaultminiframe)|(Substitue [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe).)|  
|[CMFCTasksPane::CreateMenu](#createmenu)|Appelée par l’infrastructure pour créer un menu pour le **autres volets de tâches** bouton de menu.|  
|[CMFCTasksPane::EnableAnimation](#enableanimation)|Active ou désactive l’animation pendant la réduction ou le développement des groupes de tâches.|  
|[CMFCTasksPane::EnableGroupCollapse](#enablegroupcollapse)|Spécifie si les groupes de tâches peuvent être réduits.|  
|[CMFCTasksPane::EnableHistoryMenuButtons](#enablehistorymenubuttons)|Active ou désactive les menus déroulants de **suivant** et **précédent** boutons de navigation.|  
|[CMFCTasksPane::EnableNavigationToolbar](#enablenavigationtoolbar)|Active ou désactive la barre d'outils de navigation.|  
|[CMFCTasksPane::EnableOffsetCustomControls](#enableoffsetcustomcontrols)||  
|[CMFCTasksPane::EnableScrollButtons](#enablescrollbuttons)|Active les boutons de défilement à la place d'une barre de défilement.|  
|[CMFCTasksPane::EnableWrapLabels](#enablewraplabels)|Active ou désactive le retour automatique à la ligne pour les étiquettes.|  
|[CMFCTasksPane::EnableWrapTasks](#enablewraptasks)|Active ou désactive le retour automatique à la ligne pour les tâches.|  
|[CMFCTasksPane::GetActivePage](#getactivepage)|Retourne l'index de base zéro pour la page active.|  
|[CMFCTasksPane::GetGroupCaptionHeight](#getgroupcaptionheight)|Retourne la hauteur des légendes de groupe.|  
|[CMFCTasksPane::GetGroupCaptionHorzOffset](#getgroupcaptionhorzoffset)|Retourne le décalage actuel d’une légende de groupe par rapport aux bords gauche et droit du volet des tâches.|  
|[CMFCTasksPane::GetGroupCaptionVertOffset](#getgroupcaptionvertoffset)|Retourne le décalage actuel d’une légende de groupe par rapport aux bords supérieur et inférieur du volet des tâches.|  
|[CMFCTasksPane::GetGroupCount](#getgroupcount)|Retourne le nombre total de groupes.|  
|[CMFCTasksPane::GetGroupLocation](#getgrouplocation)|Retourne l'index de groupe interne pour un groupe donné.|  
|[CMFCTasksPane::GetGroupVertOffset](#getgroupvertoffset)|Retourne le décalage vertical d'un groupe.|  
|[CMFCTasksPane::GetHorzMargin](#gethorzmargin)|Retourne l’espacement horizontal entre un volet de tâches et les bords de la zone cliente.|  
|[CMFCTasksPane::GetNextPages](#getnextpages)||  
|[CMFCTasksPane::GetPageByGroup](#getpagebygroup)|Récupère l'index de page pour un groupe spécifié.|  
|[CMFCTasksPane::GetPagesCount](#getpagescount)|Retourne le nombre de pages.|  
|[CMFCTasksPane::GetPreviousPages](#getpreviouspages)||  
|[CMFCTasksPane::GetScrollBarCtrl](#getscrollbarctrl)|(Substitue [CWnd::GetScrollBarCtrl](../../mfc/reference/cwnd-class.md#getscrollbarctrl).)|  
|[CMFCTasksPane::GetTask](#gettask)|Récupère une tâche.|  
|[CMFCTasksPane::GetTaskCount](#gettaskcount)|Retourne le nombre d’éléments de tâche d’un groupe spécifié.|  
|[CMFCTasksPane::GetTaskGroup](#gettaskgroup)|Retourne un groupe de tâches pour un index de groupe donné.|  
|[CMFCTasksPane::GetTaskLocation](#gettasklocation)|Retourne le groupe et l’index pour une tâche donnée.|  
|[CMFCTasksPane::GetTasksHorzOffset](#gettaskshorzoffset)|Retourne le décalage horizontal des tâches entre les bords gauche et droit de leurs groupes parents.|  
|[CMFCTasksPane::GetTasksIconHorzOffset](#gettasksiconhorzoffset)||  
|[CMFCTasksPane::GetTasksIconVertOffset](#gettasksiconvertoffset)||  
|[CMFCTasksPane::GetVertMargin](#getvertmargin)|Retourne l’espacement vertical entre un volet de tâches et les bords de la zone cliente.|  
|[CMFCTasksPane::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Substitue `CDockablePane::IsAccessibilityCompatible`.)|  
|[CMFCTasksPane::IsAnimationEnabled](#isanimationenabled)|Indique si l'animation est activée.|  
|[CMFCTasksPane::IsBackButtonEnabled](#isbackbuttonenabled)|Indique si le bouton Précédent est activé.|  
|[CMFCTasksPane::IsForwardButtonEnabled](#isforwardbuttonenabled)|Indique si le bouton Suivant est activé.|  
|[CMFCTasksPane::IsGroupCollapseEnabled](#isgroupcollapseenabled)||  
|[CMFCTasksPane::IsHistoryMenuButtonsEnabled](#ishistorymenubuttonsenabled)|Indique si le **suivant** et **précédent** boutons de navigation ont des menus déroulants.|  
|[CMFCTasksPane::IsNavigationToolbarEnabled](#isnavigationtoolbarenabled)|Indique si la barre d'outils de navigation est activée.|  
|[CMFCTasksPane::IsToolBox](#istoolbox)||  
|[CMFCTasksPane::IsWrapLabelsEnabled](#iswraplabelsenabled)|Indique si le volet des tâches effectue un retour automatique à la ligne dans les étiquettes.|  
|[CMFCTasksPane::IsWrapTasksEnabled](#iswraptasksenabled)|Indique si le volet des tâches effectue un retour automatique à la ligne dans les tâches.|  
|[CMFCTasksPane::LoadState](#loadstate)|(Substitue [CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917).)|  
|[CMFCTasksPane::OnCancel](#oncancel)||  
|[CMFCTasksPane::OnClickTask](#onclicktask)|Appelé par l’infrastructure quand l’utilisateur clique sur un élément dans le volet des tâches.|  
|[CMFCTasksPane::OnOK](#onok)||  
|[CMFCTasksPane::OnPressBackButton](#onpressbackbutton)|Appelé par l'infrastructure quand l'utilisateur clique sur le bouton Précédent.|  
|[CMFCTasksPane::OnPressForwardButton](#onpressforwardbutton)|Appelé par l'infrastructure quand l'utilisateur clique sur le bouton de navigation Suivant.|  
|[CMFCTasksPane::OnPressHomeButton](#onpresshomebutton)|Appelé par l'infrastructure quand l'utilisateur clique sur le bouton de navigation Accueil.|  
|[CMFCTasksPane::OnPressOtherButton](#onpressotherbutton)||  
|[CMFCTasksPane::OnSetAccData](#onsetaccdata)|(Substitue [CBasePane::OnSetAccData](../../mfc/reference/cbasepane-class.md#onsetaccdata).)|  
|[CMFCTasksPane::OnUpdateCmdUI](#onupdatecmdui)|(Substitue [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0).)|  
|[CMFCTasksPane::PreTranslateMessage](#pretranslatemessage)|(Substitue [CDockablePane::PreTranslateMessage](http://msdn.microsoft.com/en-us/49a242cc-b158-400e-9e01-0345ec9c3ffd).)|  
|[CMFCTasksPane::RecalcLayout](#recalclayout)|(Substitue [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CMFCTasksPane::RemoveAllGroups](#removeallgroups)|Supprime tous les groupes sur la page spécifiée.|  
|[CMFCTasksPane::RemoveAllPages](#removeallpages)|Supprime toutes les pages du volet des tâches à l’exception de la (première) page par défaut.|  
|[CMFCTasksPane::RemoveAllTasks](#removealltasks)|Supprime toutes les tâches du groupe.|  
|[CMFCTasksPane::RemoveGroup](#removegroup)|Supprime un groupe.|  
|[CMFCTasksPane::RemovePage](#removepage)|Supprime une page spécifiée du volet des tâches.|  
|[CMFCTasksPane::RemoveTask](#removetask)|Supprime une tâche d’un groupe de tâches.|  
|[CMFCTasksPane::SaveState](#savestate)|(Substitue [CDockablePane::SaveState](http://msdn.microsoft.com/en-us/c5c24249-8d0d-46cb-96d9-9f5c6dc191db).)|  
|[CMFCTasksPane::Serialize](#serialize)|(Substitue [CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6).)|  
|[CMFCTasksPane::SetActivePage](#setactivepage)|Active une page spécifiée dans le volet des tâches.|  
|[CMFCTasksPane::SetCaption](#setcaption)|Définit le nom de légende d’un volet de tâches.|  
|[CMFCTasksPane::SetGroupCaptionHeight](#setgroupcaptionheight)|Définit la hauteur d'une légende de groupe.|  
|[CMFCTasksPane::SetGroupCaptionHorzOffset](#setgroupcaptionhorzoffset)|Définit le décalage horizontal d'une légende de groupe.|  
|[CMFCTasksPane::SetGroupCaptionVertOffset](#setgroupcaptionvertoffset)|Définit le décalage vertical d'une légende de groupe.|  
|[CMFCTasksPane::SetGroupName](#setgroupname)|Définit un nom de groupe.|  
|[CMFCTasksPane::SetGroupTextColor](#setgrouptextcolor)|Définit la couleur du texte d'une légende de groupe.|  
|[CMFCTasksPane::SetGroupVertOffset](#setgroupvertoffset)|Définit le décalage vertical pour un groupe.|  
|[CMFCTasksPane::SetHorzMargin](#sethorzmargin)|Définit l’espacement horizontal entre un volet de tâches et les bords de la zone cliente.|  
|[CMFCTasksPane::SetIconsList](#seticonslist)|Définit la liste d’images associée aux tâches.|  
|[CMFCTasksPane::SetPageCaption](#setpagecaption)|Définit le texte de légende d’une page de volet de tâches.|  
|[CMFCTasksPane::SetTaskName](#settaskname)|Définit le nom d’une tâche.|  
|[CMFCTasksPane::SetTasksIconHorzOffset](#settasksiconhorzoffset)||  
|[CMFCTasksPane::SetTasksIconVertOffset](#settasksiconvertoffset)||  
|[CMFCTasksPane::SetTaskTextColor](#settasktextcolor)|Définit la couleur du texte d’une tâche.|  
|[CMFCTasksPane::SetTasksHorzOffset](#settaskshorzoffset)|Définit le décalage horizontal des tâches entre les bords gauche et droit de leurs groupes parents.|  
|[CMFCTasksPane::SetVertMargin](#setvertmargin)|Définit l’espacement vertical entre un volet de tâches et les bords de la zone cliente.|  
|[CMFCTasksPane::SetWindowHeight](#setwindowheight)|Définit la hauteur d'une fenêtre.|  
|[CMFCTasksPane::ShowCommandMessageString](#showcommandmessagestring)||  
|[CMFCTasksPane::ShowTask](#showtask)|Affiche ou masque une tâche.|  
|[CMFCTasksPane::ShowTaskByCmdId](#showtaskbycmdid)|Affiche ou masque une tâche en fonction de son ID de commande.|  
|[CMFCTasksPane::Update](#update)|Met à jour les éléments d’interface utilisateur graphique qui appartiennent à un volet de tâches.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCTasksPane::OnActivateTasksPanePage](#onactivatetaskspanepage)|Appelé par l’infrastructure quand une nouvelle page de volet de tâches est activée.|  
  
## <a name="remarks"></a>Remarques  
 La classe `CMFCTasksPane` implémente les fonctionnalités suivantes :  
  
-   Les éléments peuvent être regroupés et chaque regroupement d'éléments peut être associé à une légende.  
  
-   Les regroupements d'éléments peuvent être réduits ou développés.  
  
-   Une icône peut être affectée à chaque élément du volet des tâches.  
  
-   Un élément individuel peut être associé à un ID de commande qui s'exécute quand un utilisateur clique sur l'élément. Quand le clic se produit, le message `WM_COMMAND` est envoyé au propriétaire du contrôle de volet de tâches.  
  
 Pour utiliser le contrôle `CMFCTasksPane` dans votre application, procédez comme suit :  
  
1.  Incorporez un objet `CMFCTasksPane` dans la classe de fenêtre frame principale.  
  
2.  Pendant le traitement du message `WM_CREATE`, appelez la méthode `Create`. Vous pouvez utiliser la mise à jour [CControlBar](../../mfc/reference/ccontrolbar-class.md) styles. Pour plus d'informations, consultez `CControlBar::Create`.  
  
3.  Appelez le [CMFCTasksPane::AddGroup](#addgroup) méthode pour ajouter des groupes différents.  
  
4.  Appelez le [CMFCTasksPane::AddTask](#addtask), [CMFCTasksPane::AddLabel](#addlabel) ou [CMFCTasksPane::AddMRUFilesList](#addmrufileslist) des fonctions membres pour ajouter de nouveaux éléments (tâches) à chaque groupe.  
  
5.  Appelez [CMFCTasksPane::EnableGroupCollapse](#enablegroupcollapse) pour spécifier si les groupes d’éléments peuvent réduire.  
  
 L’illustration suivante représente un contrôle de volet de tâches standard. Le premier groupe est un *spéciale* sa légende et groupes est une couleur sombre. Le troisième groupe est réduit. Le dernier groupe est aligné au bas du volet des tâches et n’a pas de légende ; la dernière tâche du groupe est une simple étiquette :  
  
 ![Exemple de volet de tâches](../../mfc/reference/media/nexttaskpane.png "nexttaskpane")  
  
 Vous pouvez personnaliser l’apparence du volet des tâches en ajustant les marges et les décalages. L'illustration suivante permet de mieux comprendre la fonction de ces variables :  
  
 ![Groupe de tâches personnalisées](../../mfc/reference/media/nexttaskgrpcustom.png "nexttaskgrpcustom")  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment construire un objet `CMFCTasksPane` et utiliser différentes méthodes de la classe `CMFCTasksPane`. L’exemple montre comment activer la réduction de groupes de tâches, d’activer les menus déroulants de la **suivant** et **précédent** boutons de navigation, activer les boutons de défilement au lieu d’une barre de défilement, activer le terme d’habillage du texte dans les étiquettes, définissez le nom de la légende du volet de tâches, définir la couleur du texte de légende du groupe et les marges horizontales et verticales.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#28;](../../mfc/reference/codesnippet/cpp/cmfctaskspane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CMFCTasksPane`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxTasksPane.h  
  
##  <a name="a-nameaddgroupa--cmfctaskspaneaddgroup"></a><a name="addgroup"></a>CMFCTasksPane::AddGroup  
 Ajoute un nouveau groupe de tâches au contrôle de volet des tâches.  
  
```  
int AddGroup(
    int nPageIdx,  
    LPCTSTR lpszGroupName,  
    BOOL bBottomLocation = FALSE,  
    BOOL bSpecial = FALSE,  
    HICON hIcon = NULL);

 
int AddGroup(
    LPCTSTR lpszGroupName,  
    BOOL bBottomLocation = FALSE,  
    BOOL bSpecial = FALSE,  
    HICON hIcon = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nPageIdx`  
 Spécifie l’index de page de base zéro.  
  
 [in] `lpszGroupName`  
 Spécifie le nom du groupe.  
  
 [in] `bBottomLocation`  
 `TRUE`Pour créer le groupe en bas du contrôle de volet Office ; dans le cas contraire, `FALSE`.  
  
 [in] `bSpecial`  
 `TRUE`Pour marquer ce groupe comme un *spéciale* groupe ; sinon, `FALSE`. Pour plus d’informations sur les groupes spéciaux, consultez la section Notes de `CMFCTasksPane`.  
  
 [in] `hIcon`  
 Spécifie l’icône à afficher dans la légende du groupe.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du groupe dans la liste interne des groupes qui tient à jour la classe.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un groupe de tâches et ajoutez ce groupe pour le contrôle de volet Office.  
  
 Le framework affiche les groupes de tâches en haut du contrôle du volet de tâches ou en bas. L’infrastructure peut afficher qu’un seul groupe en bas. ce groupe doit être ajouté en dernier.  
  
##  <a name="a-nameaddlabela--cmfctaskspaneaddlabel"></a><a name="addlabel"></a>CMFCTasksPane::AddLabel  
 Ajoute une étiquette au groupe de tâches spécifié.  
  
```  
int AddLabel(
    int nGroup,  
    LPCTSTR lpszLabelName,  
    int nTaskIcon = -1,  
    BOOL bIsBold = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index du groupe dans lequel l’étiquette est ajoutée.  
  
 [in] `lpszLabelName`  
 Spécifie le nom de l’étiquette.  
  
 [in] `nTaskIcon`  
 Spécifie l’icône à afficher à côté de l’étiquette. Le framework stocke les icônes dans une liste d’images. Ce paramètre est un index dans cette liste.  
  
 [in] `bIsBold`  
 `TRUE`Pour afficher l’étiquette de texte en gras ; dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du groupe dans lequel l’étiquette a été ajoutée, ou -1 si le groupe spécifié par `nGroup` n’existe pas.  
  
### <a name="remarks"></a>Remarques  
 Le framework gère différemment les tâches et les étiquettes. Lorsqu’un utilisateur clique sur une tâche, l’infrastructure exécute une commande. Lorsqu’un utilisateur clique sur une étiquette, aucune commande n’est exécutée. Pour plus d’informations, consultez [CMFCTasksPane::AddTask](#addtask).  
  
##  <a name="a-nameaddmrufileslista--cmfctaskspaneaddmrufileslist"></a><a name="addmrufileslist"></a>CMFCTasksPane::AddMRUFilesList  
 Ajoute une tâche pour chaque fichier stocké dans une liste de fichiers la plus récemment utilisés (MRU) dans un groupe.  
  
```  
int AddMRUFilesList(
    int nGroup,  
    int nMaxFiles = 4);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index d’un groupe. Cette méthode ajoute la dernière liste de fichiers pour le groupe spécifié par ce paramètre.  
  
 [in] `nMaxFiles`  
 Spécifie le nombre de fichiers à afficher dans la liste des derniers fichiers utilisés.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du groupe dans lequel la dernière liste de fichiers a été ajoutée, ou -1 si le groupe spécifié par `nGroup` n’existe pas.  
  
##  <a name="a-nameaddpagea--cmfctaskspaneaddpage"></a><a name="addpage"></a>CMFCTasksPane::AddPage  
 Ajoute une page dans le volet Office.  
  
```  
int AddPage(LPCTSTR lpszPageLabel);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszPageLabel`  
 Spécifie l’étiquette de la page.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de la nouvelle page.  
  
##  <a name="a-nameaddseparatora--cmfctaskspaneaddseparator"></a><a name="addseparator"></a>CMFCTasksPane::AddSeparator  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int AddSeparator(int nGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameaddtaska--cmfctaskspaneaddtask"></a><a name="addtask"></a>CMFCTasksPane::AddTask  
 Ajoute une tâche pour le groupe de tâches spécifié.  
  
```  
int AddTask(
    int nGroup,  
    LPCTSTR lpszTaskName,  
    int nTaskIcon = -1,  
    UINT uiCommandID = 0,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index du groupe dans lequel la tâche est ajoutée.  
  
 [in] `lpszTaskName`  
 Spécifie le nom de la tâche.  
  
 [in] `nTaskIcon`  
 Spécifie l’icône à afficher à côté de la tâche. Le framework stocke les icônes dans une liste d’images. Ce paramètre est un index dans cette liste.  
  
 [in] `uiCommandID`  
 Spécifie l’ID de commande de la commande à exécuter lorsque l’utilisateur clique sur la tâche. La tâche est traitée comme une étiquette si `uiCommandID` est 0.  
  
 [in] `dwUserData`  
 Spécifie les données définies par l’utilisateur à associer à la tâche.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du groupe dans lequel la tâche a été ajoutée, ou -1 si le groupe spécifié par `nGroup` n’existe pas.  
  
##  <a name="a-nameaddwindowa--cmfctaskspaneaddwindow"></a><a name="addwindow"></a>CMFCTasksPane::AddWindow  
 Ajoute une fenêtre enfant au volet des tâches.  
  
```  
int AddWindow(
    int nGroup,  
    HWND hwndTask,  
    int nWndHeight,  
    BOOL bAutoDestroyWindow = FALSE,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index du groupe dans lequel la fenêtre est ajoutée.  
  
 [in] `hwndTask`  
 Spécifie le handle de la fenêtre à ajouter.  
  
 [in] `nWndHeight`  
 Spécifie la hauteur de la fenêtre.  
  
 [in] `bAutoDestroyWindow`  
 `TRUE`Pour détruire la fenêtre lorsque la tâche est supprimée ; dans le cas contraire, `FALSE`.  
  
 [in] `dwUserData`  
 Spécifie les données définies par l’utilisateur associées à la tâche.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du groupe dans lequel la fenêtre a été ajoutée, ou -1 si le groupe spécifié par `nGroup` n’existe pas.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour ajouter un contrôle à un volet de tâches. Par exemple, vous pouvez ajouter un contrôle d’édition qui fonctionne comme une barre de recherche.  
  
##  <a name="a-namecmfctaskspanea--cmfctaskspanecmfctaskspane"></a><a name="cmfctaskspane"></a>CMFCTasksPane::CMFCTasksPane  
 Construit un [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) objet.  
  
```  
CMFCTasksPane();
```  
  
##  <a name="a-namecollapseallgroupsa--cmfctaskspanecollapseallgroups"></a><a name="collapseallgroups"></a>CMFCTasksPane::CollapseAllGroups  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void CollapseAllGroups(BOOL bCollapse = TRUE);

 
void CollapseAllGroups(
    int nPageIdx,  
    BOOL bCollapse);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bCollapse`  
 [in] `nPageIdx`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namecollapsegroupa--cmfctaskspanecollapsegroup"></a><a name="collapsegroup"></a>CMFCTasksPane::CollapseGroup  
 Réduit ou développe un groupe.  
  
```  
BOOL CollapseGroup(
    CMFCTasksPaneTaskGroup* pGroup,  
    BOOL bCollapse = TRUE);

 
BOOL CollapseGroup(
    int nGroup,  
    BOOL bCollapse = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pGroup`  
 Spécifie le groupe à réduire.  
  
 [in] `bCollapse`  
 `TRUE`Pour réduire ce groupe ; `FALSE` pour développer le groupe.  
  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe à réduire dans la liste interne des groupes.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le groupe est réduit ou développe avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Un groupe réduit affiche uniquement la légende du groupe ; la liste des tâches est masquée.  
  
##  <a name="a-namecreatedefaultminiframea--cmfctaskspanecreatedefaultminiframe"></a><a name="createdefaultminiframe"></a>CMFCTasksPane::CreateDefaultMiniframe  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rectInitial`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="a-namecreatemenua--cmfctaskspanecreatemenu"></a><a name="createmenu"></a>CMFCTasksPane::CreateMenu  
 Crée un menu qui s’affiche lorsqu’un utilisateur clique sur le **autres volets de tâches** bouton de menu.  
  
```  
HMENU CreateMenu() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers le nouveau menu.  
  
### <a name="remarks"></a>Remarques  
 Substituez cette méthode dans une classe dérivée pour personnaliser le menu d’un volet Office.  
  
 Le menu contextuel créé par cette méthode contient la liste des pages dans le volet Office. Le menu affiche une case à cocher en regard de la page active.  
  
##  <a name="a-nameenableanimationa--cmfctaskspaneenableanimation"></a><a name="enableanimation"></a>CMFCTasksPane::EnableAnimation  
 Active ou désactive l’animation qui se produit lorsqu’un groupe de tâches développé ou réduit.  
  
```  
void EnableAnimation(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer l’animation qui se produit lorsqu’un groupe de tâches développé ou réduit ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, l’animation qui se produit lorsqu’un groupe de tâches développé ou réduit est activée.  
  
##  <a name="a-nameenablegroupcollapsea--cmfctaskspaneenablegroupcollapse"></a><a name="enablegroupcollapse"></a>CMFCTasksPane::EnableGroupCollapse  
 Spécifie si un utilisateur peut réduire les groupes de tâches.  
  
```  
void EnableGroupCollapse(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Si les utilisateurs peuvent réduire les groupes de tâches ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Un groupe de tâches réduit affiche uniquement la légende du groupe ; la liste des tâches est masquée.  
  
##  <a name="a-nameenablehistorymenubuttonsa--cmfctaskspaneenablehistorymenubuttons"></a><a name="enablehistorymenubuttons"></a>CMFCTasksPane::EnableHistoryMenuButtons  
 Active les menus déroulants sur le **suivant** et **précédent** boutons de navigation.  
  
```  
void EnableHistoryMenuButtons(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer les menus déroulants de la **suivant** et **précédent** boutons de navigation ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, les menus déroulants de la **suivant** et **précédent** boutons sont désactivés.  
  
 Les menus contiennent l’historique de pages de tâches que l’utilisateur a utilisé.  
  
##  <a name="a-nameenablenavigationtoolbara--cmfctaskspaneenablenavigationtoolbar"></a><a name="enablenavigationtoolbar"></a>CMFCTasksPane::EnableNavigationToolbar  
 Active ou désactive la barre d'outils de navigation.  
  
```  
void EnableNavigationToolbar(
    BOOL bEnable = TRUE,  
    UINT uiToolbarBmpRes = 0,  
    CSize sizeToolbarImage = CSize(0,
    0),  
    CSize sizeToolbarButton = CSize(0,
    0));
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer la barre d’outils de navigation ; dans le cas contraire, `FALSE`.  
  
 [in] `uiToolbarBmpRes`  
 Spécifie l’ID de ressource de la bitmap qui contient les images à afficher dans la barre d’outils.  
  
 [in] `sizeToolbarImage`  
 Spécifie la taille d’une image de la barre d’outils.  
  
 [in] `sizeToolbarButton`  
 Spécifie la taille d’un bouton de barre d’outils.  
  
### <a name="remarks"></a>Remarques  
 La barre d’outils de navigation est une barre d’outils affichée par l’infrastructure en haut du volet Office. La barre d’outils de navigation contient le **retour**, **avant**, et **accueil** boutons de navigation et un bouton de menu qui contient la liste des pages disponibles.  
  
 Par défaut, le framework n’affiche pas la barre d’outils de navigation. Si la barre d’outils de navigation n’est pas affichée, les boutons de navigation sont situés sur la légende de la barre d’ancrage.  
  
##  <a name="a-nameenableoffsetcustomcontrolsa--cmfctaskspaneenableoffsetcustomcontrols"></a><a name="enableoffsetcustomcontrols"></a>CMFCTasksPane::EnableOffsetCustomControls  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableOffsetCustomControls(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameenablescrollbuttonsa--cmfctaskspaneenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCTasksPane::EnableScrollButtons  
 Permet de faire défiler des boutons au lieu d’une barre de défilement.  
  
```  
void EnableScrollButtons(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour afficher les boutons de défilement dans le volet Office au lieu d’une barre de défilement. dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, l’infrastructure affiche les boutons de défilement dans le volet Office.  
  
##  <a name="a-nameenablewraplabelsa--cmfctaskspaneenablewraplabels"></a><a name="enablewraplabels"></a>CMFCTasksPane::EnableWrapLabels  
 Active ou désactive le retour du texte dans les étiquettes.  
  
```  
void EnableWrapLabels(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour ajuster le texte dans les étiquettes qui apparaissent dans le volet Office ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, le framework n’encapsule pas le texte des étiquettes. Lorsque le retour est activé, le texte des étiquettes peut apparaître dans plusieurs lignes. L’étiquette peut inclure comme marqueurs de saut de ligne `\n` et la marque de soulignement `&`.  
  
##  <a name="a-nameenablewraptasksa--cmfctaskspaneenablewraptasks"></a><a name="enablewraptasks"></a>CMFCTasksPane::EnableWrapTasks  
 Active ou désactive le retour du texte dans les tâches.  
  
```  
void EnableWrapTasks(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`pour encapsuler des tâches dans le volet Office. dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, le renvoi des tâches est désactivé.  
  
##  <a name="a-namegetactivepagea--cmfctaskspanegetactivepage"></a><a name="getactivepage"></a>CMFCTasksPane::GetActivePage  
 Retourne l'index de base zéro pour la page active.  
  
```  
int GetActivePage() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de la page active.  
  
##  <a name="a-namegetgroupcaptionheighta--cmfctaskspanegetgroupcaptionheight"></a><a name="getgroupcaptionheight"></a>CMFCTasksPane::GetGroupCaptionHeight  
 Retourne la hauteur de la légende du groupe.  
  
```  
int GetGroupCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur de la légende du groupe, en pixels.  
  
##  <a name="a-namegetgroupcaptionhorzoffseta--cmfctaskspanegetgroupcaptionhorzoffset"></a><a name="getgroupcaptionhorzoffset"></a>CMFCTasksPane::GetGroupCaptionHorzOffset  
 Retourne le décalage horizontal de la légende du groupe.  
  
```  
int GetGroupCaptionHorzOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décalage horizontal de la légende du groupe. Le décalage horizontal est la distance en pixels du bord gauche ou droit du volet Office.  
  
##  <a name="a-namegetgroupcaptionvertoffseta--cmfctaskspanegetgroupcaptionvertoffset"></a><a name="getgroupcaptionvertoffset"></a>CMFCTasksPane::GetGroupCaptionVertOffset  
 Retourne le décalage vertical de la légende du groupe.  
  
```  
int GetGroupCaptionVertOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décalage vertical d’une légende de groupe à partir des bords supérieur et inférieur du volet de tâches.  
  
### <a name="remarks"></a>Notes  
 La valeur par défaut pour le décalage vertical est 7 pixels.  
  
##  <a name="a-namegetgroupcounta--cmfctaskspanegetgroupcount"></a><a name="getgroupcount"></a>CMFCTasksPane::GetGroupCount  
 Retourne le nombre total de groupes.  
  
```  
int GetGroupCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre total de groupes dans le volet Office.  
  
##  <a name="a-namegetgrouplocationa--cmfctaskspanegetgrouplocation"></a><a name="getgrouplocation"></a>CMFCTasksPane::GetGroupLocation  
 Retourne l’index de groupe interne pour le groupe spécifié.  
  
```  
BOOL GetGroupLocation(
    CMFCTasksPaneTaskGroup* pGroup,  
    int& nGroup) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pGroup`  
 Spécifie le groupe de tâches dont l’emplacement est récupéré.  
  
 [out] `nGroup`  
 Contient l’index de base zéro du groupe de tâches.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le groupe de tâches a été trouvé ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-namegetgroupvertoffseta--cmfctaskspanegetgroupvertoffset"></a><a name="getgroupvertoffset"></a>CMFCTasksPane::GetGroupVertOffset  
 Retourne le décalage vertical d'un groupe.  
  
```  
int GetGroupVertOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décalage vertical d’un groupe, en pixels.  
  
##  <a name="a-namegethorzmargina--cmfctaskspanegethorzmargin"></a><a name="gethorzmargin"></a>CMFCTasksPane::GetHorzMargin  
 Retourne l’espacement horizontal entre un volet de tâches et le bord de la zone cliente.  
  
```  
int GetHorzMargin() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’espacement horizontal entre un volet de tâches et le bord de la zone cliente.  
  
### <a name="remarks"></a>Remarques  
 L’espacement par défaut entre un volet de tâches et le bord de la zone cliente est de 12 pixels.  
  
##  <a name="a-namegetnextpagesa--cmfctaskspanegetnextpages"></a><a name="getnextpages"></a>CMFCTasksPane::GetNextPages  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetNextPages(CStringList& lstNextPages) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lstNextPages`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namegetpagebygroupa--cmfctaskspanegetpagebygroup"></a><a name="getpagebygroup"></a>CMFCTasksPane::GetPageByGroup  
 Récupère l'index de page pour un groupe spécifié.  
  
```  
BOOL GetPageByGroup(
    int nGroup,  
    int& nPage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe de tâches.  
  
 [out] `nPage`  
 Contient l’index de page pour le groupe spécifié. Si le groupe de tâches contient uniquement une page par défaut, la valeur retournée est 0.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le groupe `nGroup` existe ; sinon, `FALSE`.  
  
##  <a name="a-namegetpagescounta--cmfctaskspanegetpagescount"></a><a name="getpagescount"></a>CMFCTasksPane::GetPagesCount  
 Retourne le nombre de pages.  
  
```  
int GetPagesCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de pages dans le volet Office.  
  
##  <a name="a-namegetpreviouspagesa--cmfctaskspanegetpreviouspages"></a><a name="getpreviouspages"></a>CMFCTasksPane::GetPreviousPages  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetPreviousPages(CStringList& lstPrevPages) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lstPrevPages`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namegetscrollbarctrla--cmfctaskspanegetscrollbarctrl"></a><a name="getscrollbarctrl"></a>CMFCTasksPane::GetScrollBarCtrl  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CScrollBar* GetScrollBarCtrl(int nBar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nBar`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namegettaska--cmfctaskspanegettask"></a><a name="gettask"></a>CMFCTasksPane::GetTask  
 Récupère une tâche.  
  
```  
CMFCTasksPaneTask* GetTask(
    int nGroup,  
    int nTask) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe qui contient la tâche.  
  
 [in] `nTask`  
 Spécifie l’index de base zéro de la tâche dans la liste spécifiée par `nGroup`.  
  
### <a name="return-value"></a>Valeur de retour  
 La tâche à l’index spécifié.  
  
##  <a name="a-namegettaskcounta--cmfctaskspanegettaskcount"></a><a name="gettaskcount"></a>CMFCTasksPane::GetTaskCount  
 Retourne le nombre de tâches dans un groupe spécifié.  
  
```  
int GetTaskCount(int nGroup) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index du groupe de tâches.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de tâches dans le groupe spécifié, ou 0 si `nGroup` n’est pas valide.  
  
##  <a name="a-namegettaskgroupa--cmfctaskspanegettaskgroup"></a><a name="gettaskgroup"></a>CMFCTasksPane::GetTaskGroup  
 Retourne un groupe de tâches pour un index de groupe spécifié.  
  
```  
CMFCTasksPaneTaskGroup* GetTaskGroup(int nGroup) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Le groupe de tâches à l’index spécifié.  
  
##  <a name="a-namegettasklocationa--cmfctaskspanegettasklocation"></a><a name="gettasklocation"></a>CMFCTasksPane::GetTaskLocation  
 Retourne le groupe et l’index d’une tâche spécifique.  
  
```  
BOOL GetTaskLocation(
    UINT uiCommandID,  
    int& nGroup,  
    int& nTask) const;  
  
BOOL GetTaskLocation(
    HWND hwndTask,  
    int& nGroup,  
    int& nTask) const;  
  
BOOL GetTaskLocation(
    CMFCTasksPaneTask* pTask,  
    int& nGroup,  
    int& nTask) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCommandID`  
 Spécifie l’ID de commande de la tâche à rechercher.  
  
 [out] `nGroup`  
 Contient l’index du groupe de la tâche.  
  
 [out] `nTask`  
 Contient l’index de la tâche dans le groupe de tâches.  
  
 [in] `hwndTask`  
 Spécifie la fenêtre associée à la tâche.  
  
 [in] `pTask`  
 Spécifie la tâche à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’emplacement de la tâche a été trouvé ; `FALSE` si la tâche spécifiée n’existe pas.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode récupère l’index de groupe et d’un index de la tâche pour la tâche spécifiée. Si la méthode retourne `FALSE`, `nGroup` et `nTask` ont la valeur -1.  
  
##  <a name="a-namegettaskshorzoffseta--cmfctaskspanegettaskshorzoffset"></a><a name="gettaskshorzoffset"></a>CMFCTasksPane::GetTasksHorzOffset  
 Retourne le décalage horizontal de tâches.  
  
```  
int GetTasksHorzOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décalage horizontal de tâches à partir des bords gauche et droit de leurs groupes parents.  
  
### <a name="remarks"></a>Remarques  
 Le décalage horizontal par défaut des tâches est de 12 pixels.  
  
##  <a name="a-namegettasksiconhorzoffseta--cmfctaskspanegettasksiconhorzoffset"></a><a name="gettasksiconhorzoffset"></a>CMFCTasksPane::GetTasksIconHorzOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksIconHorzOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namegettasksiconvertoffseta--cmfctaskspanegettasksiconvertoffset"></a><a name="gettasksiconvertoffset"></a>CMFCTasksPane::GetTasksIconVertOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksIconVertOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namegetvertmargina--cmfctaskspanegetvertmargin"></a><a name="getvertmargin"></a>CMFCTasksPane::GetVertMargin  
 Retourne la marge verticale entre un volet de tâches et les bords de la zone cliente.  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La marge verticale entre un volet de tâches et les bords de la zone cliente.  
  
### <a name="remarks"></a>Remarques  
 La marge verticale est l’espace entre un volet de tâches et les bords de la zone cliente. La valeur par défaut de la marge verticale est de 12 pixels.  
  
##  <a name="a-nameisaccessibilitycompatiblea--cmfctaskspaneisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CMFCTasksPane::IsAccessibilityCompatible  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="a-nameisanimationenableda--cmfctaskspaneisanimationenabled"></a><a name="isanimationenabled"></a>CMFCTasksPane::IsAnimationEnabled  
 Indique si l'animation est activée.  
  
```  
BOOL IsAnimationEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’animation qui se produit lorsqu’un utilisateur développe ou réduit un groupe est activée ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Appelez [CMFCTasksPane::EnableAnimation](#enableanimation) pour activer ou désactiver l’animation.  
  
##  <a name="a-nameisbackbuttonenableda--cmfctaskspaneisbackbuttonenabled"></a><a name="isbackbuttonenabled"></a>CMFCTasksPane::IsBackButtonEnabled  
 Indique si le bouton Précédent est activé.  
  
```  
BOOL IsBackButtonEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le bouton précédent est activé ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un utilisateur clique sur le bouton précédent, le framework affiche la page précédente de la tâche.  
  
##  <a name="a-nameisforwardbuttonenableda--cmfctaskspaneisforwardbuttonenabled"></a><a name="isforwardbuttonenabled"></a>CMFCTasksPane::IsForwardButtonEnabled  
 Indique si le bouton Suivant est activé.  
  
```  
BOOL IsForwardButtonEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le bouton suivant est activé ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Le bouton suivant permet la navigation vers l’avant dans l’historique de pages de tâches.  
  
##  <a name="a-nameisgroupcollapseenableda--cmfctaskspaneisgroupcollapseenabled"></a><a name="isgroupcollapseenabled"></a>CMFCTasksPane::IsGroupCollapseEnabled  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsGroupCollapseEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameishistorymenubuttonsenableda--cmfctaskspaneishistorymenubuttonsenabled"></a><a name="ishistorymenubuttonsenabled"></a>CMFCTasksPane::IsHistoryMenuButtonsEnabled  
 Indique si le **suivant** et **précédent** boutons de navigation ont des menus déroulants.  
  
```  
BOOL IsHistoryMenuButtonsEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le **suivant** et **précédent** des boutons de navigation ont les menus déroulants ; sinon, `FALSE`.  
  
##  <a name="a-nameisnavigationtoolbarenableda--cmfctaskspaneisnavigationtoolbarenabled"></a><a name="isnavigationtoolbarenabled"></a>CMFCTasksPane::IsNavigationToolbarEnabled  
 Indique si la barre d'outils de navigation est activée.  
  
```  
BOOL IsNavigationToolbarEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la barre d’outils de navigation est activée ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-nameistoolboxa--cmfctaskspaneistoolbox"></a><a name="istoolbox"></a>CMFCTasksPane::IsToolBox  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsToolBox() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameiswraplabelsenableda--cmfctaskspaneiswraplabelsenabled"></a><a name="iswraplabelsenabled"></a>CMFCTasksPane::IsWrapLabelsEnabled  
 Indique si le volet des tâches effectue un retour automatique à la ligne dans les étiquettes.  
  
```  
BOOL IsWrapLabelsEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si les mots dans les étiquettes sont encapsulées ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-nameiswraptasksenableda--cmfctaskspaneiswraptasksenabled"></a><a name="iswraptasksenabled"></a>CMFCTasksPane::IsWrapTasksEnabled  
 Spécifie si l’infrastructure encapsule la chaîne de la tâche.  
  
```  
BOOL IsWrapTasksEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la chaîne de tâche est encapsulée ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-nameloadstatea--cmfctaskspaneloadstate"></a><a name="loadstate"></a>CMFCTasksPane::LoadState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszProfileName`  
 [in] `nIndex`  
 [in] `uiID`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameonactivatetaskspanepagea--cmfctaskspaneonactivatetaskspanepage"></a><a name="onactivatetaskspanepage"></a>CMFCTasksPane::OnActivateTasksPanePage  
 Appelé par l’infrastructure lorsqu’il émet une page du volet tâche active.  
  
```  
virtual void OnActivateTasksPanePage();
```  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour personnaliser l’apparence de la page du volet Office.  
  
##  <a name="a-nameoncancela--cmfctaskspaneoncancel"></a><a name="oncancel"></a>CMFCTasksPane::OnCancel  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameonclicktaska--cmfctaskspaneonclicktask"></a><a name="onclicktask"></a>CMFCTasksPane::OnClickTask  
 Appelé par l’infrastructure quand l’utilisateur clique sur un élément dans le volet des tâches.  
  
```  
virtual void OnClickTask(
    int nGroupNumber,  
    int nTaskNumber,  
    UINT uiCommandID,  
    DWORD dwUserData);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroupNumber`  
 Spécifie l’index de base zéro du groupe qui contient la tâche sélectionnée.  
  
 [in] `nTaskNumber`  
 Spécifie l’index de base zéro de la tâche sélectionnée.  
  
 [in] `uiCommandID`  
 Spécifie l’ID de commande associé à la tâche.  
  
 [in] `dwUserData`  
 Contient des données définies par l’utilisateur associées à la tâche sélectionnée.  
  
### <a name="remarks"></a>Remarques  
 L’infrastructure appelle cette méthode lorsqu’un utilisateur clique sur une tâche. Par défaut, l’infrastructure vérifie l’ID de commande associé à la tâche sélectionnée et si elle n’est pas nulle, envoie le `WM_COMMAND` message au propriétaire du contrôle de volet Office.  
  
 Substituez cette méthode dans une classe dérivée pour exécuter du code personnalisé lorsqu’un clic est effectué sur une tâche.  
  
##  <a name="a-nameonoka--cmfctaskspaneonok"></a><a name="onok"></a>CMFCTasksPane::OnOK  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameonpressbackbuttona--cmfctaskspaneonpressbackbutton"></a><a name="onpressbackbutton"></a>CMFCTasksPane::OnPressBackButton  
 Appelé par l'infrastructure quand l'utilisateur clique sur le bouton Précédent.  
  
```  
virtual void OnPressBackButton();
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, l’infrastructure affiche la page précédemment affichée.  
  
 Substituez cette méthode dans une classe dérivée pour exécuter du code personnalisé lorsque l’utilisateur clique sur le bouton précédent.  
  
##  <a name="a-nameonpressforwardbuttona--cmfctaskspaneonpressforwardbutton"></a><a name="onpressforwardbutton"></a>CMFCTasksPane::OnPressForwardButton  
 Appelé par l'infrastructure quand l'utilisateur clique sur le bouton de navigation Suivant.  
  
```  
virtual void OnPressForwardButton();
```  
  
### <a name="remarks"></a>Remarques  
 Par défaut, l’infrastructure affiche la page affiché par l’utilisateur avant de cliquer sur le **retour** bouton.  
  
 Substituez cette méthode dans une classe dérivée pour exécuter du code personnalisé lorsque l’utilisateur clique sur le bouton suivant.  
  
##  <a name="a-nameonpresshomebuttona--cmfctaskspaneonpresshomebutton"></a><a name="onpresshomebutton"></a>CMFCTasksPane::OnPressHomeButton  
 Appelé par l’infrastructure lorsque l’utilisateur clique sur le bouton de navigation d’accueil.  
  
```  
virtual void OnPressHomeButton();
```  
  
### <a name="remarks"></a>Remarques  
 Par défaut, l’infrastructure affiche la page par défaut pour le groupe de tâches.  
  
 Substituez cette méthode dans une classe dérivée pour exécuter du code personnalisé lorsque l’utilisateur clique sur le bouton de navigation d’accueil.  
  
##  <a name="a-nameonpressotherbuttona--cmfctaskspaneonpressotherbutton"></a><a name="onpressotherbutton"></a>CMFCTasksPane::OnPressOtherButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnPressOtherButton(
    CMFCCaptionMenuButton* pbtn,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pbtn`  
 [in] `pWndOwner`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameonsetaccdataa--cmfctaskspaneonsetaccdata"></a><a name="onsetaccdata"></a>CMFCTasksPane::OnSetAccData  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lVal`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="a-nameonupdatecmduia--cmfctaskspaneonupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCTasksPane::OnUpdateCmdUI  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pTarget`  
 [in] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="a-namepretranslatemessagea--cmfctaskspanepretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCTasksPane::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namerecalclayouta--cmfctaskspanerecalclayout"></a><a name="recalclayout"></a>CMFCTasksPane::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void RecalcLayout(BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bRedraw`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameremoveallgroupsa--cmfctaskspaneremoveallgroups"></a><a name="removeallgroups"></a>CMFCTasksPane::RemoveAllGroups  
 Supprime tous les groupes sur la page spécifiée.  
  
```  
void RemoveAllGroups(int nPageIdx = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nPageIdx`  
 Spécifie l’index de base zéro de la page.  
  
### <a name="remarks"></a>Remarques  
 Supprime tous les groupes sur la page spécifiée par `nPageIdx`, ou tous les groupes s’il existe une page par défaut.  
  
##  <a name="a-nameremoveallpagesa--cmfctaskspaneremoveallpages"></a><a name="removeallpages"></a>CMFCTasksPane::RemoveAllPages  
 Supprime toutes les pages du volet des tâches à l’exception de la (première) page par défaut.  
  
```  
void RemoveAllPages();
```  
  
##  <a name="a-nameremovealltasksa--cmfctaskspaneremovealltasks"></a><a name="removealltasks"></a>CMFCTasksPane::RemoveAllTasks  
 Supprime toutes les tâches du groupe spécifié.  
  
```  
void RemoveAllTasks(int nGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe.  
  
##  <a name="a-nameremovegroupa--cmfctaskspaneremovegroup"></a><a name="removegroup"></a>CMFCTasksPane::RemoveGroup  
 Supprime un groupe.  
  
```  
void RemoveGroup(int nGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe à supprimer.  
  
### <a name="remarks"></a>Notes  
 Cette méthode supprime un groupe unique. Pour supprimer tous les groupes, appelez [CMFCTasksPane::RemoveAllGroups](#removeallgroups) à la place.  
  
 Lorsque le framework supprime un groupe, les tâches utilisateur windows associés sont détruits.  
  
##  <a name="a-nameremovepagea--cmfctaskspaneremovepage"></a><a name="removepage"></a>CMFCTasksPane::RemovePage  
 Supprime une page spécifiée du volet des tâches.  
  
```  
void RemovePage(int nPageIdx);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nPageIdx`  
 Spécifie l’index de base zéro de la page à supprimer.  
  
##  <a name="a-nameremovetaska--cmfctaskspaneremovetask"></a><a name="removetask"></a>CMFCTasksPane::RemoveTask  
 Supprime une tâche d’un groupe de tâches.  
  
```  
BOOL RemoveTask(
    int nGroup,  
    int nTask,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe de tâches contenant la tâche à supprimer.  
  
 [in] `nTask`  
 Spécifie l’index de base zéro de la tâche à supprimer.  
  
 [in] `bRedraw`  
 `TRUE`pour redessiner le volet Office. dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fonction réussit ; `FALSE` si `nGroup` ou `nTask` n’est pas valide.  
  
##  <a name="a-namesavestatea--cmfctaskspanesavestate"></a><a name="savestate"></a>CMFCTasksPane::SaveState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszProfileName`  
 [in] `nIndex`  
 [in] `uiID`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameserializea--cmfctaskspaneserialize"></a><a name="serialize"></a>CMFCTasksPane::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `ar`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namesetactivepagea--cmfctaskspanesetactivepage"></a><a name="setactivepage"></a>CMFCTasksPane::SetActivePage  
 Rend la page spécifiée dans le volet actif.  
  
```  
void SetActivePage(int nPageIdx);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nPageIdx`  
 Spécifie l’index de base zéro de la page à afficher.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode déclare si le `nPageIdx` n’est pas valide.  
  
##  <a name="a-namesetcaptiona--cmfctaskspanesetcaption"></a><a name="setcaption"></a>CMFCTasksPane::SetCaption  
 Définit le nom de légende d’un volet de tâches.  
  
```  
void SetCaption(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszName`  
 Spécifie le nom de la légende.  
  
### <a name="remarks"></a>Remarques  
 Si un volet de tâches comporte plusieurs pages, la page par défaut est la légende qui a été définie à l’aide de cette fonction.  
  
##  <a name="a-namesetgroupcaptionheighta--cmfctaskspanesetgroupcaptionheight"></a><a name="setgroupcaptionheight"></a>CMFCTasksPane::SetGroupCaptionHeight  
 Définit la hauteur d'une légende de groupe.  
  
```  
void SetGroupCaptionHeight(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie la hauteur de la légende.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour personnaliser les marges d’éléments du volet de tâches.  
  
 Si `n` -1, le framework détermine la valeur de la marge à l’aide du Gestionnaire visuel ( `CMFCVisualManager::GetTasksPaneGroupCaptionHeight`). Hauteur de la légende par défaut est 25 pixels.  
  
##  <a name="a-namesetgroupcaptionhorzoffseta--cmfctaskspanesetgroupcaptionhorzoffset"></a><a name="setgroupcaptionhorzoffset"></a>CMFCTasksPane::SetGroupCaptionHorzOffset  
 Définit le décalage horizontal d'une légende de groupe.  
  
```  
void SetGroupCaptionHorzOffset(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie le décalage horizontal de la légende du groupe.  
  
##  <a name="a-namesetgroupcaptionvertoffseta--cmfctaskspanesetgroupcaptionvertoffset"></a><a name="setgroupcaptionvertoffset"></a>CMFCTasksPane::SetGroupCaptionVertOffset  
 Définit le décalage vertical d'une légende de groupe.  
  
```  
void SetGroupCaptionVertOffset(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie le décalage vertical, en pixels, de la légende du groupe.  
  
##  <a name="a-namesetgroupnamea--cmfctaskspanesetgroupname"></a><a name="setgroupname"></a>CMFCTasksPane::SetGroupName  
 Définit un nom de groupe.  
  
```  
BOOL SetGroupName(
    int nGroup,  
    LPCTSTR lpszGroupName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe.  
  
 [in] `lpszGroupName`  
 Spécifie le nom du groupe.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le nom de groupe a été correctement défini ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-namesetgrouptextcolora--cmfctaskspanesetgrouptextcolor"></a><a name="setgrouptextcolor"></a>CMFCTasksPane::SetGroupTextColor  
 Définit la couleur du texte d'une légende de groupe.  
  
```  
BOOL SetGroupTextColor(
    int nGroup,  
    COLORREF color,  
    COLORREF colorHot = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe.  
  
 [in] `color`  
 Spécifie la couleur du texte.  
  
 [in] `colorHot`  
 Spécifie la couleur du texte pour le groupe en surbrillance. Si-1, la couleur de surbrillance par défaut est utilisée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la couleur de texte de groupe a été modifiée avec succès. dans le cas contraire, `FALSE`.  
  
##  <a name="a-namesetgroupvertoffseta--cmfctaskspanesetgroupvertoffset"></a><a name="setgroupvertoffset"></a>CMFCTasksPane::SetGroupVertOffset  
 Définit le décalage vertical pour un groupe.  
  
```  
void SetGroupVertOffset(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie le décalage vertical.  
  
### <a name="remarks"></a>Remarques  
 Le décalage vertical est la distance entre un groupe de tâches et de la bordure du volet de tâches.  
  
 Appelez cette méthode pour personnaliser les marges d’éléments du volet des tâches. Si `n` -1, le framework détermine la valeur de la marge à l’aide du Gestionnaire visuel ( `CMFCVisualManager::GetTasksPaneGroupVertOffset`). Le décalage par défaut est de 15 pixels.  
  
##  <a name="a-namesethorzmargina--cmfctaskspanesethorzmargin"></a><a name="sethorzmargin"></a>CMFCTasksPane::SetHorzMargin  
 Définit la marge horizontale.  
  
```  
void SetHorzMargin(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie la marge, en pixels.  
  
### <a name="remarks"></a>Notes  
 La marge horizontale est la distance entre un volet de tâches et le bord supérieur ou inférieur de la zone cliente.  
  
 Si n est -1, et l’infrastructure détermine la valeur de la marge à l’aide du Gestionnaire visuel ( `CMFCVisualManager::GetTasksPaneHorzMargin`). La marge horizontale par défaut est de 12 pixels.  
  
##  <a name="a-nameseticonslista--cmfctaskspaneseticonslist"></a><a name="seticonslist"></a>CMFCTasksPane::SetIconsList  
 Définit la liste d’images.  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent = RGB(255, 0, 255));  
  
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiImageListResID`  
 Spécifie l’ID de ressource de la liste d’images.  
  
 [in] `cx`  
 Spécifie la taille des icônes dans la liste d’images.  
  
 [in] `clrTransparent`  
 Spécifie la couleur transparente.  
  
 [in] `hIcons`  
 Spécifie la liste d’images qui contient les icônes du volet Office.  
  
### <a name="remarks"></a>Remarques  
 Le framework stocke les icônes dans une liste d’images. Tâches sont associées à des icônes qui sont stockés dans cette liste.  
  
 Cette méthode associe une liste d’images avec le contrôle de volet Office. Pour définir l’icône d’une tâche lorsque vous appelez [CMFCTasksPane::AddTask](#addtask), définissez `nTaskIcon` à l’index de base zéro dans cette liste d’images appropriée.  
  
##  <a name="a-namesetpagecaptiona--cmfctaskspanesetpagecaption"></a><a name="setpagecaption"></a>CMFCTasksPane::SetPageCaption  
 Définit le texte de légende d’une page de volet de tâches.  
  
```  
void SetPageCaption(
    int nPageIdx,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nPageIdx`  
 Spécifie l’index de base zéro de la page.  
  
 [in] `lpszName`  
 Spécifie le texte de légende à afficher sur la page.  
  
### <a name="remarks"></a>Remarques  
 Si un volet de tâches comporte plusieurs pages, la page par défaut est la légende qui a été définie à l’aide de cette méthode.  
  
##  <a name="a-namesettasknamea--cmfctaskspanesettaskname"></a><a name="settaskname"></a>CMFCTasksPane::SetTaskName  
 Définit le nom d’une tâche.  
  
```  
BOOL SetTaskName(
    int nGroup,  
    int nTask,  
    LPCTSTR lpszTaskName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe de tâches.  
  
 [in] `nTask`  
 Spécifie l’index de base zéro de la tâche.  
  
 [in] `lpszTaskName`  
 Spécifie le nom de la tâche.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le nom de la tâche a été correctement défini ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-namesettaskshorzoffseta--cmfctaskspanesettaskshorzoffset"></a><a name="settaskshorzoffset"></a>CMFCTasksPane::SetTasksHorzOffset  
 Définit le décalage horizontal pour les tâches.  
  
```  
void SetTasksHorzOffset(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie le décalage horizontal.  
  
### <a name="remarks"></a>Notes  
 Le décalage horizontal est la distance en pixels des bords gauche et droit d’un groupe.  
  
 Si `n` -1, cette méthode définit le décalage horizontal à la valeur retournée par le `CMFCVisualManager::GetTasksPaneTaskHorzOffset` (méthode).  
  
 Le décalage horizontal par défaut est de 12 pixels.  
  
##  <a name="a-namesettasksiconhorzoffseta--cmfctaskspanesettasksiconhorzoffset"></a><a name="settasksiconhorzoffset"></a>CMFCTasksPane::SetTasksIconHorzOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetTasksIconHorzOffset(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namesettasksiconvertoffseta--cmfctaskspanesettasksiconvertoffset"></a><a name="settasksiconvertoffset"></a>CMFCTasksPane::SetTasksIconVertOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetTasksIconVertOffset(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-namesettasktextcolora--cmfctaskspanesettasktextcolor"></a><a name="settasktextcolor"></a>CMFCTasksPane::SetTaskTextColor  
 Définit la couleur du texte d’une tâche.  
  
```  
BOOL SetTaskTextColor(
    int nGroup,  
    int nTask,  
    COLORREF color,  
    COLORREF colorHot = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe de tâches contenant la tâche.  
  
 [in] `nTask`  
 Spécifie l’index de base zéro de la tâche.  
  
 [in] `color`  
 Spécifie la couleur du texte de la tâche.  
  
 [in] `colorHot`  
 Spécifie la couleur du texte pour le groupe en surbrillance. Si-1, cette méthode utilise la couleur de surbrillance par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la couleur du texte de la tâche a été correctement définie ; dans le cas contraire, `FALSE`.  
  
##  <a name="a-namesetvertmargina--cmfctaskspanesetvertmargin"></a><a name="setvertmargin"></a>CMFCTasksPane::SetVertMargin  
 Définit la marge verticale.  
  
```  
void SetVertMargin(int n = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Spécifie la marge verticale à définir.  
  
### <a name="remarks"></a>Remarques  
 La marge verticale est la distance entre un volet de tâches et les bords verticaux de la zone cliente.  
  
 Si `n` -1, le framework détermine la valeur de la marge à l’aide du Gestionnaire visuel ( `CMFCVisualManager::GetTasksPaneVertMargin`). La marge par défaut est de 12 pixels.  
  
##  <a name="a-namesetwindowheighta--cmfctaskspanesetwindowheight"></a><a name="setwindowheight"></a>CMFCTasksPane::SetWindowHeight  
 Définit la hauteur d’un contrôle de fenêtre.  
  
```  
BOOL SetWindowHeight(
    int nGroup,  
    HWND hwndTask,  
    int nWndHeight);

 
BOOL SetWindowHeight(
    HWND hwndTask,  
    int nWndHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe qui contient le contrôle de fenêtre.  
  
 [in] `hwndTask`  
 Spécifie le handle pour le contrôle de fenêtre.  
  
 [in] `nWndHeight`  
 Spécifie la hauteur définie.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la hauteur du contrôle de fenêtre a été correctement définie ; `FALSE` si `nGroup` n’est pas valide ou si `hwndTask` n’existe pas.  
  
### <a name="remarks"></a>Notes  
 Appelez [CMFCTasksPane::AddWindow](#addwindow) pour ajouter des tâches avec des contrôles de fenêtre.  
  
##  <a name="a-nameshowcommandmessagestringa--cmfctaskspaneshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCTasksPane::ShowCommandMessageString  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmdId`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="a-nameshowtaska--cmfctaskspaneshowtask"></a><a name="showtask"></a>CMFCTasksPane::ShowTask  
 Affiche ou masque une tâche.  
  
```  
BOOL ShowTask(
    int nGroup,  
    int nTask,  
    BOOL bShow = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nGroup`  
 Spécifie l’index de base zéro du groupe.  
  
 [in] `nTask`  
 Spécifie l’index de base zéro de la tâche pour afficher ou masquer.  
  
 [in] `bShow`  
 `TRUE`Pour afficher la tâche. `FALSE` pour masquer la tâche.  
  
 [in] `bRedraw`  
 `TRUE`pour redessiner le volet Office. dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la tâche a été correctement affichée ou masquée ; `FALSE` si le groupe spécifié ou la tâche n’existe pas.  
  
### <a name="remarks"></a>Remarques  
 Utilisez [CMFCTasksPane::ShowTaskByCmdId](#showtaskbycmdid) pour afficher ou masquer une tâche en fonction de son ID de commande.  
  
##  <a name="a-nameshowtaskbycmdida--cmfctaskspaneshowtaskbycmdid"></a><a name="showtaskbycmdid"></a>CMFCTasksPane::ShowTaskByCmdId  
 Affiche ou masque une tâche en fonction de son ID de commande.  
  
```  
BOOL ShowTaskByCmdId(
    UINT uiCommandID,  
    BOOL bShow = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCommandID`  
 Spécifie l’ID de commande de la tâche pour afficher ou masquer.  
  
 [in] `bShow`  
 `TRUE`Pour afficher la tâche. `FALSE` pour masquer la tâche.  
  
 [in] `bRedraw`  
 `TRUE`pour redessiner le volet Office. dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la tâche a été correctement affichée ou masquée ; `FALSE` si une tâche avec l’ID de commande spécifié n’existe pas.  
  
### <a name="remarks"></a>Remarques  
 Utilisez [CMFCTasksPane::ShowTask](#showtask) pour afficher ou masquer une tâche en fonction de son ID de commande.  
  
##  <a name="a-nameupdatea--cmfctaskspaneupdate"></a><a name="update"></a>CMFCTasksPane::Update  
 Actualise tous les contrôles dans un volet Office.  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode met à jour la légende du volet des tâches, ajuste la barre de défilement, repositionne toutes les tâches et redessine tous les contrôles du volet Office.  
  
 Substituez cette méthode dans une classe dérivée pour exécuter du code personnalisé lors de l’infrastructure actualise le volet Office.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPaneTaskGroup (classe)](../../mfc/reference/cmfctaskspanetaskgroup-class.md)   
 [CMFCTasksPaneTask (classe)](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar (classe)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCVisualManager (classe)](../../mfc/reference/cmfcvisualmanager-class.md)

