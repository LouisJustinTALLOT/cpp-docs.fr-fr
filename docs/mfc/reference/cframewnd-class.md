---
title: CFrameWnd (classe) | Documents Microsoft
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
ms.openlocfilehash: 35a3fb35115e1fd86a2ccf168e048a697a17dc01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378503"
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
|[CFrameWnd::CreateView](#createview)|Crée une vue dans un frame qui n’est pas dérivée de `CView`.|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Ancre une barre de contrôle.|  
|[CFrameWnd::EnableDocking](#enabledocking)|Permet à une barre de contrôle être ancrée.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Termine l’état modal de la fenêtre frame. Permet à toutes les fenêtres désactivées par `BeginModalState`.|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Flotte une barre de contrôle.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Retourne l’actif **CDocument** objet.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Retourne l’actif `CFrameWnd` objet.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Retourne l’actif `CView` objet.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Récupère la barre de contrôle.|  
|[CFrameWnd::GetDockState](#getdockstate)|Récupère l’état d’ancrage d’une fenêtre frame.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Récupère l’état d’affichage du menu de l’application MFC en cours.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indique si le comportement par défaut du menu de l’application MFC en cours est visible ou masqué.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Retourne un pointeur vers l’état de la barre appartenant à la fenêtre frame.|  
|[CFrameWnd::GetMessageString](#getmessagestring)|Récupère le message correspondant à un ID de commande.|  
|[CFrameWnd::GetTitle](#gettitle)|Récupère le titre de la barre de contrôle associé.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Provoque la `OnInitialUpdate` fonction membre appartenant à toutes les vues dans la fenêtre frame à appeler.|  
|[CFrameWnd::InModalState](#inmodalstate)|Retourne une valeur qui indique si une fenêtre frame est dans un état modal.|  
|[CFrameWnd::IsTracking](#istracking)|Détermine si la barre de fractionnement est actuellement déplacée.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Appel pour charger une table d’accélérateurs.|  
|[CFrameWnd::LoadBarState](#loadbarstate)|L’appel à restaurer les paramètres de barre de contrôle.|  
|[CFrameWnd::LoadFrame](#loadframe)|L’appel à créer dynamiquement une fenêtre frame d’informations sur la ressource.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Négocie l’espace de bordure de la fenêtre frame.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Appelé chaque fois qu’une action est effectuée dans la barre de contrôle spécifié.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Gère les MAJ + F1 Aide pour les éléments en place.|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Définit la fenêtre frame principale de l’application dans et hors mode Aperçu avant impression.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Appelé par le framework lorsque le menu associé est mis à jour.|  
|[CFrameWnd::RecalcLayout](#recalclayout)|Repositionne les barres de contrôles de la `CFrameWnd` objet.|  
|[CFrameWnd::SaveBarState](#savebarstate)|L’appel à enregistrer les paramètres de barre de contrôle.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Désigne la vue spécifiée à la vue active pour l’aperçu riche.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Définit l’actif `CView` objet.|  
|[CFrameWnd::SetDockState](#setdockstate)|Appel pour ancrer la fenêtre frame dans la fenêtre principale.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Définit l’état d’affichage du menu de l’application MFC actuelle masqué ou affiché.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Définit le comportement par défaut du menu de l’application MFC en cours pour être masquées ou visibles.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Définit le texte d’une barre d’état standard.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Définit la position actuelle pour la barre de progression Windows 7 affichée sur la barre des tâches.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Définit la plage de barre de progression Windows 7 affichée sur la barre des tâches.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Définit le type et l’état de l’indicateur de progression affichée sur un bouton de barre des tâches.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Surchargé. S’applique à un segment de recouvrement à un bouton de barre des tâches pour indiquer l’état de l’application ou d’une notification à l’utilisateur.|  
|[CFrameWnd::SetTitle](#settitle)|Définit le titre de la barre de contrôle associé.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|L’appel à afficher la barre de contrôle.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Affiche toutes les fenêtres qui sont des descendants de le `CFrameWnd` objet.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crée une fenêtre du client pour le frame.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Appelé avant que le menu de l’application MFC en cours est masqué.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Appelé avant que le menu de l’application MFC en cours s’affiche.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Contrôles automatique activent et désactiver les fonctionnalités des éléments de menu.|  
|[CFrameWnd::rectDefault](#rectdefault)|Passer ce statique `CRect` en tant que paramètre lorsque vous créez un `CFrameWnd` objet pour autoriser Windows à choisir la taille initiale et la position de la fenêtre.|  
  
## <a name="remarks"></a>Notes  
 Pour créer une fenêtre frame utiles pour votre application, dérivez une classe de `CFrameWnd`. Ajoutez des variables membres à la classe dérivée pour stocker les données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.  
  
 Il existe trois manières de construire une fenêtre frame :  
  
-   Construire directement à l’aide de [créer](#create).  
  
-   Construire directement à l’aide de [LoadFrame](#loadframe).  
  
-   Indirectement le générer à l’aide d’un modèle de document.  
  
 Avant d’appeler soit **créer** ou `LoadFrame`, vous devez construire l’objet de fenêtre frame sur le tas à l’aide de C++ **nouveau** opérateur. Avant d’appeler **créer**, vous pouvez également enregistrer une classe de fenêtre avec le [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) fonction globale pour définir les styles d’icône et de la classe pour le frame.  
  
 Utilisez le **créer** fonction membre pour passer des paramètres de création du frame immédiats comme arguments.  
  
 `LoadFrame` nécessite moins d’arguments que **créer**et récupère à la place de la plupart de ses valeurs par défaut à partir des ressources, y compris la légende du frame, icône, table d’accélérateurs et menu. Pour être accessible aux `LoadFrame`, toutes ces ressources doivent avoir le même ID de ressource (par exemple, **IDR_MAINFRAME**).  
  
 Lorsqu’un `CFrameWnd` objet contient des vues et des documents, elles sont créées indirectement par le framework au lieu de directement par le programmeur. Le `CDocTemplate` objet orchestre la création de l’image, la création des vues contenant et la connexion des vues de document approprié. Les paramètres de la `CDocTemplate` constructeur spécifie la `CRuntimeClass` des trois classes impliquées (document, le frame et vue). A `CRuntimeClass` objet est utilisé par l’infrastructure pour créer dynamiquement les nouvelles images lorsque spécifié par l’utilisateur (par exemple, en utilisant la commande fichier nouveau ou la commande nouvelle fenêtre de plusieurs documents MDI (interface)).  
  
 Une classe de fenêtre frame dérivée de `CFrameWnd` doit être déclaré avec `DECLARE_DYNCREATE` dans l’ordre des produits ci-dessus `RUNTIME_CLASS` mécanisme fonctionne correctement.  
  
 A `CFrameWnd` contient les implémentations par défaut pour effectuer les fonctions suivantes d’une fenêtre principale dans une application pour Windows :  
  
-   A `CFrameWnd` fenêtre frame effectue le suivi d’une vue actuellement active qui est indépendante de la fenêtre active de Windows ou le focus d’entrée actuel. Lorsque le frame est réactivé, la vue active est avertie en appelant `CView::OnActivateView`.  
  
-   Commande des messages et nombreux messages de notification de frame courantes, y compris celles gérées par le `OnSetFocus`, `OnHScroll`, et `OnVScroll` fonctions de `CWnd`, sont déléguées à un `CFrameWnd` fenêtre frame à la vue actuellement active.  
  
-   La vue actuellement active (ou la fenêtre de frame MDI enfant active dans le cas d’un frame MDI) peut déterminer la légende de la fenêtre frame. Cette fonctionnalité peut être désactivée en désactivant le **FWS_ADDTOTITLE** bit de style de la fenêtre frame.  
  
-   A `CFrameWnd` fenêtre frame gère le positionnement des barres de contrôles, des vues et des autres fenêtres enfants au sein de la zone cliente de la fenêtre frame. Une fenêtre frame effectue également la mise à jour de la durée d’inactivité de la barre d’outils et d’autres boutons de barre de contrôle. A `CFrameWnd` fenêtre frame possède également des implémentations par défaut des commandes pour activer et désactiver la barre d’outils et barre d’état.  
  
-   A `CFrameWnd` fenêtre frame gère la barre de menus principale. Lorsqu’un menu contextuel est affiché, la fenêtre frame utilise le **UPDATE_COMMAND_UI** mécanisme permettant de déterminer les éléments de menu doivent être activés, désactivés ou activés. Lorsque l’utilisateur sélectionne un élément de menu, la fenêtre frame met à jour la barre d’état avec la chaîne de message pour cette commande.  
  
-   A `CFrameWnd` fenêtre frame a une table d’accélérateurs facultative qui convertit automatiquement les accélérateurs clavier.  
  
-   A `CFrameWnd` fenêtre frame comporte un ID d’aide facultatif défini avec `LoadFrame` qui est utilisé pour l’aide contextuelle. Une fenêtre frame est le principal orchestrator des États semi-modaux tels que l’aide contextuelle (MAJ + F1) et les modes d’aperçu avant impression.  
  
-   A `CFrameWnd` fenêtre frame s’ouvre un fichier à partir du Gestionnaire de fichiers glissés -déposés dans la fenêtre frame. Si une extension de fichier est enregistrée et associée à l’application, la fenêtre frame répond à la demande d’ouverture dynamique des données (DDE) exchange qui se produit lorsque l’utilisateur ouvre un fichier de données dans le Gestionnaire de fichiers ou le **ShellExecute** Fonction de Windows est appelée.  
  
-   Si la fenêtre frame est la fenêtre d’application principale (autrement dit, `CWinThread::m_pMainWnd`), lorsque l’utilisateur ferme l’application, la fenêtre frame invite l’utilisateur à enregistrer les documents modifiés (pour `OnClose` et `OnQueryEndSession`).  
  
-   Si la fenêtre frame est la fenêtre principale de l’application, la fenêtre frame est le contexte d’exécution WinHelp. Fermeture de la fenêtre frame s’arrêtent WINHELP. EXE s’il a été lancé pour l’aide de cette application.  
  
 N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame. Utilisez plutôt `CWnd::DestroyWindow`. Le `CFrameWnd` implémentation de `PostNcDestroy` va supprimer l’objet C++ lorsque la fenêtre est détruite. Lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut `OnClose` gestionnaire appelle `DestroyWindow`.  
  
 Pour plus d’informations sur `CFrameWnd`, consultez [fenêtres Frame](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame  
 Appelez cette fonction membre pour activer et restaure la fenêtre frame, afin qu’il soit visible et accessible à l’utilisateur.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 `nCmdShow`  
 Spécifie le paramètre à passer à [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Par défaut, le frame est affiché et restauré correctement.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est généralement appelée après un événement de l’interface utilisateur non tels que les autres événements qui peuvent afficher la fenêtre frame ou son contenu à l’utilisateur, OLE ou DDE.  
  
 L’implémentation par défaut active le frame et affiche en haut de l’ordre de plan et, si nécessaire, exécute la procédure de fenêtre frame principale de l’application.  
  
 Remplacez cette fonction membre pour modifier la façon dont une image est activée. Par exemple, vous pouvez forcer des fenêtres MDI enfants à être agrandi. Ajouter la fonctionnalité appropriée, puis appeler la version classe de base avec explicite `nCmdShow`.  
  
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
 Appelez **créer** pour créer la fenêtre visible.  
  
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
 `lpszClassName`  
 Pointe vers une chaîne de caractères terminée par null que les noms de la classe Windows. Le nom de classe peut être n’importe quel nom inscrit avec le `AfxRegisterWndClass` fonction globale ou **RegisterClass** fonction Windows. Si **NULL**, utilise la valeur par défaut prédéfinie `CFrameWnd` attributs.  
  
 `lpszWindowName`  
 Pointe vers une chaîne de caractères terminée par null qui représente le nom de la fenêtre. Utilisé en tant que texte de la barre de titre.  
  
 `dwStyle`  
 Spécifie la fenêtre [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) attributs. Inclure le **FWS_ADDTOTITLE** si vous souhaitez que la barre de titre pour afficher automatiquement le nom du document représenté dans la fenêtre de style.  
  
 `rect`  
 Spécifie la taille et la position de la fenêtre. Le `rectDefault` valeur permet à Windows pour spécifier la taille et la position de la nouvelle fenêtre.  
  
 `pParentWnd`  
 Spécifie la fenêtre parente de la fenêtre frame. Ce paramètre doit être **NULL** pour les fenêtres frames de niveau supérieur.  
  
 *lpszMenuName*  
 Identifie le nom de la ressource de menu à utiliser avec la fenêtre. Utilisez **MAKEINTRESOURCE** si le menu contient un ID d’entier au lieu d’une chaîne. Ce paramètre peut être **NULL**.  
  
 `dwExStyle`  
 Spécifie la fenêtre étendue [style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) attributs.  
  
 `pContext`  
 Spécifie un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure. Ce paramètre peut être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’initialisation a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Construire un `CFrameWnd` objet en deux étapes. Tout d’abord, appelez le constructeur, qui construit la `CFrameWnd` de l’objet, puis appelez **créer**, qui crée la fenêtre frame Windows et l’attache à le `CFrameWnd` objet. **Créer** initialise le nom de classe et le nom de la fenêtre de la fenêtre et enregistre les valeurs par défaut pour son style, le parent et le menu associé.  
  
 Utilisez `LoadFrame` plutôt que **créer** pour charger la fenêtre frame à partir d’une ressource au lieu de spécifier ses arguments.  
  
##  <a name="createview"></a>  CFrameWnd::CreateView  
 Appelez `CreateView` pour créer un affichage dans un frame.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Paramètres  
 `pContext`  
 Spécifie le type de document et la vue.  
  
 `nID`  
 Numéro d’identification d’une vue.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un `CWnd` objet en cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre pour créer des « vues » qui ne sont pas `CView`-dérivée dans un frame. Après avoir appelé `CreateView`, vous devez manuellement la valeur de l’affichage actif et la configurer pour être visible ; ces tâches ne sont pas effectuées automatiquement par `CreateView`.  
  
##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar  
 Provoque une barre de contrôle être ancré à la fenêtre frame.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBar`  
 Pointe vers la barre de contrôle pour être ancrée.  
  
 `nDockBarID`  
 Détermine quel côté de la fenêtre frame à prendre en considération d’ancrage. Il peut être 0, ou la valeur d’un ou plusieurs des opérations suivantes :  
  
- `AFX_IDW_DOCKBAR_TOP` Ancrer en haut de la fenêtre frame.  
  
- **AFX_IDW_DOCKBAR_BOTTOM** ancre en fonction de la partie inférieure de la fenêtre frame.  
  
- `AFX_IDW_DOCKBAR_LEFT` Ancrer sur le côté gauche de la fenêtre frame.  
  
- `AFX_IDW_DOCKBAR_RIGHT` Ancrer à droite de la fenêtre frame.  
  
 Si 0, la barre de contrôle peut être ancrée à n’importe quel côté activée pour l’ancrage dans la fenêtre frame de destination.  
  
 `lpRect`  
 Détermine, en coordonnées d’écran, où la barre de contrôle sera ancrée dans la zone non cliente de la fenêtre frame de destination.  
  
### <a name="remarks"></a>Notes  
 La barre de contrôle sera ancrée à un des côtés de la fenêtre frame spécifié dans les appels à la fois aux [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) et [CFrameWnd::EnableDocking](#enabledocking). Le côté choisi est déterminé par `nDockBarID`.  
  
##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking  
 Appelez cette fonction pour activer les barres de contrôle dans une fenêtre frame.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwDockStyle`  
 Spécifie les côtés de la fenêtre frame peuvent servir d’ancrage de sites pour les barres de contrôle. Il peut être un ou plusieurs des opérations suivantes :  
  
- `CBRS_ALIGN_TOP` Permet d’ancrage en haut de la zone cliente.  
  
- `CBRS_ALIGN_BOTTOM` Permet d’ancrage en bas de la zone cliente.  
  
- `CBRS_ALIGN_LEFT` Permet d’ancrage à gauche de la zone cliente.  
  
- `CBRS_ALIGN_RIGHT` Permet d’ancrage sur le côté droit de la zone cliente.  
  
- `CBRS_ALIGN_ANY` Permet d’ancrage sur n’importe quel côté de la zone cliente.  
  
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
 Appelez cette fonction pour provoquer une barre de contrôle ne pas ancrer à la fenêtre frame.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBar`  
 Pointe vers la barre de contrôle pour être affichée.  
  
 `point`  
 L’emplacement, en coordonnées d’écran, où l’angle supérieur gauche de la barre de contrôle sera placé.  
  
 `dwStyle`  
 Spécifie s’il faut aligner la barre de contrôle horizontalement ou verticalement dans sa nouvelle fenêtre frame. Il peut prendre l’une des opérations suivantes :  
  
- `CBRS_ALIGN_TOP` Oriente la barre de contrôle verticalement.  
  
- `CBRS_ALIGN_BOTTOM` Oriente la barre de contrôle verticalement.  
  
- `CBRS_ALIGN_LEFT` Oriente la barre de contrôle horizontalement.  
  
- `CBRS_ALIGN_RIGHT` Oriente la barre de contrôle horizontalement.  
  
 Si les styles sont passés en spécifiant l’orientation horizontale et verticale, la barre d’outils sera orienté horizontalement.  
  
### <a name="remarks"></a>Notes  
 En règle générale, cela au démarrage de l’application lorsque le programme de restauration des paramètres à partir de l’exécution précédente.  
  
 Cette fonction est appelée par l’infrastructure quand l’utilisateur entraîne une opération de suppression en relâchant le bouton gauche de la souris tout en faisant glisser la barre de contrôle sur un emplacement qui n’est pas disponible pour la station d’accueil.  
  
##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument  
 Appelez cette fonction membre pour obtenir un pointeur vers la version **CDocument** associé à la vue active actuelle.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la version [CDocument](../../mfc/reference/cdocument-class.md). S’il n’existe aucun document actif, retourne **NULL**.  
  
##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame  
 Appelez cette fonction membre pour obtenir un pointeur vers l’actif fenêtre interface multidocument (MDI) enfant d’une fenêtre frame MDI.  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la fenêtre enfant MDI active. Si l’application est une application SDI, ou la fenêtre frame MDI ne possède aucun document actif, l’implicite **cela** pointeur est retourné.  
  
### <a name="remarks"></a>Notes  
 S’il n’existe aucun enfant MDI actif ou l’application est une interface monodocument (SDI), implicite **cela** pointeur est retourné.  
  
##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView  
 Appelez cette fonction membre pour obtenir un pointeur vers la vue active (le cas échéant) attaché à une fenêtre frame ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la version [CView](../../mfc/reference/cview-class.md). S’il n’existe aucun affichage actuel, retourne **NULL**.  
  
### <a name="remarks"></a>Notes  
 Cette fonction retourne **NULL** lorsqu’elle est appelée pour une fenêtre frame principale MDI ( `CMDIFrameWnd`). Dans une application MDI, la fenêtre frame principale MDI n’a pas une vue associée. Au lieu de cela, chaque fenêtre enfant ( `CMDIChildWnd`) a une ou plusieurs vues associées. La vue active dans une application MDI peut être obtenue par la recherche d’abord la fenêtre enfant MDI active et puis en recherchant la vue active pour cette fenêtre enfant. La fenêtre enfant MDI active sont accessibles en appelant la fonction `MDIGetActive` ou **GetActiveFrame** comme illustré dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar  
 Appelez `GetControlBar` pour accéder à la barre de contrôle qui est associée à l’ID.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `nID`  
 Le numéro d’ID d’une barre de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la barre de contrôle qui est associé à l’ID.  
  
### <a name="remarks"></a>Notes  
 Le `nID` paramètre fait référence à l’identificateur unique est passé à la **créer** méthode de la barre de contrôle. Pour plus d’informations sur les barres de contrôles, reportez-vous à la rubrique intitulée [barres de contrôles](../../mfc/control-bars.md).  
  
 `GetControlBar` Retourne la barre de contrôle même si elle est flottant et par conséquent, n’est pas une fenêtre enfant de l’image.  
  
##  <a name="getdockstate"></a>  CFrameWnd::GetDockState  
 Appelez cette fonction membre pour stocker les informations d’état à propos des barres de contrôle de la fenêtre frame dans un `CDockState` objet.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `state`  
 Contient l’état actuel de la fenêtre frame barres de contrôles au moment du retour.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez ensuite écrire le contenu de `CDockState` à l’aide du stockage `CDockState::SaveState` ou `Serialize`. Si vous souhaitez ultérieurement restaurer les barres de contrôles à un état antérieur, charger l’état avec `CDockState::LoadState` ou `Serialize`, puis appelez `SetDockState` pour appliquer l’état précédent aux barres de contrôles de la fenêtre frame.  
  
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
 Indique si l’état par défaut du menu de l’application MFC en cours est visible ou masquée.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne l’une des valeurs suivantes :  
  
-   AFX_MBV_KEEPVISIBLE (0 x 01) - le menu s’affiche d’à tout moment et par défaut n’a pas le focus.  
  
-   AFX_MBV_DISPLAYONFOCUS (0 x 02) - le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche ALT pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur la touche ALT ou sur ÉCHAP pour le masquer.  
  
-   AFX_MBV_ DISPLAYONFOCUS (0 x 02) &#124; AFX_MBV_DISPLAYONF10 (0 x 04) (combinaison (OR)) - le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche F10 pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur F10 pour basculer le focus ou de désactiver le menu. Le menu s’affiche jusqu'à ce que vous appuyez sur la touche ALT ou sur ÉCHAP pour le masquer.  
  
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
 Remplacez cette fonction pour fournir des chaînes personnalisées pour les ID de commande.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nID`  
 ID de ressource du message souhaité.  
  
 `rMessage`  
 `CString` objet dans lequel placer le message.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut charge simplement la chaîne spécifiée par `nID` à partir du fichier de ressources. Cette fonction est appelée par l’infrastructure lors de la chaîne de message dans la barre d’état à jour.  
  
##  <a name="gettitle"></a>  CFrameWnd::GetTitle  
 Récupère le titre de l’objet de fenêtre.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant le titre en cours de l’objet de fenêtre.  
  
##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame  
 Appelez **IntitialUpdateFrame** après la création d’un nouveau frame avec **créer**.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDoc`  
 Pointe vers le document auquel la fenêtre frame est associée. Peut être **NULL**.  
  
 `bMakeVisible`  
 Si **TRUE**, indique que l’image doit être visible et actif. Si **FALSE**, aucuns descendants ne sont visibles.  
  
### <a name="remarks"></a>Notes  
 Cela entraîne de toutes les vues dans cette fenêtre frame pour recevoir leurs `OnInitialUpdate` appels.  
  
 En outre, s’il n’est pas une vue active, la vue principale de la fenêtre frame devient active. L’affichage principal est une vue avec l’ID enfant de **AFX_IDW_PANE_FIRST**. Enfin, la fenêtre frame est rendue visible si `bMakeVisible` est différente de zéro. Si `bMakeVisible` est 0, le focus actuel et l’état de visibilité de la fenêtre frame demeurent inchangés. Il n’est pas nécessaire d’appeler cette fonction lorsque vous utilisez l’implémentation de l’infrastructure du nouveau fichier et ouvrir le fichier.  
  
##  <a name="inmodalstate"></a>  CFrameWnd::InModalState  
 Appelez cette fonction membre pour vérifier si une fenêtre frame est modale ou non.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si Oui ; Sinon, 0.  
  
##  <a name="istracking"></a>  CFrameWnd::IsTracking  
 Appelez cette fonction membre pour déterminer si la barre de fractionnement dans la fenêtre est actuellement déplacée.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une opération de fractionnement est en cours ; Sinon, 0.  
  
##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable  
 Appel pour charger la table d’accélérateurs spécifié.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszResourceName`  
 Identifie le nom de la ressource de l’accélérateur. Utilisez **MAKEINTRESOURCE** si la ressource est identifiée par un ID d’entier.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la table d’accélérateurs a été chargée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Une seule table peut être chargée à la fois.  
  
 Tables d’accélérateurs chargés à partir des ressources sont libérées automatiquement lorsque l’application se termine.  
  
 Si vous appelez `LoadFrame` pour créer la fenêtre frame, le framework charge une table d’accélérateurs, ainsi que les ressources de menu et l’icône et un appel ultérieur à cette fonction membre est alors inutile.  
  
##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState  
 Appelez cette fonction pour restaurer les paramètres de chaque barre de contrôle appartenant à la fenêtre frame.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszProfileName`  
 Nom d’une section dans le fichier d’initialisation (INI) ou d’une clé dans le Registre Windows où sont stockées les informations d’état.  
  
### <a name="remarks"></a>Notes  
 Les informations restaurées incluent la visibilité, horizontal/vertical orientation, état d’ancrage et la position de la barre de contrôle.  
  
 Les paramètres que vous souhaitez restaurer doivent être écrites dans le Registre avant d’appeler `LoadBarState`. Écrire les informations dans le Registre en appelant [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Écriture des informations dans le fichier INI en appelant [SaveBarState](#savebarstate).  
  
##  <a name="loadframe"></a>  CFrameWnd::LoadFrame  
 L’appel à créer dynamiquement une fenêtre frame d’informations sur la ressource.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDResource`  
 ID de ressources partagées associées à la fenêtre frame.  
  
 *dwDefaultStyle*  
 L’image [style](../../mfc/reference/styles-used-by-mfc.md#window-styles). Inclure le **FWS_ADDTOTITLE** si vous souhaitez que la barre de titre pour afficher automatiquement le nom du document représenté dans la fenêtre de style.  
  
 `pParentWnd`  
 Pointeur vers le parent du cadre.  
  
 `pContext`  
 Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure. Ce paramètre peut être **NULL**.  
  
### <a name="remarks"></a>Notes  
 Construire un `CFrameWnd` objet en deux étapes. Tout d’abord, appelez le constructeur, qui construit la `CFrameWnd` de l’objet, puis appelez `LoadFrame`, qui se charge de la fenêtre frame Windows et des ressources associées et attache la fenêtre frame à le `CFrameWnd` objet. Le `nIDResource` paramètre spécifie le menu, la table d’accélérateurs, l’icône et la ressource de chaîne du titre de la fenêtre frame.  
  
 Utilisez le **créer** fonction membre plutôt que `LoadFrame` lorsque vous souhaitez spécifier tous les paramètres de création de la fenêtre frame.  
  
 Le framework appelle `LoadFrame` lorsqu’il crée une fenêtre frame à l’aide d’un objet de modèle de document.  
  
 L’infrastructure utilise le `pContext` argument afin de spécifier les objets pour la connexion à la fenêtre frame, y compris les contenus des objets de vue. Vous pouvez définir le `pContext` argument **NULL** lorsque vous appelez `LoadFrame`.  
  
##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable  
 Lorsque ce membre de données est activé (qui est la valeur par défaut), éléments de menu qui n’ont pas `ON_UPDATE_COMMAND_UI` ou `ON_COMMAND` gestionnaires seront automatiquement désactivés lorsque l’utilisateur retire un menu déroulant.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Notes  
 Les éléments de menu qui ont un `ON_COMMAND` Gestionnaire mais aucun `ON_UPDATE_COMMAND_UI` gestionnaire sera automatiquement activé.  
  
 Lorsque ce membre de données est défini, les éléments de menu sont automatiquement activées dans la même façon que les boutons de barre d’outils sont activés.  
  
> [!NOTE]
> `m_bAutoMenuEnable` n’a aucun effet sur les éléments de menu de niveau supérieur.  
  
 Ce membre de données simplifie l’implémentation de commandes facultatives en fonction de la sélection actuelle et réduit le besoin d’écrire `ON_UPDATE_COMMAND_UI` gestionnaires pour activer ou désactiver des éléments de menu.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace  
 Appelez cette fonction membre pour négocier l’espace de bordure dans une fenêtre frame lors de l’activation de OLE sur place.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBorderCmd*  
 Contient l’une des valeurs suivantes à partir de la **enum BorderCmd**:  
  
- **borderGet** = 1  
  
- **borderRequest** = 2  
  
- **borderSet** = 3  
  
 `lpRectBorder`  
 Pointeur vers un [RECT](../../mfc/reference/rect-structure1.md) structure ou un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui spécifie les coordonnées de la bordure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est la **CFrameWnd** implémentation de la négociation d’espace OLE bordure.  
  
##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck  
 Appelé chaque fois qu’une action est effectuée dans la barre de contrôle spécifié.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `nID`  
 L’ID du contrôle de la barre est affichée.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la barre de contrôle existe ; Sinon, 0.  
  
##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp  
 Gère les MAJ + F1 Aide pour les éléments en place.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Notes  
 Pour activer l’aide contextuelle, vous devez ajouter une  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 instruction à votre `CFrameWnd` classe table des messages et également ajouter une entrée de table d’accélérateurs, généralement MAJ + F1, pour activer cette fonction membre.  
  
 Si votre application est un conteneur OLE, `OnContextHelp` place tous les éléments sur place sont contenues dans l’objet de fenêtre frame en mode d’aide. Le curseur se transforme en flèche et un point d’interrogation et l’utilisateur peut ensuite déplacer le pointeur de la souris et appuyez sur le bouton gauche de la souris pour sélectionner une boîte de dialogue, une fenêtre, un menu ou un bouton de commande. Cette fonction membre appelle la fonction Windows `WinHelp` avec le contexte d’aide de l’objet sous le curseur.  
  
##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient  
 Appelé par l’infrastructure pendant l’exécution de `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpcs`  
 Un pointeur vers un Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) structure.  
  
 `pContext`  
 Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Ne jamais appeler cette fonction.  
  
 L’implémentation par défaut de cette fonction crée un `CView` objet à partir des informations fournies dans `pContext`, si possible.  
  
 Remplacez cette fonction pour substituer les valeurs passées dans la `CCreateContext` de l’objet ou pour modifier les façon dont les contrôles dans la zone principale du client de la fenêtre frame sont créés. Le `CCreateContext` vous pouvez substituer les membres sont décrits dans le [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) classe.  
  
> [!NOTE]
>  Ne remplacez pas les valeurs passées dans la `CREATESTRUCT` structure. Ils sont uniquement à titre d’information. Si vous souhaitez remplacer le rectangle de la première fenêtre, par exemple, remplacer le `CWnd` fonction membre [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar  
 Cette fonction est appelée lorsque le système est sur le point de masquer la barre de menus dans l’application MFC en cours.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements permet à votre application effectuer des actions personnalisées lorsque le système est sur le point de masquer le menu. Vous ne pouvez pas empêcher le menu de masquer, mais vous pouvez, par exemple, appeler d’autres méthodes pour récupérer l’état ou le style de menu.  
  
##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode  
 Appelez cette fonction membre pour définir la fenêtre frame principale de l’application dans et en dehors du mode Aperçu avant impression.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Paramètres  
 *bPreview*  
 Spécifie s’il faut ou non à placer l’application en mode d’aperçu avant impression. La valeur **TRUE** à placer dans l’aperçu avant impression, **FALSE** pour annuler le mode Aperçu.  
  
 `pState`  
 Un pointeur vers un **CPrintPreviewState** structure.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut désactive toutes les barres d’outils standard et masque le menu principal et la fenêtre principale du client. Cela active les fenêtres de frame MDI dans les fenêtres de frame SDI temporaires.  
  
 Remplacez cette fonction membre pour personnaliser le masquage et affichage des barres de contrôles et d’autres parties de la fenêtre frame au cours de l’aperçu avant impression. Appeler l’implémentation de classe de base à partir de dans la version substituée.  
  
##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar  
 Cette fonction est appelée lorsque le système est sur le point d’afficher la barre de menus dans l’application MFC en cours.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements permet à votre application effectuer des actions personnalisées lorsque le menu est sur le point d’être affiché. Vous ne pouvez pas empêcher le menu Affichage, mais vous pouvez, par exemple, appeler d’autres méthodes pour récupérer l’état ou le style de menu.  
  
##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu  
 Appelé par le framework lorsque le menu associé est mis à jour.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCmdUI`  
 Un pointeur vers un [CCmdUI](../../mfc/reference/ccmdui-class.md) objet qui représente le menu qui a généré la commande de mise à jour. Appels du Gestionnaire de mise à jour la [activer](../../mfc/reference/ccmdui-class.md#enable) fonction membre de la `CCmdUI` par le biais de l’objet `pCmdUI` pour mettre à jour l’interface utilisateur.  
  
##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout  
 Appelé par le framework lorsque les barres de contrôles standard sont activées ou désactivées ou lorsque la fenêtre frame est redimensionnée.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bNotify`  
 Détermine si l’élément actif de la place de la fenêtre frame reçoit la notification de la modification de la disposition. Si **TRUE**, l’élément est notifié ; sinon **FALSE**.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction membre appelle le `CWnd` fonction membre `RepositionBars` pour repositionner les barres de contrôles dans le frame, ainsi que dans la fenêtre principale du client (généralement un `CView` ou **MDICLIENT**) .  
  
 Remplacez cette fonction membre pour contrôler l’apparence et le comportement des barres de contrôle après la modification de la disposition de la fenêtre frame. Appelez-le, par exemple, lorsque vous activez ou désactiver les barres de contrôle ou que vous ajoutez une autre barre de contrôle.  
  
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
 `lpszProfileName`  
 Nom d’une section dans le fichier d’initialisation ou une clé dans le Registre Windows où sont stockées les informations d’état.  
  
### <a name="remarks"></a>Notes  
 Ces informations peuvent être lues à partir du fichier d’initialisation en utilisant [LoadBarState](#loadbarstate). Informations stockées incluent la visibilité, l’orientation horizontale/verticale, station d’accueil d’état et la position de barre de contrôle.  
  
##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView  
 Désigne la vue spécifiée à la vue active pour l’aperçu riche.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Paramètres  
 `pViewNew`  
 Pointeur vers une vue d’être activées.  
  
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
 Spécifie un pointeur vers un [CView](../../mfc/reference/cview-class.md) objet, ou **NULL** pour aucune vue active.  
  
 `bNotify`  
 Spécifie si la vue doit être averti de l’activation. Si **TRUE**, `OnActivateView` est appelée pour le nouvel affichage ; si **FALSE**, il n’est pas.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction automatiquement que l’utilisateur met le focus sur une vue dans la fenêtre frame. Vous pouvez appeler explicitement `SetActiveView` pour déplacer le focus vers la vue spécifiée.  
  
##  <a name="setdockstate"></a>  CFrameWnd::SetDockState  
 Appelez cette fonction membre pour appliquer les informations d’état stockées dans un `CDockState` objet aux barres de contrôles de la fenêtre frame.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Paramètres  
 `state`  
 S’applique à l’état stocké aux barres de contrôles de la fenêtre frame.  
  
### <a name="remarks"></a>Notes  
 Pour restaurer un état antérieur des barres de contrôles, vous pouvez charger l’état stocké avec `CDockState::LoadState` ou `Serialize`, puis utilisez `SetDockState` pour l’appliquer aux barres de contrôles de la fenêtre frame. L’état précédent est stocké dans le `CDockState` avec l’objet `GetDockState`  
  
##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState  
 Définit l’état d’affichage du menu de l’application MFC actuelle masqué ou affiché.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `nState`|Spécifie s’il faut afficher ou masquer le menu. Le `nState` paramètre peut avoir les valeurs suivantes :<br /><br /> -AFX_MBS_VISIBLE (0 x 01) - affiche le menu si elle est masquée, mais n’a aucun effet s’il est visible.<br />-AFX_MBS_HIDDEN (0 x 02) - masque le menu si elle est visible, mais n’a aucun effet s’il est masqué.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode modifie correctement l’état de menu ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Si une erreur d’exécution se produit, cette méthode déclare en mode débogage et déclenche une exception dérivée de la [CException](../../mfc/reference/cexception-class.md) classe.  
  
##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility  
 Définit le comportement par défaut du menu de l’application MFC en cours pour être masquées ou visibles.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `nStyle`|Spécifie si le menu par défaut est masqué, ou n’est visible et a le focus. Le `nStyle` paramètre peut avoir les valeurs suivantes :<br /><br /> -AFX_MBV_KEEPVISIBLE (0 X 01)-<br />     Le menu est affiché en permanence et par défaut n’a pas le focus.<br />-AFX_MBV_DISPLAYONFOCUS (0 X 02)-<br />     Le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche ALT pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur la touche ALT ou sur ÉCHAP pour masquer le menu.<br />-AFX_MBV_ DISPLAYONFOCUS (0 x 02) &#124; AFX_MBV_DISPLAYONF10 (0 x 04)<br />     (combinaison (OR)) - le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche F10 pour afficher le menu et lui donner le focus. Si le menu s’affiche, appuyez sur F10 pour basculer le focus ou de désactiver le menu. Le menu s’affiche jusqu'à ce que vous appuyez sur la touche ALT ou sur ÉCHAP pour le masquer.|  
  
### <a name="remarks"></a>Notes  
 Si la valeur de la `nStyle` paramètre n’est pas valide, cette méthode déclare en mode débogage et déclenche [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en mode Release. En cas d’autres erreurs d’exécution, cette méthode déclare en mode débogage et déclenche une exception dérivée de la [CException](../../mfc/reference/cexception-class.md) classe.  
  
 Cette méthode affecte l’état des menus dans les applications écrites pour [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] et versions ultérieures.  
  
##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText  
 Appelez cette fonction pour placer une chaîne dans le volet de barre d’état qui possède un ID égal à 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Pointe vers la chaîne doit être placé sur la barre d’état.  
  
 `nID`  
 Chaîne d’ID de ressource de la chaîne doit être placé sur la barre d’état.  
  
### <a name="remarks"></a>Notes  
 C’est généralement le plus à gauche et la plus long, le volet de la barre d’état.  
  
##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition  
 Définit la position actuelle de la barre de progression Windows 7 affichée sur la barre des tâches.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Paramètres  
 `nProgressPos`  
 Spécifie la position à définir. Il doit être dans la plage définie par `SetProgressBarRange`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange  
 Définit la plage de la barre de progression Windows 7 affichée sur la barre des tâches.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Paramètres  
 `nRangeMin`  
 Valeur minimale.  
  
 `nRangeMax`  
 Valeur maximale.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState  
 Définit le type et l’état de l’indicateur de progression affichée sur un bouton de barre des tâches.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 `tbpFlags`  
 Indicateurs qui contrôlent l’état actuel du bouton de progression. Spécifiez uniquement une de ces indicateurs, car tous les États s’excluent mutuellement : TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon  
 Surchargé. S’applique à un segment de recouvrement à un bouton de barre des tâches pour indiquer l’état de l’application ou pour informer l’utilisateur.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDResource`  
 Spécifie l’ID de ressource d’une icône à utiliser en tant que le segment de recouvrement. Consultez la description pour `hIcon` pour plus d’informations.  
  
 `lpcszDescr`  
 Pointeur vers une chaîne qui fournit une version texte de remplacement des informations fournies par le segment de recouvrement, à des fins d’accessibilité.  
  
 `hIcon`  
 Le handle d’une icône à utiliser en tant que le segment de recouvrement. Il s’agit d’une petite icône, mesurer 16 x 16 pixels à 96 points par pouce (PPP). Si une icône de recouvrement est déjà appliquée sur le bouton de barre des tâches, ce segment existant est remplacé. Cette valeur peut être `NULL`. Comment un `NULL` valeur est traitée dépend de si le bouton de barre des tâches représente une fenêtre unique ou un groupe de windows. Il incombe à l’application appelante pour libérer `hIcon` quand il n’est plus nécessaire.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` en cas de réussite ; `FALSE` si la version de système d’exploitation est inférieure à Windows 7 ou si une erreur se produit de définition de l’icône.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settitle"></a>  CFrameWnd::SetTitle  
 Définit le titre de l’objet de fenêtre.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszTitle`  
 Pointeur vers une chaîne de caractères contenant le titre de l’objet de fenêtre.  
  
##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar  
 Appelez cette fonction membre pour afficher ou masquer la barre de contrôle.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBar`  
 Pointeur vers la barre de contrôle doit être affiché ou masqué.  
  
 `bShow`  
 Si **TRUE**, spécifie que la barre de contrôle doit être indiqué. Si **FALSE**, spécifie que la barre de contrôle doit être masqué.  
  
 *bDelay*  
 Si **TRUE**, retarder l’affichage de la barre de contrôle. Si **FALSE**, afficher le contrôle de barre immédiatement.  
  
##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows  
 Appelez cette fonction membre pour afficher toutes les fenêtres qui sont des descendants de le `CFrameWnd` objet.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 `bShow`  
 Spécifie si les fenêtres enfants doivent être affichés ou masqués.  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd (classe)](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd (classe)](../../mfc/reference/cmdichildwnd-class.md)   
 [CView (classe)](../../mfc/reference/cview-class.md)   
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass, structure](../../mfc/reference/cruntimeclass-structure.md)
