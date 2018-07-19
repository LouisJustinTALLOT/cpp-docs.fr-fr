---
title: CFrameWnd, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
dev_langs:
- C++
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d2dee6c5157858fef2bd26101ac128ff3d53d23
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337380"
---
# <a name="cframewnd-class"></a>CFrameWnd (classe)
Fournit les fonctionnalités d'une fenêtre frame contextuelle ou superposée d'interface monodocument (SDI) Windows, ainsi que des membres permettant de gérer la fenêtre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](#cframewnd)|Construit un objet `CFrameWnd`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|Rend le frame visible et accessible à l’utilisateur.|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|Définit la fenêtre frame modal.|  
|[CFrameWnd::Create](#create)|Appel pour créer et initialiser la fenêtre frame Windows associée le `CFrameWnd` objet.|  
|[CFrameWnd::CreateView](#createview)|Crée une vue dans un frame qui n’est pas dérivé `CView`.|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Ancre une barre de contrôle.|  
|[CFrameWnd::EnableDocking](#enabledocking)|Permet à une barre de contrôle d’être ancrée.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Termine un état modal de la fenêtre frame. Permet à toutes les fenêtres désactivées par `BeginModalState`.|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Flotte une barre de contrôle.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Retourne l’actif `CDocument` objet.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Retourne l’actif `CFrameWnd` objet.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Retourne l’actif `CView` objet.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Récupère la barre de contrôle.|  
|[CFrameWnd::GetDockState](#getdockstate)|Récupère l’état d’ancrage d’une fenêtre frame.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Récupère l’état d’affichage du menu de l’application MFC en cours.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indique si le comportement par défaut du menu de l’application MFC actuelle est masquée ou visible.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Retourne un pointeur vers l’état de la barre appartenant à la fenêtre frame.|  
|[CFrameWnd::GetMessageString](#getmessagestring)|Récupère le message correspondant à un ID de commande.|  
|[CFrameWnd::GetTitle](#gettitle)|Récupère le titre de la barre de contrôle associée.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Provoque le `OnInitialUpdate` fonction membre appartenant à toutes les vues dans la fenêtre frame à appeler.|  
|[CFrameWnd::InModalState](#inmodalstate)|Retourne une valeur indiquant si une fenêtre frame est dans un état modal.|  
|[CFrameWnd::IsTracking](#istracking)|Détermine si la barre de fractionnement est en cours de déplacement.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|L’appel pour charger une table d’accélérateurs.|  
|[CFrameWnd::LoadBarState](#loadbarstate)|L’appel à restaurer les paramètres de barre de contrôle.|  
|[CFrameWnd::LoadFrame](#loadframe)|L’appel pour créer dynamiquement une fenêtre frame à partir des informations sur les ressources.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Négocie l’espace de bordure dans la fenêtre frame.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Appelée chaque fois qu’une action est effectuée dans la barre de contrôle spécifié.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Gère MAJ + F1 Aide pour les éléments de la place.|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Définit la fenêtre frame principale de l’application dans et hors du mode d’aperçu avant impression.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Appelé par le framework lorsque le menu associé est mis à jour.|  
|[CFrameWnd::RecalcLayout](#recalclayout)|Repositionne les barres de contrôle de la `CFrameWnd` objet.|  
|[CFrameWnd::SaveBarState](#savebarstate)|L’appel à enregistrer les paramètres de barre de contrôle.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Désigne la vue spécifiée à la vue active pour l’aperçu riche.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Définit l’actif `CView` objet.|  
|[CFrameWnd::SetDockState](#setdockstate)|Appel pour ancrer la fenêtre frame dans la fenêtre principale.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Définit l’état d’affichage du menu dans l’application MFC actuelle masqué ou affiché.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Définit le comportement par défaut du menu dans l’application MFC actuelle pour être masquées ou visibles.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Définit le texte d’une barre d’état standard.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Définit la position actuelle pour la barre de progression Windows 7 sur la barre des tâches.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Définit la plage de barre de progression Windows 7 sur la barre des tâches.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Définit le type et l’état de l’indicateur de progression affichée sur un bouton de barre des tâches.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Surchargé. S’applique à une superposition à un bouton de barre des tâches pour indiquer l’état de l’application ou une notification à l’utilisateur.|  
|[CFrameWnd::SetTitle](#settitle)|Définit le titre de la barre de contrôle associée.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|L’appel pour afficher la barre de contrôle.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Affiche toutes les fenêtres qui sont des descendants de le `CFrameWnd` objet.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crée une fenêtre de client pour le frame.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Appelé avant que le menu de l’application MFC actuelle est masqué.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Appelé avant que le menu de l’application MFC en cours s’affiche.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Contrôles automatique activer et désactiver la fonctionnalité pour les éléments de menu.|  
|[CFrameWnd::rectDefault](#rectdefault)|Passer ce statique `CRect` en tant que paramètre lorsque vous créez un `CFrameWnd` objet pour autoriser Windows à choisir la taille initiale et la position de la fenêtre.|  
  
## <a name="remarks"></a>Notes  
 Pour créer une fenêtre frame utiles pour votre application, dérivez une classe de `CFrameWnd`. Ajoutez des variables membres à la classe dérivée pour stocker les données propres à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.  
  
 Il existe trois manières de construire une fenêtre frame :  
  
-   Construire directement à l’aide de [créer](#create).  
  
-   Construire directement à l’aide de [LoadFrame](#loadframe).  
  
-   Indirectement le générer à l’aide d’un modèle de document.  
  
 Avant d’appeler soit `Create` ou `LoadFrame`, vous devez construire l’objet de fenêtre frame sur le tas à l’aide de C++ **nouveau** opérateur. Avant d’appeler `Create`, vous pouvez également enregistrer une classe de fenêtre avec le [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) fonction globale pour définir les styles d’icône et de classe pour le frame.  
  
 Utilisez le `Create` fonction membre pour passer des arguments comme immédiats de paramètres de création de l’image.  
  
 `LoadFrame` nécessite moins d’arguments que `Create`et récupère à la place de la plupart de ses valeurs par défaut à partir de ressources, y compris la légende du frame, icône, table d’accélérateurs et menu. Pour être accessible par `LoadFrame`, toutes ces ressources doivent avoir le même ID de ressource (par exemple, IDR_MAINFRAME).  
  
 Quand un `CFrameWnd` objet contient des vues et des documents, elles sont créées indirectement par le framework au lieu de directement par le programmeur. Le `CDocTemplate` objet orchestre la création de l’image, la création des vues contenants et la connexion des vues au document approprié. Les paramètres de la `CDocTemplate` constructeur spécifie le `CRuntimeClass` des trois classes impliquées (document, le frame et affichage). Un `CRuntimeClass` objet est utilisé par l’infrastructure pour créer dynamiquement des nouvelles images lorsque spécifié par l’utilisateur (par exemple, en utilisant la commande fichier nouveau ou la commande de nouvelle fenêtre d’interface (multidocument MDI) document plusieurs).  
  
 Une classe de fenêtre frame dérivée de `CFrameWnd` doit être déclaré avec DECLARE_DYNCREATE afin que le mécanisme RUNTIME_CLASS ci-dessus fonctionne correctement.  
  
 Un `CFrameWnd` contient des implémentations par défaut pour effectuer les fonctions suivantes d’une fenêtre principale dans une application pour Windows :  
  
-   Un `CFrameWnd` fenêtre frame effectue le suivi d’une vue actuellement active est indépendante de la fenêtre active de Windows ou le focus d’entrée actuel. Lorsque le frame est réactivé, la vue active est notifiée en appelant `CView::OnActivateView`.  
  
-   Commande de messages et nombreux messages de notification de frame courants, y compris celles gérées par le `OnSetFocus`, `OnHScroll`, et `OnVScroll` fonctions de `CWnd`, sont déléguées par un `CFrameWnd` fenêtre frame à la vue actuellement active.  
  
-   La vue actuellement active (ou la fenêtre de frame MDI enfant active dans le cas d’un frame MDI) peut déterminer la légende de la fenêtre frame. Cette fonctionnalité peut être désactivée en désactivant le bit de style FWS_ADDTOTITLE de la fenêtre frame.  
  
-   Un `CFrameWnd` fenêtre frame gère le positionnement des barres de contrôles, des vues et des autres fenêtres enfants à l’intérieur de la zone fenêtre frame du client. Une fenêtre frame effectue également la mise à jour de durée d’inactivité de la barre d’outils et d’autres boutons de barre de contrôle. Un `CFrameWnd` fenêtre frame a également des implémentations par défaut des commandes pour activer et désactiver la barre d’outils et barre d’état.  
  
-   Un `CFrameWnd` fenêtre frame gère la barre de menus principale. Quand un menu contextuel s’affiche, la fenêtre frame utilise le mécanisme UPDATE_COMMAND_UI pour déterminer quels éléments de menu doivent être activés, désactivés ou activés. Lorsque l’utilisateur sélectionne un élément de menu, la fenêtre frame met à jour la barre d’état avec la chaîne de message pour cette commande.  
  
-   Un `CFrameWnd` fenêtre frame a une table d’accélérateurs facultative qui convertit automatiquement les accélérateurs de clavier.  
  
-   Un `CFrameWnd` fenêtre frame a un ID d’aide facultatif défini avec `LoadFrame` qui est utilisé pour l’aide contextuelle. Une fenêtre frame est l’orchestrateur principal des États semi-modaux tels que l’aide contextuelle (MAJ + F1) et les modes d’aperçu avant impression.  
  
-   Un `CFrameWnd` fenêtre frame s’ouvre un fichier à partir du Gestionnaire de fichier glisser -déplacer sur la fenêtre frame. Si une extension de fichier est enregistrée et associée à l’application, la fenêtre frame répond à la demande d’ouverture dynamique de données (DDE) exchange qui se produit lorsque l’utilisateur ouvre un fichier de données dans le Gestionnaire de fichiers ou le `ShellExecute` Windows fonction est appelée.  
  
-   Si la fenêtre frame est la fenêtre principale de l’application (autrement dit, `CWinThread::m_pMainWnd`), lorsque l’utilisateur ferme l’application, la fenêtre frame invite l’utilisateur à enregistrer les documents modifiés (pour `OnClose` et `OnQueryEndSession`).  
  
-   Si la fenêtre frame est la fenêtre principale de l’application, la fenêtre frame est le contexte pour l’exécution de WinHelp. Fermeture de la fenêtre frame s’arrêtera WINHELP. EXE si elle a été lancé pour l’aide de cette application.  
  
 N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame. Utilisez plutôt `CWnd::DestroyWindow`. Le `CFrameWnd` implémentation de `PostNcDestroy` supprime l’objet C++ lorsque la fenêtre est détruite. Lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut `OnClose` Gestionnaire appellera `DestroyWindow`.  
  
 Pour plus d’informations sur `CFrameWnd`, consultez [Frame Windows](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame  
 Appelez cette fonction membre pour activer et de restaurer la fenêtre frame afin qu’il soit visible et accessible à l’utilisateur.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCmdShow*  
 Spécifie le paramètre à passer à [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Par défaut, le frame est indiqué et correctement restauré.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est généralement appelée après un événement sans interface utilisateur comme DDE, OLE ou tout autre événement qui peut afficher la fenêtre frame ou son contenu à l’utilisateur.  
  
 L’implémentation par défaut active le frame amène au haut de l’ordre de plan et, si nécessaire, exécute les mêmes étapes pour la fenêtre frame principale de l’application.  
  
 Remplacez cette fonction membre pour modifier la manière d’activer un frame. Par exemple, vous pouvez forcer des fenêtres MDI enfants à être agrandi. Ajouter la fonctionnalité appropriée, puis appelez la version de la classe de base avec un texte explicite *nCmdShow*.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState  
 Appelez cette fonction membre pour rendre modale une fenêtre frame.  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd  
 Construit un `CFrameWnd` de l’objet, mais ne crée pas de la fenêtre frame visible.  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>Notes  
 Appelez `Create` pour créer la fenêtre visible.  
  
##  <a name="create"></a>  CFrameWnd::Create  
 Appel pour créer et initialiser la fenêtre frame Windows associée le `CFrameWnd` objet.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CWnd* pParentWnd = NULL,  
    LPCTSTR lpszMenuName = NULL,  
    DWORD dwExStyle = 0,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszClassName*  
 Pointe vers une chaîne de caractères se terminant par null qui nomme la classe Windows. Le nom de classe peut être n’importe quel nom inscrit avec le `AfxRegisterWndClass` fonction globale ou `RegisterClass` (fonction) Windows. Si NULL, utilise la valeur par défaut prédéfinie `CFrameWnd` attributs.  
  
 *lpszWindowName*  
 Pointe vers une chaîne de caractères se terminant par null qui représente le nom de la fenêtre. Utilisé en tant que texte pour la barre de titre.  
  
 *dwStyle*  
 Spécifie la fenêtre [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) attributs. Inclure le style FWS_ADDTOTITLE si vous souhaitez que la barre de titre pour afficher automatiquement le nom du document représenté dans la fenêtre.  
  
 *Rect*  
 Spécifie la taille et la position de la fenêtre. Le *rectDefault* valeur permet à Windows spécifier la taille et la position de la nouvelle fenêtre.  
  
 *pParentWnd*  
 Spécifie la fenêtre parente de cette fenêtre frame. Ce paramètre doit être NULL pour les fenêtres frame de niveau supérieur.  
  
 *lpszMenuName*  
 Identifie le nom de la ressource de menu à utiliser avec la fenêtre. Utilisez MAKEINTRESOURCE si le menu a un ID d’entier plutôt qu’une chaîne. Ce paramètre peut être NULL.  
  
 *dwExStyle*  
 Spécifie la fenêtre étendue [style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) attributs.  
  
 *pContext*  
 Spécifie un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure. Ce paramètre peut être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’initialisation aboutit ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Construire un `CFrameWnd` objet en deux étapes. Tout d’abord, appeler le constructeur, ce qui construit la `CFrameWnd` de l’objet, puis appelez `Create`, qui crée la fenêtre frame Windows et l’attache à la `CFrameWnd` objet. `Create` Initialise le nom de la classe de la fenêtre et le nom de la fenêtre et enregistre les valeurs par défaut pour son style, le parent et le menu associé.  
  
 Utilisez `LoadFrame` plutôt que `Create` pour charger la fenêtre frame d’une ressource au lieu de spécifier ses arguments.  
  
##  <a name="createview"></a>  CFrameWnd::CreateView  
 Appelez `CreateView` pour créer une vue dans un frame.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Paramètres  
 *pContext*  
 Spécifie le type d’affichage et du document.  
  
 *nID*  
 Numéro d’identification d’une vue.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un `CWnd` objet en cas de réussite ; sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre pour créer « vues » qui ne sont pas `CView`-dérivées au sein d’un frame. Après avoir appelé `CreateView`, vous devez manuellement la valeur de la vue active et configurez-le pour être visible ; ces tâches ne sont pas effectuées automatiquement par `CreateView`.  
  
##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar  
 Provoque une barre de contrôle être ancré à la fenêtre frame.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pBar*  
 Pointe vers la barre de contrôle d’être ancrée.  
  
 *nDockBarID*  
 Détermine les côtés de la fenêtre frame à prendre en compte pour l’ancrage. Il peut être 0, ou un ou plusieurs des opérations suivantes :  
  
- Ancrage de AFX_IDW_DOCKBAR_TOP pour le côté supérieur de la fenêtre frame.  
  
- Ancrage de AFX_IDW_DOCKBAR_BOTTOM pour le côté inférieur de la fenêtre frame.  
  
- Ancrage de AFX_IDW_DOCKBAR_LEFT vers le côté gauche de la fenêtre frame.  
  
- AFX_IDW_DOCKBAR_RIGHT l’ancrer à droite de la fenêtre frame.  
  
 Si 0, la barre de contrôle peut être ancrée sur n’importe quel côté activée pour l’ancrage dans la fenêtre frame de destination.  
  
 *lpRect*  
 Détermine, en coordonnées d’écran, où la barre de contrôle sera ancrée dans la zone non cliente de la fenêtre frame de destination.  
  
### <a name="remarks"></a>Notes  
 La barre de contrôle sera ancrée à un des côtés de la fenêtre frame spécifié dans les appels à la fois aux [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) et [CFrameWnd::EnableDocking](#enabledocking). Le choisi côté est déterminé par *nDockBarID*.  
  
##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking  
 Appelez cette fonction pour activer les barres de contrôle dans une fenêtre frame.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDockStyle*  
 Spécifie les côtés de la fenêtre frame pouvant servir d’ancrage de sites pour les barres de contrôle. Il peut être une ou plusieurs des opérations suivantes :  
  
- CBRS_ALIGN_TOP permet d’ancrage en haut de la zone cliente.  
  
- CBRS_ALIGN_BOTTOM permet d’ancrage en bas de la zone cliente.  
  
- CBRS_ALIGN_LEFT permet d’ancrage sur le côté gauche de la zone cliente.  
  
- CBRS_ALIGN_RIGHT permet d’ancrage sur le côté droit de la zone cliente.  
  
- CBRS_ALIGN_ANY permet d’ancrage sur n’importe quel côté de la zone cliente.  
  
### <a name="remarks"></a>Notes  
 Par défaut, les barres de contrôle seront ancrés à un côté de la fenêtre frame dans l’ordre suivant : haut, bas, gauche, droite.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).  
  
##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState  
 Appelez cette fonction membre pour changer une fenêtre frame modale en fenêtre frame non modale.  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>Notes  
 `EndModalState` permet à toutes les fenêtres désactivées par [BeginModalState](#beginmodalstate).  
  
##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar  
 Appelez cette fonction pour provoquer une barre de contrôle pour n’être ancré à la fenêtre frame.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Paramètres  
 *pBar*  
 Pointe vers la barre de contrôle à laisser flotter.  
  
 *point*  
 L’emplacement, en coordonnées d’écran, où le coin supérieur gauche de la barre de contrôle sera placé.  
  
 *dwStyle*  
 Spécifie s’il faut aligner horizontalement ou verticalement la barre de contrôle dans sa fenêtre frame. Il peut prendre l’une des opérations suivantes :  
  
- CBRS_ALIGN_TOP oriente verticalement la barre de contrôle.  
  
- CBRS_ALIGN_BOTTOM oriente verticalement la barre de contrôle.  
  
- CBRS_ALIGN_LEFT oriente horizontalement la barre de contrôle.  
  
- CBRS_ALIGN_RIGHT oriente horizontalement la barre de contrôle.  
  
 Si les styles sont passés en spécifiant l’orientation horizontale et verticale, la barre d’outils sera orienté horizontalement.  
  
### <a name="remarks"></a>Notes  
 En règle générale, cela au démarrage de l’application lorsque le programme de restauration des paramètres de l’exécution précédente.  
  
 Cette fonction est appelée par l’infrastructure quand l’utilisateur entraîne une opération de déplacement en relâchant le bouton gauche de la souris tout en faisant glisser la barre de contrôle sur un emplacement qui n’est pas disponible pour l’ancrage.  
  
##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument  
 Appelez cette fonction membre pour obtenir un pointeur vers l’actuel `CDocument` associé à la vue active actuelle.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’actuel [CDocument](../../mfc/reference/cdocument-class.md). S’il n’existe aucun document actif, renvoie la valeur NULL.  
  
##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame  
 Appelez cette fonction membre pour obtenir un pointeur vers l’actif fenêtre interface multidocument (MDI) enfant d’une fenêtre frame MDI.  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la fenêtre enfant MDI active. Si l’application est une application SDI, ou la fenêtre frame MDI ne possède aucun document actif, le caractère implicite **cela** pointeur s’affichera.  
  
### <a name="remarks"></a>Notes  
 S’il n’existe aucun enfant MDI actif ou que l’application est une interface monodocument (SDI), le caractère implicite **cela** pointeur est retourné.  
  
##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView  
 Appelez cette fonction membre pour obtenir un pointeur vers la vue active (le cas échéant) attaché à une fenêtre frame ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’actuel [CView](../../mfc/reference/cview-class.md). S’il n’existe aucun affichage actuel, retourne la valeur NULL.  
  
### <a name="remarks"></a>Notes  
 Cette fonction retourne la valeur NULL lorsqu’elle est appelée pour une fenêtre frame principale MDI ( `CMDIFrameWnd`). Dans une application MDI, la fenêtre frame principale MDI n’a pas une vue associée. Au lieu de cela, chaque fenêtre enfants individuels ( `CMDIChildWnd`) a une ou plusieurs vues associées. La vue active dans une application MDI peut être obtenue en recherche tout d’abord la fenêtre MDI enfant active, puis en recherchant la vue active pour cette fenêtre enfant. Vous trouverez la fenêtre MDI enfant active en appelant la fonction `MDIGetActive` ou `GetActiveFrame` comme illustré dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar  
 Appelez `GetControlBar` pour accéder à la barre de contrôle qui est associée avec le code.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 Numéro d’identification d’une barre de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la barre de contrôle qui est associé avec le code.  
  
### <a name="remarks"></a>Notes  
 Le *nID* paramètre fait référence à l’identificateur unique passé à la `Create` méthode de la barre de contrôle. Pour plus d’informations sur les barres de contrôle, reportez-vous à la rubrique intitulée [barres de contrôles](../../mfc/control-bars.md).  
  
 `GetControlBar` Retourne la barre de contrôle même s’il est flottant et par conséquent, n’est pas actuellement une fenêtre enfant de l’image.  
  
##  <a name="getdockstate"></a>  CFrameWnd::GetDockState  
 Appelez cette fonction membre pour stocker les informations d’état à propos des barres de contrôle de la fenêtre frame dans une `CDockState` objet.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *state*  
 Contient l’état actuel de la fenêtre frame barres de contrôles au moment du retour.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez ensuite écrire le contenu de `CDockState` à l’utilisation de stockage `CDockState::SaveState` ou `Serialize`. Si vous souhaitez ultérieurement restaurer les barres de contrôles à un état antérieur, charger l’état avec `CDockState::LoadState` ou `Serialize`, puis appelez `SetDockState` pour appliquer l’état précédent à barres de contrôle de la fenêtre frame.  
  
##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState  
 Récupère l’état d’affichage du menu de l’application MFC en cours.  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour peut avoir les valeurs suivantes :  
  
-   AFX_MBS_VISIBLE (0 x 01) - le menu est visible.  
  
-   AFX_MBS_HIDDEN (0 x 02) - le menu est masqué.  
  
### <a name="remarks"></a>Notes  
 Si une erreur d’exécution se produit, cette méthode déclare en mode débogage et déclenche une exception dérivée de la [CException](../../mfc/reference/cexception-class.md) classe.  
  
##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility  
 Indique si l’état par défaut du menu de l’application MFC actuelle est visible ou masquée.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne une des valeurs suivantes :  
  
-   AFX_MBV_KEEPVISIBLE (0 x 01) - le menu apparaît à tous les moments et par défaut n’a pas le focus.  
  
-   AFX_MBV_DISPLAYONFOCUS (0 x 02) - le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche ALT pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur la touche ALT ou sur ÉCHAP pour le masquer.  
  
-   AFX_MBV_ DISPLAYONFOCUS (0 x 02) &#124; AFX_MBV_DISPLAYONF10 (0 x 04) (combinaison (OR)) - le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche F10 pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur la touche F10 pour activer/désactiver le focus ou désactiver le menu. Le menu s’affiche jusqu'à ce que vous appuyez sur la touche ALT ou sur ÉCHAP pour le masquer.  
  
### <a name="remarks"></a>Notes  
 Si une erreur d’exécution se produit, cette méthode déclare en mode débogage et déclenche une exception dérivée de la [CException](../../mfc/reference/cexception-class.md) classe.  
  
##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar  
 Appelez cette fonction membre pour obtenir un pointeur vers la barre d’état.  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la fenêtre de la barre d’état.  
  
##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString  
 Remplacez cette fonction pour fournir des chaînes personnalisées pour l’ID de commande.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 ID de ressource du message souhaité.  
  
 *rMessage*  
 `CString` objet dans lequel placer le message.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut charge simplement la chaîne spécifiée par *nID* à partir du fichier de ressources. Cette fonction est appelée par l’infrastructure lors de la chaîne de message dans la barre d’état a besoin de la mise à jour.  
  
##  <a name="gettitle"></a>  CFrameWnd::GetTitle  
 Récupère le titre de l’objet window.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant le titre de l’objet de fenêtre actuelle.  
  
##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame  
 Appelez `IntitialUpdateFrame` après avoir créé un nouveau frame avec `Create`.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDoc*  
 Pointe vers le document auquel la fenêtre frame est associée. Peut être NULL.  
  
 *bMakeVisible*  
 Si la valeur est TRUE, indique que le frame doit devenir visible et actif. Si la valeur est FALSE, aucun descendants ne sont rendues visibles.  
  
### <a name="remarks"></a>Notes  
 Cela provoque toutes les vues dans cette fenêtre frame pour recevoir leur `OnInitialUpdate` appels.  
  
 En outre, s’il n'existait pas précédemment une vue active, la vue de la fenêtre frame principale devient active. La vue principale est une vue avec un ID de AFX_IDW_PANE_FIRST enfant. Enfin, la fenêtre frame est rendue visible si *bMakeVisible* est différent de zéro. Si *bMakeVisible* est 0, le focus actuel et l’état visible de la fenêtre frame restera inchangés. Il n’est pas nécessaire d’appeler cette fonction lorsque vous utilisez l’implémentation de l’infrastructure du nouveau fichier et ouvrir le fichier.  
  
##  <a name="inmodalstate"></a>  CFrameWnd::InModalState  
 Appelez cette fonction membre pour vérifier si une fenêtre frame est modale ou non modale.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si Oui ; sinon 0.  
  
##  <a name="istracking"></a>  CFrameWnd::IsTracking  
 Appelez cette fonction membre pour déterminer si la barre de fractionnement dans la fenêtre est en cours de déplacement.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une opération de fractionnement est en cours ; sinon 0.  
  
##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable  
 L’appel pour charger la table d’accélérateurs spécifié.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszResourceName*  
 Identifie le nom de la ressource de l’accélérateur. Utilisez MAKEINTRESOURCE si la ressource est identifiée par un ID d’entier.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la table d’accélérateurs a été chargée avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Une seule table peut être chargée à la fois.  
  
 Tables d’accélérateurs chargés à partir de ressources sont libérées automatiquement lors de l’application se termine.  
  
 Si vous appelez `LoadFrame` pour créer la fenêtre frame, le framework charge une table d’accélérateurs, ainsi que les ressources de menu et icône, et un appel ultérieur à cette fonction membre est alors inutile.  
  
##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState  
 Appelez cette fonction pour restaurer les paramètres de chaque barre de contrôle appartenant à la fenêtre frame.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszProfileName*  
 Nom d’une section dans le fichier d’initialisation (INI) ou une clé dans le Registre Windows où sont stockées les informations d’état.  
  
### <a name="remarks"></a>Notes  
 Les informations restaurées incluent la visibilité, l’orientation verticale/horizontale, état d’ancrage et position de la barre de contrôle.  
  
 Les paramètres que vous souhaitez restaurer doivent être écrites dans le Registre avant d’appeler `LoadBarState`. Écrire les informations dans le Registre en appelant [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Écrire les informations du fichier INI en appelant [SaveBarState](#savebarstate).  
  
##  <a name="loadframe"></a>  CFrameWnd::LoadFrame  
 L’appel pour créer dynamiquement une fenêtre frame à partir des informations sur les ressources.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDResource*  
 ID de ressources partagées associées à la fenêtre frame.  
  
 *dwDefaultStyle*  
 Le frame [style](../../mfc/reference/styles-used-by-mfc.md#window-styles). Inclure le style FWS_ADDTOTITLE si vous souhaitez que la barre de titre pour afficher automatiquement le nom du document représenté dans la fenêtre.  
  
 *pParentWnd*  
 Pointeur vers le parent du cadre.  
  
 *pContext*  
 Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure. Ce paramètre peut être NULL.  
  
### <a name="remarks"></a>Notes  
 Construire un `CFrameWnd` objet en deux étapes. Tout d’abord, appeler le constructeur, ce qui construit la `CFrameWnd` de l’objet, puis appelez `LoadFrame`, qui se charge de la fenêtre de frame de Windows et les ressources associées et attache la fenêtre frame pour le `CFrameWnd` objet. Le *nIDResource* paramètre spécifie le menu, la table d’accélérateurs, l’icône et la ressource de chaîne du titre de la fenêtre frame.  
  
 Utilisez le `Create` fonction membre plutôt que `LoadFrame` lorsque vous souhaitez spécifier tous les paramètres de création de la fenêtre frame.  
  
 Le framework appelle `LoadFrame` lorsqu’il crée une fenêtre frame à l’aide d’un objet de modèle de document.  
  
 L’infrastructure utilise le *pContext* argument pour spécifier les objets d’être connecté à la fenêtre frame, y compris les contenus des objets de vue. Vous pouvez définir le *pContext* argument null lorsque vous appelez `LoadFrame`.  
  
##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable  
 Lorsque ce membre de données est activé (qui est la valeur par défaut), les éléments de menu qui n’ont pas de gestionnaires ON_UPDATE_COMMAND_UI ou ON_COMMAND seront automatiquement désactivés lorsque l’utilisateur retire un menu déroulant.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Notes  
 Les éléments de menu qui ont un gestionnaire ON_COMMAND mais aucun gestionnaire ON_UPDATE_COMMAND_UI seront automatiquement activés.  
  
 Lorsque ce membre de données est défini, les éléments de menu sont automatiquement activés dans la même façon que les boutons de barre d’outils sont activés.  
  
> [!NOTE]
> `m_bAutoMenuEnable` n’a aucun effet sur les éléments de menu de niveau supérieur.  
  
 Ce membre de données simplifie l’implémentation de commandes facultatives en fonction de la sélection actuelle et réduit le besoin d’écrire des gestionnaires ON_UPDATE_COMMAND_UI pour activer ou désactiver des éléments de menu.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace  
 Appelez cette fonction membre pour négocier l’espace de bordure dans une fenêtre frame pendant l’activation de OLE sur place.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBorderCmd*  
 Contient l’une des valeurs suivantes à partir de la `enum BorderCmd`:  
  
- `borderGet` = 1  
  
- `borderRequest` = 2  
  
- `borderSet` = 3  
  
 *lpRectBorder*  
 Pointeur vers un [RECT](../../mfc/reference/rect-structure1.md) structure ou un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui spécifie les coordonnées de la bordure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est la `CFrameWnd` implémentation de négociation d’espace de bordure OLE.  
  
##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck  
 Appelée chaque fois qu’une action est effectuée dans la barre de contrôle spécifié.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 L’ID du contrôle de la barre est affichée.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la barre de contrôle existait ; sinon 0.  
  
##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp  
 Gère MAJ + F1 Aide pour les éléments de la place.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Notes  
 Pour activer l’aide contextuelle, vous devez ajouter une  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 instruction à votre `CFrameWnd` classe table des messages et également ajouter une entrée de table d’accélérateurs, généralement MAJ + F1, pour activer cette fonction membre.  
  
 Si votre application est un conteneur OLE, `OnContextHelp` place tous les éléments de place contenus dans l’objet de fenêtre frame en mode d’aide. Le curseur se transforme en flèche et un point d’interrogation et que l’utilisateur peut déplacer le pointeur de la souris, puis appuyez sur le bouton gauche de la souris pour sélectionner une boîte de dialogue, une fenêtre, un menu ou un bouton de commande. Cette fonction membre appelle la fonction Windows `WinHelp` avec le contexte d’aide de l’objet sous le curseur.  
  
##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient  
 Appelé par l’infrastructure pendant l’exécution de `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Paramètres  
 *Procedure Calls, LPC*  
 Un pointeur vers un Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) structure.  
  
 *pContext*  
 Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Ne jamais appeler cette fonction.  
  
 L’implémentation par défaut de cette fonction crée un `CView` objet à partir des informations fournies dans *pContext*, si possible.  
  
 Remplacez cette fonction pour remplacer les valeurs passées dans le `CCreateContext` de l’objet ou pour modifier les façon dont les contrôles dans la zone principale du client de la fenêtre frame sont créés. Le `CCreateContext` vous pouvez remplacer les membres sont décrites dans le [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) classe.  
  
> [!NOTE]
>  Ne remplacez pas les valeurs passées dans le `CREATESTRUCT` structure. Ils sont uniquement à titre d’information. Si vous souhaitez remplacer le rectangle de la fenêtre initiale, par exemple, remplacer le `CWnd` fonction membre [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar  
 Cette fonction est appelée lorsque le système est sur le point de masquer la barre de menus dans l’application MFC actuelle.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements permet à votre application effectuer des actions personnalisées lorsque le système est sur le point de masquer le menu. Vous ne pouvez pas empêcher le menu de masqué, mais vous pouvez, par exemple, appeler des autres méthodes pour récupérer le style de menu ou d’un état.  
  
##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode  
 Appelez cette fonction membre pour définir la fenêtre frame principale de l’application dans et en dehors du mode Aperçu avant impression.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Paramètres  
 *bPreview*  
 Spécifie s’il faut placer l’application en mode d’aperçu avant impression. La valeur TRUE à placer dans l’aperçu avant impression, FALSE pour annuler le mode Aperçu.  
  
 *pState*  
 Un pointeur vers un `CPrintPreviewState` structure.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut désactive toutes les barres d’outils standards et masque le menu principal et la fenêtre principale du client. Cela transforme les fenêtres frames MDI en fenêtres de frame SDI temporaires.  
  
 Remplacez cette fonction membre pour personnaliser le masquage et l’affichage des barres de contrôles et d’autres parties de la fenêtre frame pendant l’aperçu avant impression. Appeler l’implémentation de classe de base à partir de dans la version substituée.  
  
##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar  
 Cette fonction est appelée lorsque le système est sur le point d’afficher la barre de menus dans l’application MFC en cours.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements permet à votre application effectuer des actions personnalisées lorsque le menu est sur le point d’être affiché. Vous ne pouvez pas empêcher le le menu Affichage, mais vous pouvez, par exemple, appeler des autres méthodes pour récupérer le style de menu ou d’un état.  
  
##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu  
 Appelé par le framework lorsque le menu associé est mis à jour.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers un [CCmdUI](../../mfc/reference/ccmdui-class.md) objet qui représente le menu qui a généré la commande de mise à jour. Le Gestionnaire de mise à jour appelle le [activer](../../mfc/reference/ccmdui-class.md#enable) fonction membre de la `CCmdUI` par le biais de l’objet *pCmdUI* pour mettre à jour de l’interface utilisateur.  
  
##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout  
 Appelé par l’infrastructure lorsque les barres de contrôle standard sont activées ou désactivées ou lorsque la fenêtre frame est redimensionnée.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bNotify*  
 Détermine si l’élément actif sur place de la fenêtre frame reçoit la notification de la modification de la disposition. Si la valeur est TRUE, l’élément est notifié ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction membre appelle le `CWnd` fonction membre `RepositionBars` à repositionner toutes les barres de contrôle dans le frame, ainsi que dans la fenêtre cliente principale (généralement un `CView` ou MDICLIENT).  
  
 Remplacez cette fonction membre pour contrôler l’apparence et le comportement des barres de contrôle une fois que la disposition de la fenêtre frame a été modifiée. Appelez-le, par exemple, lorsque vous activez ou désactiver les barres de contrôle ou que vous ajoutez une autre barre de contrôle.  
  
##  <a name="rectdefault"></a>  CFrameWnd::rectDefault  
 Passer ce statique `CRect` en tant que paramètre lors de la création d’une fenêtre pour autoriser Windows à choisir la taille initiale et la position de la fenêtre.  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState  
 Appelez cette fonction pour stocker des informations sur chaque barre de contrôle appartenant à la fenêtre frame.  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszProfileName*  
 Nom d’une section dans le fichier d’initialisation ou d’une clé dans le Registre Windows où sont stockées les informations d’état.  
  
### <a name="remarks"></a>Notes  
 Ces informations peuvent être lues depuis le fichier d’initialisation à l’aide [LoadBarState](#loadbarstate). Informations stockées incluent la visibilité, l’orientation horizontale/verticale, station d’accueil d’état et la position de barre de contrôle.  
  
##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView  
 Désigne la vue spécifiée à la vue active pour l’aperçu riche.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Paramètres  
 *pViewNew*  
 Pointeur vers une vue à activer.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView  
 Appelez cette fonction membre pour définir la vue active.  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pViewNew*  
 Spécifie un pointeur vers un [CView](../../mfc/reference/cview-class.md) objet, ou NULL pour aucune vue active.  
  
 *bNotify*  
 Spécifie si la vue doit être averti de l’activation. Si la valeur est TRUE, `OnActivateView` est appelée pour la nouvelle vue ; si FALSE, il n’est pas.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction automatiquement lorsque l’utilisateur modifie le focus à une vue dans la fenêtre frame. Vous pouvez appeler explicitement `SetActiveView` pour déplacer le focus vers la vue spécifiée.  
  
##  <a name="setdockstate"></a>  CFrameWnd::SetDockState  
 Appelez cette fonction membre pour appliquer les informations d’état stockées dans un `CDockState` objet aux barres de contrôles de la fenêtre frame.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Paramètres  
 *state*  
 Appliquer l’état stocké à des barres de contrôle de la fenêtre frame.  
  
### <a name="remarks"></a>Notes  
 Pour restaurer un état antérieur des barres de contrôles, vous pouvez charger l’état stocké avec `CDockState::LoadState` ou `Serialize`, puis utiliser `SetDockState` pour l’appliquer aux barres de contrôles de la fenêtre frame. L’état précédent est stocké dans le `CDockState` avec l’objet `GetDockState`  
  
##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState  
 Définit l’état d’affichage du menu dans l’application MFC actuelle masqué ou affiché.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *nState*|Spécifie s’il faut afficher ou masquer le menu. Le *nState* paramètre peut avoir les valeurs suivantes :<br /><br /> -AFX_MBS_VISIBLE (0 x 01) - affiche le menu si elle est masquée, mais n’a aucun effet s’il est visible.<br />-AFX_MBS_HIDDEN (0 x 02) - masque le contrôle menu si elle est visible, mais n’a aucun effet s’il est masqué.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a correctement modifié l’état de menu ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Si une erreur d’exécution se produit, cette méthode déclare en mode débogage et déclenche une exception dérivée de la [CException](../../mfc/reference/cexception-class.md) classe.  
  
##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility  
 Définit le comportement par défaut du menu dans l’application MFC actuelle pour être masquées ou visibles.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *nStyle*|Spécifie si le menu par défaut est masquée, ou n’est visible et a le focus. Le *nStyle* paramètre peut avoir les valeurs suivantes :<br /><br /> -AFX_MBV_KEEPVISIBLE (0 X 01)-<br />     Le menu est affiché en permanence et par défaut n’a pas le focus.<br />-AFX_MBV_DISPLAYONFOCUS (0 X 02)-<br />     Le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche ALT pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur ALT ou sur ÉCHAP pour masquer le menu.<br />-AFX_MBV_ DISPLAYONFOCUS (0 x 02) &#124; AFX_MBV_DISPLAYONF10 (0 x 04)<br />     (combinaison (OR)) - le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche F10 pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur la touche F10 pour activer/désactiver le focus ou désactiver le menu. Le menu s’affiche jusqu'à ce que vous appuyez sur la touche ALT ou sur ÉCHAP pour le masquer.|  
  
### <a name="remarks"></a>Notes  
 Si la valeur de la *nStyle* paramètre n’est pas valide, cette méthode déclare en mode débogage et déclenche [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en mode Release. En cas d’autres erreurs d’exécution, cette méthode déclare en mode débogage et déclenche une exception dérivée de la [CException](../../mfc/reference/cexception-class.md) classe.  
  
 Cette méthode affecte l’état des menus dans les applications écrites pour [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] et versions ultérieures.  
  
##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText  
 Appelez cette fonction pour placer une chaîne dans le volet de barre d’état qui a un ID égal à 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszText*  
 Pointe vers la chaîne à placer sur la barre d’état.  
  
 *nID*  
 ID de ressource de la chaîne à placer sur la barre d’état de la chaîne.  
  
### <a name="remarks"></a>Notes  
 C’est généralement le plus à gauche et la plus long, le volet de la barre d’état.  
  
##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition  
 Définit la position actuelle pour la barre de progression de Windows 7 affichée sur la barre des tâches.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Paramètres  
 *nProgressPos*  
 Spécifie la position à définir. Il doit être dans la plage définie par `SetProgressBarRange`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange  
 Définit la plage pour la barre de progression de Windows 7 affichée sur la barre des tâches.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRangeMin*  
 Valeur minimale.  
  
 *nRangeMax*  
 Valeur maximale.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState  
 Définit le type et l’état de l’indicateur de progression affichée sur un bouton de barre des tâches.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *tbpFlags*  
 Indicateurs qui contrôlent l’état actuel du bouton de progression. Spécifiez uniquement une de ces indicateurs, car tous les États s’excluent mutuellement : TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon  
 Surchargé. S’applique à une superposition à un bouton de barre des tâches pour indiquer l’état de l’application ou pour informer l’utilisateur.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDResource*  
 Spécifie l’ID de ressource d’une icône à utiliser comme la superposition. Consultez la description pour *hIcon* pour plus d’informations.  
  
 *lpcszDescr*  
 Un pointeur vers une chaîne qui fournit une version texte de remplacement des informations fournies par la superposition, à des fins d’accessibilité.  
  
 *hIcon*  
 Le handle d’une icône à utiliser comme la superposition. Il doit s’agir d’une petite icône, mesurer 16 x 16 pixels à 96 points par pouce (PPP) Si une icône de superposition est déjà appliquée au bouton de barre des tâches, cette superposition existante est remplacée. Cette valeur peut être NULL. Comment une valeur NULL est gérée dépend de si le bouton de barre des tâches représente une fenêtre unique ou un groupe de windows. Il incombe à l’application appelante pour libérer *hIcon* quand il n’est plus nécessaire.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE en cas de réussite ; FALSE si la version de système d’exploitation est inférieure à Windows 7 ou si une erreur se produit la définition de l’icône.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settitle"></a>  CFrameWnd::SetTitle  
 Définit le titre de l’objet window.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszTitle*  
 Pointeur vers une chaîne de caractères contenant le titre de l’objet window.  
  
##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar  
 Appelez cette fonction membre pour afficher ou masquer la barre de contrôle.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Paramètres  
 *pBar*  
 Pointeur vers la barre de contrôle doit être affiché ou masqué.  
  
 *bShow*  
 Si la valeur est TRUE, spécifie que la barre de contrôle doit être indiqué. Si la valeur est FALSE, spécifie que la barre de contrôle doit être masqué.  
  
 *bDelay*  
 Si la valeur est TRUE, délai d’affichage de la barre de contrôle. Si la valeur est FALSE, afficher le contrôle de barre immédiatement.  
  
##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows  
 Appelez cette fonction membre pour afficher toutes les fenêtres qui sont des descendants de le `CFrameWnd` objet.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 *bShow*  
 Spécifie si les fenêtres enfants doivent être affichés ou masqués.  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd, classe](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd, classe](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd (classe)](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd (classe)](../../mfc/reference/cmdichildwnd-class.md)   
 [CView (classe)](../../mfc/reference/cview-class.md)   
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass, structure](../../mfc/reference/cruntimeclass-structure.md)
