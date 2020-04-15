---
title: CFrameWnd, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 0fd104e377300233ef1526f6c453346555dd27d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373789"
---
# <a name="cframewnd-class"></a>CFrameWnd, classe

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
|[CFrameWnd::ActivateFrame](#activateframe)|Rend le cadre visible et accessible à l’utilisateur.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Définit la fenêtre du cadre pour modal.|
|[CFrameWnd::Créer](#create)|Appelez pour créer et initialiser la `CFrameWnd` fenêtre de cadre Windows associée à l’objet.|
|[CFrameWnd::CreateView](#createview)|Crée une vue dans un cadre `CView`qui n’est pas dérivé de .|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Docks une barre de contrôle.|
|[CFrameWnd::EnableDocking](#enabledocking)|Permet d’amarrer une barre de contrôle.|
|[CFrameWnd::EndModalState](#endmodalstate)|Termine l’état modal de la fenêtre de cadre. Permet toutes les fenêtres `BeginModalState`désactivées par .|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Flotte une barre de contrôle.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Retourne l’objet actif. `CDocument`|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Retourne l’objet actif. `CFrameWnd`|
|[CFrameWnd::GetActiveView](#getactiveview)|Retourne l’objet actif. `CView`|
|[CFrameWnd::GetControlBar](#getcontrolbar)|Récupère la barre de contrôle.|
|[CFrameWnd::GetDockState](#getdockstate)|Récupère l’état du quai d’une fenêtre de cadre.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Récupère l’état d’affichage du menu dans l’application MFC actuelle.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indique si le comportement par défaut du menu dans l’application MFC actuelle est soit caché, soit visible.|
|[CFrameWnd::GetMessageBar](#getmessagebar)|Retourne un pointeur à la barre d’état appartenant à la fenêtre du cadre.|
|[CFrameWnd::GetMessageString](#getmessagestring)|Récupère le message correspondant à une pièce d’identité de commande.|
|[CFrameWnd::GetTitle](#gettitle)|Récupère le titre de la barre de contrôle connexe.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Provoque `OnInitialUpdate` la fonction du membre appartenant à toutes les vues dans la fenêtre du cadre à être appelé.|
|[CFrameWnd::InModalState](#inmodalstate)|Retourne une valeur indiquant si oui ou non une fenêtre de cadre est dans un état modal.|
|[CFrameWnd::IsTracking](#istracking)|Détermine si la barre de séparation est actuellement déplacée.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Appelez pour charger une table d’accélérateur.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Appelez pour restaurer les paramètres de la barre de contrôle.|
|[CFrameWnd::LoadFrame](#loadframe)|Appelez pour créer dynamiquement une fenêtre de cadre à partir d’informations sur les ressources.|
|[CFrameWnd::NégocierBorderSpace](#negotiateborderspace)|Négocie l’espace de la frontière dans la fenêtre du cadre.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Appelé chaque fois qu’une action est effectuée sur la barre de contrôle spécifiée.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Gère l’aide SHIFT-F1 pour les articles sur place.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Définit la fenêtre principale du cadre de l’application en mode impression-aperçu.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Appelé par le cadre lorsque le menu associé est mis à jour.|
|[CFrameWnd::RecalcLayout](#recalclayout)|Repositionne les barres `CFrameWnd` de contrôle de l’objet.|
|[CFrameWnd::SaveBarState](#savebarstate)|Appelez pour enregistrer les paramètres de la barre de contrôle.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Désigne la vue spécifiée comme vue active pour Rich Preview.|
|[CFrameWnd::SetActiveView](#setactiveview)|Définit l’objet actif. `CView`|
|[CFrameWnd::SetDockState](#setdockstate)|Appelez pour amarrer la fenêtre du cadre dans la fenêtre principale.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Définit l’état d’affichage du menu dans l’application MFC actuelle à caché ou affiché.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Définit le comportement par défaut du menu dans l’application MFC actuelle pour être caché ou visible.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Définit le texte d’une barre de statut standard.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Définit la position actuelle de la barre de progression Windows 7 affichée sur la barre des tâches.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Définit la plage pour la barre de progression Windows 7 affichée sur la barre des tâches.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Définit le type et l’état de l’indicateur de progression affiché sur un bouton de barre des tâches.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Surchargé. Applique une superposition sur un bouton de barre des tâches pour indiquer l’état de l’application ou une notification à l’utilisateur.|
|[CFrameWnd::SetTitle](#settitle)|Définit le titre de la barre de contrôle connexe.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Appelez pour montrer la barre de contrôle.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Affiche toutes les fenêtres qui `CFrameWnd` sont des descendants de l’objet.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crée une fenêtre client pour le cadre.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Appelé avant le menu de l’application MFC actuelle est caché.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Appelé avant le menu de l’application MFC actuelle est affiché.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Contrôle les fonctionnalités automatiques d’activation et de désactivation pour les éléments du menu.|
|[CFrameWnd::rectDefault](#rectdefault)|Passez cette `CRect` statique comme paramètre `CFrameWnd` lors de la création d’un objet pour permettre à Windows de choisir la taille et la position initiales de la fenêtre.|

## <a name="remarks"></a>Notes

Pour créer une fenêtre de cadre utile `CFrameWnd`pour votre application, dérivez une classe de . Ajoutez des variables aux membres à la classe dérivée pour stocker des données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Il y a trois façons de construire une fenêtre de cadre :

- Construisez-le directement en utilisant [Create](#create).

- Construisez-le directement à l’aide [de LoadFrame](#loadframe).

- Construisez-le indirectement à l’aide d’un modèle de document.

Avant d’appeler `LoadFrame`l’un ou l’autre, `Create` vous devez construire l’objet de la fenêtre de cadre sur le tas à l’aide du **nouvel** opérateur C. Avant `Create`d’appeler, vous pouvez également enregistrer une classe de fenêtre avec la fonction globale [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) pour définir les styles d’icône et de classe pour le cadre.

Utilisez `Create` la fonction du membre pour passer les paramètres de création du cadre comme arguments immédiats.

`LoadFrame`nécessite moins `Create`d’arguments que , et récupère plutôt la plupart de ses valeurs par défaut à partir de ressources, y compris la légende du cadre, icône, table d’accélérateur, et le menu. Pour être `LoadFrame`accessible par , toutes ces ressources doivent avoir la même pièce d’identité de ressource (par exemple, IDR_MAINFRAME).

Lorsqu’un `CFrameWnd` objet contient des vues et des documents, ils sont créés indirectement par le cadre au lieu directement par le programmeur. L’objet `CDocTemplate` orchestre la création du cadre, la création des vues contenantes et la connexion des vues au document approprié. Les paramètres du `CDocTemplate` constructeur spécifient les `CRuntimeClass` trois classes concernées (document, cadre et vue). Un `CRuntimeClass` objet est utilisé par le cadre pour créer dynamiquement de nouvelles images lorsqu’il est spécifié par l’utilisateur (par exemple, en utilisant la commande De fichier Nouveau ou la fenêtre de fenêtre multiple interface de document (MDI) Nouvelle commande).

Une classe de fenêtre `CFrameWnd` de cadre dérivée doit être déclarée avec DECLARE_DYNCREATE afin que le mécanisme de RUNTIME_CLASS ci-dessus fonctionne correctement.

A `CFrameWnd` contient des implémentations par défaut pour effectuer les fonctions suivantes d’une fenêtre principale dans une application typique pour Windows:

- Une `CFrameWnd` fenêtre de cadre garde une trace d’une vue actuellement active qui est indépendante de la fenêtre active Windows ou de la mise au point d’entrée actuelle. Lorsque le cadre est réactivé, la `CView::OnActivateView`vue active est notifiée en appelant .

- Les messages de commande et de nombreux messages `OnSetFocus`communs `OnHScroll`de `OnVScroll` notification `CWnd`de cadre, y `CFrameWnd` compris ceux manipulés par le , , et les fonctions de , sont délégués par une fenêtre de cadre à la vue actuellement active.

- La vue actuellement active (ou la fenêtre de cadre pour enfants MDI actuellement active dans le cas d’un cadre MDI) peut déterminer la légende de la fenêtre du cadre. Cette fonctionnalité peut être désactivée en éteignant le FWS_ADDTOTITLE morceau de style de la fenêtre de cadre.

- Une `CFrameWnd` fenêtre de cadre gère le positionnement des barres de contrôle, des vues et d’autres fenêtres d’enfant à l’intérieur de la zone cliente de la fenêtre du cadre. Une fenêtre de cadre effectue également une mise à jour en temps d’activ de la barre d’outils et d’autres boutons de barre de contrôle. Une `CFrameWnd` fenêtre de cadre a également des implémentations par défaut de commandes pour basculer sur et en dehors de la barre d’outils et de la barre d’état.

- Une `CFrameWnd` fenêtre cadre gère la barre de menu principale. Lorsqu’un menu pop-up est affiché, la fenêtre du cadre utilise le mécanisme UPDATE_COMMAND_UI pour déterminer quels éléments de menu doivent être activés, désactivés ou vérifiés. Lorsque l’utilisateur sélectionne un élément de menu, la fenêtre du cadre met à jour la barre d’état avec la chaîne de message pour cette commande.

- Une `CFrameWnd` fenêtre de cadre dispose d’une table d’accélérateur facultative qui traduit automatiquement les accélérateurs de clavier.

- Une `CFrameWnd` fenêtre de cadre dispose `LoadFrame` d’un ensemble d’identification d’aide facultatif qui est utilisé pour une aide sensible au contexte. Une fenêtre de cadre est l’orchestrateur principal des états semimodaux tels que l’aide contextuelle (SHIFT-F1) et les modes d’impression-aperçu.

- Une `CFrameWnd` fenêtre de cadre ouvrira un fichier traîné du gestionnaire de fichiers et tombé sur la fenêtre du cadre. Si une extension de fichier est enregistrée et associée à l’application, la fenêtre de cadre répond à la demande d’échange `ShellExecute` de données dynamique (DDE) qui se produit lorsque l’utilisateur ouvre un fichier de données dans le gestionnaire de fichiers ou lorsque la fonction Windows est appelée.

- Si la fenêtre de cadre est la `CWinThread::m_pMainWnd`fenêtre d’application principale (c’est-à-dire), lorsque l’utilisateur ferme l’application, la fenêtre du cadre invite l’utilisateur à enregistrer tous les documents modifiés (pour `OnClose` et `OnQueryEndSession`).

- Si la fenêtre de cadre est la fenêtre d’application principale, la fenêtre de cadre est le contexte pour exécuter WinHelp. La fermeture de la fenêtre du cadre s’arrêtera WINHELP. EXE s’il a été lancé pour obtenir de l’aide pour cette application.

N’utilisez pas l’opérateur de **suppression** de C POUR détruire une fenêtre de cadre. Utilisez `CWnd::DestroyWindow` à la place. La `CFrameWnd` mise `PostNcDestroy` en œuvre de supprimera l’objet CMD lorsque la fenêtre sera détruite. Lorsque l’utilisateur ferme la fenêtre `OnClose` du `DestroyWindow`cadre, le gestionnaire par défaut appelle .

Pour plus `CFrameWnd`d’informations sur , voir [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFrameWnd::ActivateFrame

Appelez cette fonction de membre pour activer et restaurer la fenêtre de cadre afin qu’elle soit visible et disponible pour l’utilisateur.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Paramètres

*nCmdShow (en)*<br/>
Specifie le paramètre pour passer à [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Par défaut, le cadre est affiché et correctement restauré.

### <a name="remarks"></a>Notes

Cette fonction de membre est généralement appelée après un événement d’interface non utilisateur tel qu’un DDE, OLE, ou tout autre événement qui peut montrer la fenêtre de cadre ou son contenu à l’utilisateur.

La implémentation par défaut active le cadre et l’amène en haut de l’ordre Z et, si nécessaire, effectue les mêmes étapes pour la fenêtre de cadre principale de l’application.

Remplacer cette fonction de membre pour modifier la façon dont un cadre est activé. Par exemple, vous pouvez forcer les fenêtres des enfants MDI à être maximisées. Ajoutez la fonctionnalité appropriée, puis appelez la version de classe de base avec un *nCmdShow*explicite .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFrameWnd::BeginModalState

Appelez cette fonction membre pour rendre modale une fenêtre frame.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFrameWnd::CFrameWnd

Construit un `CFrameWnd` objet, mais ne crée pas la fenêtre de cadre visible.

```
CFrameWnd();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer la fenêtre visible.

## <a name="cframewndcreate"></a><a name="create"></a>CFrameWnd::Créer

Appelez pour créer et initialiser la `CFrameWnd` fenêtre de cadre Windows associée à l’objet.

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

*lpszClassName (en)*<br/>
Indique une chaîne de caractères à durée nulle qui nomme la classe Windows. Le nom de la classe `AfxRegisterWndClass` peut être `RegisterClass` n’importe quel nom enregistré auprès de la fonction globale ou de la fonction Windows. Si NULL, utilise les attributs par défaut `CFrameWnd` prédéfinis.

*lpszWindowName (en)*<br/>
Indique une chaîne de caractères non terminée qui représente le nom de fenêtre. Utilisé comme texte pour la barre de titre.

*dwStyle (en)*<br/>
Spécifie les attributs de [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) de fenêtre. Inclure le style FWS_ADDTOTITLE si vous voulez que la barre de titre affiche automatiquement le nom du document représenté dans la fenêtre.

*Rect*<br/>
Spécifie la taille et la position de la fenêtre. La valeur *rectDefault* permet à Windows de spécifier la taille et la position de la nouvelle fenêtre.

*pParentWnd*<br/>
Spécifie la fenêtre parente de cette fenêtre de cadre. Ce paramètre doit être NULL pour les fenêtres à cadre de haut niveau.

*lpszMenuName*<br/>
Identifie le nom de la ressource de menu à utiliser avec la fenêtre. Utilisez MAKEINTRESOURCE si le menu a une pièce d’identité integer au lieu d’une chaîne. Ce paramètre peut être NULL.

*dwExStyle (en anglais)*<br/>
Spécifie les attributs de [style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) étendu de fenêtre.

*pContext*<br/>
Spécifie un pointeur d’une structure [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation est réussie; sinon 0.

### <a name="remarks"></a>Notes

Construire `CFrameWnd` un objet en deux étapes. Tout d’abord, invoquer `CFrameWnd` le constructeur, `Create`qui construit l’objet, puis appeler `CFrameWnd` , ce qui crée la fenêtre de cadre Windows et l’attache à l’objet. `Create`initialise le nom de classe et le nom de fenêtre de la fenêtre de la fenêtre et enregistre les valeurs par défaut pour son style, son parent et son menu associé.

Utilisez `LoadFrame` plutôt `Create` que de charger la fenêtre de cadre à partir d’une ressource au lieu de spécifier ses arguments.

## <a name="cframewndcreateview"></a><a name="createview"></a>CFrameWnd::CreateView

Appelez `CreateView` pour créer une vue dans un cadre.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Spécifie le type de vue et de document.

*nID*<br/>
Le numéro d’identification d’une vue.

### <a name="return-value"></a>Valeur de retour

Pointer vers `CWnd` un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre pour `CView`créer des « vues » qui ne sont pas dérivées dans un cadre. Après `CreateView`l’appel, vous devez définir manuellement la vue à active et la définir pour être visible; ces tâches ne sont `CreateView`pas automatiquement effectuées par .

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFrameWnd::DockControlBar

Une barre de contrôle est amarrée à la fenêtre du cadre.

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
Points à la barre de contrôle à amarrer.

*nDockBarID (en)*<br/>
Détermine les côtés de la fenêtre du cadre à considérer pour l’amarrage. Il peut s’agir de 0, ou d’un ou plusieurs des éléments suivants :

- AFX_IDW_DOCKBAR_TOP Dock sur le côté supérieur de la fenêtre du cadre.

- AFX_IDW_DOCKBAR_BOTTOM Dock sur le côté inférieur de la fenêtre du cadre.

- AFX_IDW_DOCKBAR_LEFT Dock sur le côté gauche de la fenêtre du cadre.

- AFX_IDW_DOCKBAR_RIGHT Dock sur le côté droit de la fenêtre du cadre.

Si 0, la barre de commande peut être amarrée à n’importe quel côté activé pour l’amarrage dans la fenêtre de cadre de destination.

*lpRect*<br/>
Détermine, dans les coordonnées de l’écran, où la barre de commande sera amarrée dans la zone non-cilente de la fenêtre du cadre de destination.

### <a name="remarks"></a>Notes

La barre de contrôle sera amarrée à l’un des côtés de la fenêtre de cadre spécifiée dans les appels à la fois [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) et [CFrameWnd::EnableDocking](#enabledocking). Le côté choisi est déterminé par *nDockBarID*.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFrameWnd::EnableDocking

Appelez cette fonction pour activer les barres de contrôle amarrées dans une fenêtre de cadre.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

*dwDockStyle (en)*<br/>
Précise quels côtés de la fenêtre du cadre peuvent servir de sites d’amarrage pour les barres de contrôle. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- CBRS_ALIGN_TOP permet l’amarrage au sommet de la zone client.

- CBRS_ALIGN_BOTTOM permet l’amarrage au bas de la zone client.

- CBRS_ALIGN_LEFT permet l’amarrage sur le côté gauche de la zone client.

- CBRS_ALIGN_RIGHT permet l’amarrage sur le côté droit de la zone client.

- CBRS_ALIGN_ANY permet l’amarrage de n’importe quel côté de la zone client.

### <a name="remarks"></a>Notes

Par défaut, les barres de commande seront amarrées sur un côté de la fenêtre du cadre dans l’ordre suivant : en haut, en bas, à gauche, à droite.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CToolBar:Créer](../../mfc/reference/ctoolbar-class.md#create).

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFrameWnd::EndModalState

Appelez cette fonction membre pour changer une fenêtre frame modale en fenêtre frame non modale.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Notes

`EndModalState`permet toutes les fenêtres désactivées par [BeginModalState](#beginmodalstate).

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar

Appelez cette fonction pour provoquer une barre de contrôle de ne pas être amarré à la fenêtre du cadre.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
Points à la barre de commande à flotter.

*Point*<br/>
L’emplacement, dans les coordonnées de l’écran, où le coin supérieur gauche de la barre de contrôle sera placé.

*dwStyle (en)*<br/>
Précise s’il faut aligner la barre de contrôle horizontalement ou verticalement dans sa nouvelle fenêtre de cadre. Il peut être l’un des suivants:

- CBRS_ALIGN_TOP Oriente la barre de contrôle verticalement.

- CBRS_ALIGN_BOTTOM Oriente la barre de contrôle verticalement.

- CBRS_ALIGN_LEFT Oriente la barre de contrôle horizontalement.

- CBRS_ALIGN_RIGHT Oriente la barre de contrôle horizontalement.

Si les styles sont adoptés spécifiant à la fois l’orientation horizontale et verticale, la barre d’outils sera orientée horizontalement.

### <a name="remarks"></a>Notes

En règle générale, cela se fait lors du démarrage de l’application lorsque le programme rétablit les paramètres de l’exécution précédente.

Cette fonction est appelée par le cadre lorsque l’utilisateur provoque une opération de chute en libérant le bouton de la souris gauche tout en faisant glisser la barre de contrôle sur un emplacement qui n’est pas disponible pour l’amarrage.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFrameWnd::GetActiveDocument

Appelez cette fonction de membre pour `CDocument` obtenir un pointeur sur le courant attaché à la vue active actuelle.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’actuel [CDocument](../../mfc/reference/cdocument-class.md). S’il n’y a pas de document actuel, renvoie NULL.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFrameWnd::GetActiveFrame

Appelez cette fonction de membre pour obtenir un pointeur à la fenêtre active d’interface de document multiple (MDI) d’une fenêtre de cadre MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre active de l’enfant MDI. Si l’application est une application SDI, ou si la fenêtre de cadre MDI n’a pas de document actif, le **pointeur** implicite sera retourné.

### <a name="remarks"></a>Notes

S’il n’y a pas d’enfant MDI actif ou si l’application est une interface de document unique (SDI), l’implicite **ce** pointeur est retourné.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFrameWnd::GetActiveView

Appelez cette fonction de membre pour obtenir un pointeur à la `CFrameWnd`vue active (le cas échéant) attaché à une fenêtre de cadre ( ).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’actuel [CView](../../mfc/reference/cview-class.md). S’il n’y a pas de vue actuelle, renvoie NULL.

### <a name="remarks"></a>Notes

Cette fonction renvoie NULL lorsqu’on appelle `CMDIFrameWnd`pour une fenêtre de cadre principal MDI ( ). Dans une application MDI, la fenêtre de cadre principal MDI n’a pas de vue qui lui est associée. Au lieu de cela, chaque fenêtre enfant individuel ( `CMDIChildWnd`) a une ou plusieurs vues associées. La vue active dans une demande D’IED peut être obtenue en trouvant d’abord la fenêtre active de l’enfant MDI, puis en trouvant la vue active pour cette fenêtre d’enfant. La fenêtre active de l’enfant MDI peut être trouvée en appelant la fonction `MDIGetActive` ou `GetActiveFrame` comme démontré dans ce qui suit :

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFrameWnd::GetControlBar

Appelez `GetControlBar` pour accéder à la barre de contrôle associée à l’ID.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Le numéro d’identification d’une barre de contrôle.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la barre de contrôle qui est associée à l’ID.

### <a name="remarks"></a>Notes

Le paramètre *nID* se réfère à `Create` l’identifiant unique transmis à la méthode de la barre de contrôle. Pour plus d’informations sur les barres de contrôle, consultez le sujet intitulé [Control Bars](../../mfc/control-bars.md).

`GetControlBar`retournera la barre de contrôle même si elle flotte et n’est donc pas actuellement une fenêtre enfant du cadre.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFrameWnd::GetDockState

Appelez cette fonction membre pour stocker des informations d’état sur les barres de commande de la fenêtre de cadre dans un `CDockState` objet.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Paramètres

*État*<br/>
Contient l’état actuel des barres de contrôle de la fenêtre de cadre au retour.

### <a name="remarks"></a>Notes

Vous pouvez ensuite écrire `CDockState` le `CDockState::SaveState` contenu `Serialize`de stockage à l’aide ou . Si vous souhaitez plus tard restaurer les barres de `CDockState::LoadState` contrôle `Serialize`à `SetDockState` un état précédent, chargez l’état avec ou, puis appelez pour appliquer l’état précédent aux barres de contrôle de la fenêtre de cadre.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState

Récupère l’état d’affichage du menu dans l’application MFC actuelle.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Valeur de retour

La valeur de rendement peut avoir les valeurs suivantes :

- AFX_MBS_VISIBLE (0x01) - Le menu est visible.

- AFX_MBS_HIDDEN (0x02) - Le menu est caché.

### <a name="remarks"></a>Notes

Si une erreur de temps d’exécution se produit, cette méthode s’affirme en mode Debug et soulève une exception dérivée de la classe [CException.](../../mfc/reference/cexception-class.md)

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility

Indique si l’état par défaut du menu dans l’application MFC actuelle est caché ou visible.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Valeur de retour

La méthode retourne l'une des valeurs suivantes :

- AFX_MBV_KEEPVISIBLE (0x01) - Le menu est affiché en tout temps, et par défaut n’a pas la mise au point.

- AFX_MBV_DISPLAYONFOCUS (0x02) - Le menu est caché par défaut. Si le menu est caché, appuyez sur la touche ALT pour afficher le menu et lui donner la mise au point. Si le menu est affiché, appuyez sur la clé ALT ou ESC pour le cacher.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (combinaison bitwise (OR)) - Le menu est caché par défaut. Si le menu est caché, appuyez sur la touche F10 pour afficher le menu et lui donner la mise au point. Si le menu est affiché, appuyez sur la touche F10 pour basculer l’accent sur ou hors du menu. Le menu est affiché jusqu’à ce que vous appuyez sur la clé ALT ou ESC pour le cacher.

### <a name="remarks"></a>Notes

Si une erreur de temps d’exécution se produit, cette méthode s’affirme en mode Debug et soulève une exception dérivée de la classe [CException.](../../mfc/reference/cexception-class.md)

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFrameWnd::GetMessageBar

Appelez cette fonction de membre pour obtenir un pointeur à la barre d’état.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre de la barre d’état.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFrameWnd::GetMessageString

Remplacer cette fonction pour fournir des chaînes personnalisées pour les cartes d’application.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Id de ressources du message souhaité.

*rMessage (en)*<br/>
`CString`objet dans lequel placer le message.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut charge simplement la chaîne spécifiée par *nID* à partir du fichier de ressources. Cette fonction est appelée par le cadre lorsque la chaîne de messages dans la barre d’état doit être mise à jour.

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFrameWnd::GetTitle

Récupère le titre de l’objet de fenêtre.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le titre actuel de l’objet de fenêtre.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame

Appelez `IntitialUpdateFrame` après avoir créé `Create`un nouveau cadre avec .

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Paramètres

*pDoc (en)*<br/>
Indique le document auquel la fenêtre du cadre est associée. Sa valeur peut être NULL.

*bMakeVisible*<br/>
Si VRAI, indique que le cadre doit devenir visible et actif. Si FALSE, aucun descendant n’est visible.

### <a name="remarks"></a>Notes

Cela provoque toutes les vues dans `OnInitialUpdate` cette fenêtre de cadre pour recevoir leurs appels.

En outre, s’il n’y avait pas auparavant une vue active, la vue principale de la fenêtre de cadre est rendue active. La vue principale est une vue avec une carte d’identité pour enfants de AFX_IDW_PANE_FIRST. Enfin, la fenêtre de cadre est rendue visible si *bMakeVisible* n’est paszero. Si *bMakeVisible* est 0, la mise au point actuelle et l’état visible de la fenêtre du cadre resteront inchangés. Il n’est pas nécessaire d’appeler cette fonction lors de l’utilisation de la mise en œuvre du cadre de File New et File Open.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>CFrameWnd::InModalState

Appelez cette fonction de membre pour vérifier si une fenêtre de cadre est modale ou sans mode.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si oui; sinon 0.

## <a name="cframewndistracking"></a><a name="istracking"></a>CFrameWnd::IsTracking

Appelez cette fonction de membre pour déterminer si la barre de séparaur dans la fenêtre est actuellement déplacée.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si une opération de splitter est en cours; sinon 0.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFrameWnd::LoadAccelTable

Appelez pour charger la table d’accélérateur spécifiée.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName (en)*<br/>
Identifie le nom de la ressource d’accélérateur. Utilisez MAKEINTRESOURCE si la ressource est identifiée avec une pièce d’identité integer.

### <a name="return-value"></a>Valeur de retour

Nonzero si la table d’accélérateur a été chargée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Une seule table peut être chargée à la fois.

Les tables d’accélérateur chargées des ressources sont libérées automatiquement lorsque l’application prend fin.

Si vous `LoadFrame` appelez pour créer la fenêtre de cadre, le cadre charge une table d’accélérateur avec le menu et les ressources d’icône, et un appel ultérieur à cette fonction de membre est alors inutile.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFrameWnd::LoadBarState

Appelez cette fonction pour restaurer les paramètres de chaque barre de contrôle appartenant à la fenêtre de cadre.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Nom d’une section dans le fichier d’initialisation (INI) ou d’une clé dans le registre Windows où les informations de l’État sont stockées.

### <a name="remarks"></a>Notes

L’information restaurée comprend la visibilité, l’orientation horizontale/verticale, l’état d’amarrage et la position de la barre de contrôle.

Les paramètres que vous souhaitez restaurer doivent être `LoadBarState`écrits au registre avant d’appeler . Écrivez l’information au registre en appelant [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Écrivez les informations au fichier INI en appelant [SaveBarState](#savebarstate).

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFrameWnd::LoadFrame

Appelez pour créer dynamiquement une fenêtre de cadre à partir d’informations sur les ressources.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*nIDResource (en)*<br/>
L’ID des ressources partagées associées à la fenêtre du cadre.

*dwDefaultStyle (en)*<br/>
Le [style](../../mfc/reference/styles-used-by-mfc.md#window-styles)du cadre . Inclure le style FWS_ADDTOTITLE si vous voulez que la barre de titre affiche automatiquement le nom du document représenté dans la fenêtre.

*pParentWnd*<br/>
Un pointeur pour le parent du cadre.

*pContext*<br/>
Un pointeur vers une structure [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Ce paramètre peut être NULL.

### <a name="remarks"></a>Notes

Construire `CFrameWnd` un objet en deux étapes. Tout d’abord, invoquer `CFrameWnd` le constructeur, `LoadFrame`qui construit l’objet, puis appeler , qui charge `CFrameWnd` la fenêtre de cadre Windows et les ressources associées et attache la fenêtre de cadre à l’objet. Le *paramètre nIDResource* spécifie le menu, la table d’accélérateur, l’icône et la ressource de chaîne du titre pour la fenêtre du cadre.

Utilisez `Create` la fonction `LoadFrame` du membre plutôt que lorsque vous souhaitez spécifier tous les paramètres de création de la fenêtre de cadre.

Le cadre `LoadFrame` appelle lorsqu’il crée une fenêtre de cadre à l’aide d’un objet de modèle de document.

Le cadre utilise l’argument *pContext* pour spécifier les objets à connecter à la fenêtre du cadre, y compris les objets de vue contenus. Vous pouvez définir l’argument *pContext* à NULL lorsque vous appelez `LoadFrame`.

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable

Lorsque ce membre de données est activé (ce qui est par défaut), les éléments de menu qui n’ont pas de ON_UPDATE_COMMAND_UI ou de ON_COMMAND les gestionnaires seront automatiquement désactivés lorsque l’utilisateur tire vers le bas d’un menu.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Notes

Les éléments de menu qui ont un gestionnaire de ON_COMMAND mais aucun gestionnaire de ON_UPDATE_COMMAND_UI ne seront automatiquement activés.

Lorsque ce membre de données est défini, les éléments de menu sont automatiquement activés de la même manière que les boutons de la barre d’outils sont activés.

> [!NOTE]
> `m_bAutoMenuEnable`n’a aucun effet sur les éléments de menu de haut niveau.

Ce membre des données simplifie la mise en œuvre de commandes facultatives en fonction de la sélection actuelle et réduit la nécessité d’écrire ON_UPDATE_COMMAND_UI les gestionnaires pour permettre et désactiver les éléments de menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWnd::NégocierBorderSpace

Appelez cette fonction de membre pour négocier l’espace de frontière dans une fenêtre de cadre pendant l’activation de l’OLE à l’endroit.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Paramètres

*nBorderCmd (en)*<br/>
Contient l’une des `enum BorderCmd`valeurs suivantes de la :

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie les coordonnées de la bordure.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de `CFrameWnd` membre est la mise en œuvre de la négociation spatiale OLE frontière.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFrameWnd::OnBarCheck

Appelé chaque fois qu’une action est effectuée sur la barre de contrôle spécifiée.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’ID de la barre de contrôle étant montré.

### <a name="return-value"></a>Valeur de retour

Nonzero si la barre de contrôle existait; sinon 0.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWnd::OnContextHelp

Gère l’aide SHIFT-F1 pour les articles sur place.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Notes

Pour activer une aide sensible au contexte, vous devez ajouter un

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

indiquez `CFrameWnd` à votre carte de message de classe et ajoutez également une entrée de table d’accélérateur, typiquement SHIFT-F1, pour activer cette fonction de membre.

Si votre application est un `OnContextHelp` conteneur OLE, met tous les éléments en place contenus dans l’objet de fenêtre de cadre en mode Aide. Le curseur se transforme en flèche et un point d’interrogation, et l’utilisateur peut alors déplacer le pointeur de la souris et appuyer sur le bouton de la souris gauche pour sélectionner une boîte de dialogue, une fenêtre, un menu ou un bouton de commande. Cette fonction membre appelle `WinHelp` la fonction Windows avec le contexte d’aide de l’objet sous le curseur.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFrameWnd::OnCreateClient

Appelé par le cadre `OnCreate`lors de l’exécution de .

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Paramètres

*Retard*<br/>
Un pointeur vers une structure Windows [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pContext*<br/>
Un pointeur vers une structure [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md)

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

N’appelez jamais cette fonction.

La mise en œuvre par défaut de cette fonction crée un `CView` objet à partir des informations fournies dans *pContext*, si possible.

Remplacer cette fonction pour remplacer les `CCreateContext` valeurs passées dans l’objet ou pour modifier la façon dont les contrôles dans la zone client principale de la fenêtre de cadre sont créés. Les `CCreateContext` membres que vous pouvez remplacer sont décrits dans la classe [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md)

> [!NOTE]
> Ne remplacez pas `CREATESTRUCT` les valeurs passées dans la structure. Ils sont pour une utilisation informationnelle seulement. Si vous souhaitez remplacer le rectangle de fenêtre initial, par exemple, remplacer la `CWnd` fonction membre [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar

Cette fonction est appelée lorsque le système est sur le point de cacher la barre de menu dans l’application MFC actuelle.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Notes

Ce gestionnaire d’événements permet à votre application d’effectuer des actions personnalisées lorsque le système est sur le point de cacher le menu. Vous ne pouvez pas empêcher le menu d’être caché, mais vous pouvez, par exemple, appeler d’autres méthodes pour récupérer le style de menu ou l’état.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode

Appelez cette fonction membre pour définir la fenêtre frame principale de l’application dans et en dehors du mode Aperçu avant impression.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Paramètres

*bPréview (en)*<br/>
Précise s’il faut ou non placer l’application en mode impression-aperçu. Définissez à TRUE pour placer en aperçu d’impression, FALSE pour annuler le mode aperçu.

*pState (États-Unis)*<br/>
Un pointeur `CPrintPreviewState` vers une structure.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut désactive toutes les barres d’outils standard et cache le menu principal et la fenêtre client principale. Cela transforme les fenêtres de cadre MDI en fenêtres provisoires de cadre SDI.

Remplacer cette fonction de membre pour personnaliser la dissimulation et la démonstration des barres de contrôle et autres parties de fenêtre de cadre pendant l’aperçu d’impression. Appelez l’implémentation de la classe de base à partir de la version prépondérer.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar

Cette fonction est appelée lorsque le système est sur le point d’afficher la barre de menu dans l’application MFC actuelle.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Notes

Ce gestionnaire d’événements permet à votre application d’effectuer des actions personnalisées lorsque le menu est sur le point d’être affiché. Vous ne pouvez pas empêcher l’affichage du menu, mais vous pouvez, par exemple, appeler d’autres méthodes pour récupérer le style ou l’état du menu.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu

Appelé par le cadre lorsque le menu associé est mis à jour.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur vers un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) représentant le menu qui a généré la commande de mise à jour. Le gestionnaire de [Enable](../../mfc/reference/ccmdui-class.md#enable) mise à `CCmdUI` jour appelle la fonction membre Enable de l’objet via *pCmdUI* pour mettre à jour l’interface utilisateur.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFrameWnd::RecalcLayout

Appelé par le cadre lorsque les barres de contrôle standard sont basculent sur ou hors ou lorsque la fenêtre de cadre est resized.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

*bNotifier*<br/>
Détermine si l’élément actif sur place de la fenêtre de trame reçoit une notification de la modification de mise en page. Si VRAI, l’article est notifié; autrement FALSE.

### <a name="remarks"></a>Notes

La mise en œuvre `CWnd` par `RepositionBars` défaut de cette fonction membre appelle la fonction membre à `CView` repositionner toutes les barres de contrôle dans le cadre ainsi que dans la fenêtre client principale (généralement un ou MDICLIENT).

Remplacer cette fonction de membre pour contrôler l’apparence et le comportement des barres de contrôle après que la disposition de la fenêtre de cadre a changé. Par exemple, appelez-le lorsque vous allumez ou éteignez les barres de contrôle ou ajoutez une autre barre de contrôle.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFrameWnd::rectDefault

Passez cette `CRect` statique comme paramètre lors de la création d’une fenêtre pour permettre à Windows de choisir la taille et la position initiales de la fenêtre.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFrameWnd::SaveBarState

Appelez cette fonction pour stocker des informations sur chaque barre de contrôle appartenant à la fenêtre du cadre.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Nom d’une section dans le fichier d’initialisation ou d’une clé dans le registre Windows où les informations de l’État sont stockées.

### <a name="remarks"></a>Notes

Ces informations peuvent être lues à partir du fichier d’initialisation à l’aide [de LoadBarState](#loadbarstate). Les informations stockées comprennent la visibilité, l’orientation horizontale/verticale, l’état d’amarrage et la position de la barre de commande.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView

Désigne la vue spécifiée comme vue active pour Rich Preview.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Paramètres

*pViewNew*<br/>
Un pointeur à une vue à activer.

### <a name="remarks"></a>Notes

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFrameWnd::SetActiveView

Appelez cette fonction de membre pour définir la vue active.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

*pViewNew*<br/>
Spécifie un pointeur vers un objet [CView,](../../mfc/reference/cview-class.md) ou NULL sans vue active.

*bNotifier*<br/>
Précise si la vue doit être notifiée de l’activation. Si VRAI, `OnActivateView` est appelé pour le nouveau point de vue; si FALSE, ce n’est pas le cas.

### <a name="remarks"></a>Notes

Le cadre appellera cette fonction automatiquement que l’utilisateur change la mise au point à une vue dans la fenêtre du cadre. Vous pouvez `SetActiveView` appeler explicitement pour modifier la mise au point vers la vue spécifiée.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFrameWnd::SetDockState

Appelez cette fonction membre pour appliquer `CDockState` les informations d’état stockées dans un objet aux barres de contrôle de la fenêtre de cadre.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Paramètres

*État*<br/>
Appliquer l’état stocké sur les barres de contrôle de la fenêtre du cadre.

### <a name="remarks"></a>Notes

Pour restaurer un état antérieur des barres de commande, `Serialize`vous `SetDockState` pouvez charger l’état stocké avec `CDockState::LoadState` ou, puis l’utiliser pour l’appliquer aux barres de contrôle de la fenêtre de cadre. L’état précédent est `CDockState` stocké dans l’objet avec`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState

Définit l’état d’affichage du menu dans l’application MFC actuelle à caché ou affiché.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nState (États-Unis)*|[dans] Précise s’il faut afficher ou cacher le menu. Le *paramètre nState* peut avoir les valeurs suivantes :<br /><br />- AFX_MBS_VISIBLE (0x01) - Affiche le menu s’il est caché, mais n’a aucun effet s’il est visible.<br />- AFX_MBS_HIDDEN (0x02) - Cache le menu s’il est visible, mais n’a aucun effet s’il est caché.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode change avec succès l’état du menu; autrement, FALSE.

### <a name="remarks"></a>Notes

Si une erreur de temps d’exécution se produit, cette méthode s’affirme en mode Debug et soulève une exception dérivée de la classe [CException.](../../mfc/reference/cexception-class.md)

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility

Définit le comportement par défaut du menu dans l’application MFC actuelle pour être caché ou visible.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nStyle*|[dans] Précise si le menu est par défaut caché, ou est visible et a la mise au point. Le *paramètre nStyle* peut avoir les valeurs suivantes :<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     Le menu est affiché en tout temps, et par défaut n’a pas la mise au point.<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     Le menu est caché par défaut. Si le menu est caché, appuyez sur la touche ALT pour afficher le menu et lui donner la mise au point. Si le menu est affiché, appuyez sur la clé ALT ou ESC pour masquer le menu.<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (combinaison bitwise (OR)) - Le menu est caché par défaut. Si le menu est caché, appuyez sur la touche F10 pour afficher le menu et lui donner la mise au point. Si le menu est affiché, appuyez sur la touche F10 pour basculer l’accent sur ou hors du menu. Le menu est affiché jusqu’à ce que vous appuyez sur la clé ALT ou ESC pour le cacher.|

### <a name="remarks"></a>Notes

Si la valeur du paramètre *nStyle* n’est pas valide, cette méthode l’affirme en mode Debug et augmente [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en mode Version. En cas d’autres erreurs de temps d’exécution, cette méthode s’affirme en mode Debug et soulève une exception dérivée de la classe [CException.](../../mfc/reference/cexception-class.md)

Cette méthode affecte l’état des menus dans les applications écrites pour Windows Vista et plus tard.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFrameWnd::SetMessageText

Appelez cette fonction pour placer une chaîne dans la vitre de l’état-bar qui a une pièce d’identité de 0.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Points à la corde à placer sur la barre d’état.

*nID*<br/>
Id de ressources de chaîne de la chaîne à placer sur la barre d’état.

### <a name="remarks"></a>Notes

Il s’agit généralement de la vitre la plus gauche et la plus longue de la barre d’état.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition

Définit la position actuelle de la barre de progression Windows 7 affichée sur la barre des tâches.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Paramètres

*nProgressPos*<br/>
Spécifie la position à définir. Il doit être dans `SetProgressBarRange`la plage définie par .

### <a name="remarks"></a>Notes

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange

Définit la plage de la barre de progression Windows 7 affichée sur la barre des tâches.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Paramètres

*nRangeMin (en)*<br/>
Valeur minimale.

*nRangeMax (en)*<br/>
Valeur maximale.

### <a name="remarks"></a>Notes

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState

Définit le type et l’état de l’indicateur de progression affiché sur un bouton de barre des tâches.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Paramètres

*tbpFlags*<br/>
Drapeaux qui contrôlent l’état actuel du bouton de progression. Spécifier un seul des drapeaux suivants parce que tous les États s’excluent mutuellement : TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Notes

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon

Surchargé. Applique une superposition sur un bouton de barre des tâches pour indiquer l’état de l’application ou pour en informer l’utilisateur.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Paramètres

*nIDResource (en)*<br/>
Spécifie l’ID de ressources d’une icône à utiliser comme superposition. Voir la description pour *hIcon* pour plus de détails.

*lpcszDescr*<br/>
Un pointeur à une chaîne qui fournit une version texte alt de l’information transmise par la superposition, à des fins d’accessibilité.

*hIcon (en)*<br/>
Le manche d’une icône à utiliser comme superposition. Il devrait s’agir d’une petite icône, mesurant 16x16 pixels à 96 points par pouce (dpi). Si une icône de superposition est déjà appliquée sur le bouton de la barre des tâches, cette superposition existante est remplacée. Cette valeur peut être NULL. La façon dont une valeur NULL est traitée dépend du fait que le bouton de la barre des tâches représente une seule fenêtre ou un groupe de fenêtres. Il est de la responsabilité de l’application d’appel de libérer *hIcon* quand il n’est plus nécessaire.

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès; FALSE si la version OS est inférieure à Windows 7 ou si une erreur se produit le réglage de l’icône.

### <a name="remarks"></a>Notes

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFrameWnd::SetTitle

Définit le titre de l’objet de fenêtre.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Paramètres

*lpszTitle (lpszTitle)*<br/>
Un pointeur à une chaîne de caractère contenant le titre de l’objet de fenêtre.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFrameWnd::ShowControlBar

Appelez cette fonction de membre pour montrer ou cacher la barre de contrôle.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
Pointeur vers la barre de contrôle à montrer ou à cacher.

*bShow (en)*<br/>
Si TRUE, spécifie que la barre de contrôle doit être affichée. Si FALSE, spécifie que la barre de contrôle doit être cachée.

*bDelay (en)*<br/>
Si VRAI, retard montrant la barre de contrôle. Si FALSE, montrez immédiatement la barre de contrôle.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows

Appelez cette fonction de membre pour montrer `CFrameWnd` toutes les fenêtres qui sont des descendants de l’objet.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
Précise si les fenêtres possédées doivent être montrées ou cachées.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd, classe](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md)
