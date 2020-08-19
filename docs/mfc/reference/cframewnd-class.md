---
title: CFrameWnd (classe)
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
ms.openlocfilehash: 5e40f08447d24eed51588b5c2dfa87e289d99eed
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561575"
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
|[CFrameWnd :: CFrameWnd](#cframewnd)|Construit un objet `CFrameWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFrameWnd :: ActivateFrame](#activateframe)|Rend le frame visible et accessible à l’utilisateur.|
|[CFrameWnd :: BeginModalState](#beginmodalstate)|Définit la fenêtre frame sur modale.|
|[CFrameWnd :: Create](#create)|Appelez pour créer et initialiser la fenêtre frame Windows associée à l' `CFrameWnd` objet.|
|[CFrameWnd :: CreateView](#createview)|Crée une vue dans un frame qui n’est pas dérivé de `CView` .|
|[CFrameWnd ::D ockControlBar](#dockcontrolbar)|Ancre une barre de contrôle.|
|[CFrameWnd :: EnableDocking](#enabledocking)|Permet à une barre de contrôle d’être ancrée.|
|[CFrameWnd :: EndModalState](#endmodalstate)|Met fin à l’État modal de la fenêtre frame. Active toutes les fenêtres désactivées par `BeginModalState` .|
|[CFrameWnd :: FloatControlBar](#floatcontrolbar)|Flotte une barre de contrôle.|
|[CFrameWnd :: GetActiveDocument](#getactivedocument)|Retourne l' `CDocument` objet actif.|
|[CFrameWnd :: GetActiveFrame](#getactiveframe)|Retourne l' `CFrameWnd` objet actif.|
|[CFrameWnd :: GetActiveView](#getactiveview)|Retourne l' `CView` objet actif.|
|[CFrameWnd :: GetControlBar](#getcontrolbar)|Récupère la barre de contrôle.|
|[CFrameWnd :: GetDockState](#getdockstate)|Récupère l’état d’ancrage d’une fenêtre frame.|
|[CFrameWnd :: GetMenuBarState](#getmenubarstate)|Récupère l’état d’affichage du menu dans l’application MFC actuelle.|
|[CFrameWnd :: GetMenuBarVisibility](#getmenubarvisibility)|Indique si le comportement par défaut du menu dans l’application MFC actuelle est soit masqué, soit visible.|
|[CFrameWnd :: GetMessageBar](#getmessagebar)|Retourne un pointeur vers la barre d’État qui appartient à la fenêtre frame.|
|[CFrameWnd :: GetMessageString](#getmessagestring)|Récupère le message correspondant à un ID de commande.|
|[CFrameWnd :: GetTitle](#gettitle)|Récupère le titre de la barre de contrôle associée.|
|[CFrameWnd :: InitialUpdateFrame](#initialupdateframe)|Entraîne l' `OnInitialUpdate` appel de la fonction membre appartenant à toutes les vues dans la fenêtre frame.|
|[CFrameWnd :: InModalState](#inmodalstate)|Retourne une valeur indiquant si une fenêtre frame est dans un État modal.|
|[CFrameWnd :: IsTracking](#istracking)|Détermine si la barre de fractionnement est en cours de déplacement.|
|[CFrameWnd :: LoadAccelTable](#loadacceltable)|Appelez pour charger une table d’accélérateurs.|
|[CFrameWnd :: LoadBarState](#loadbarstate)|Appelez pour restaurer les paramètres de la barre de contrôle.|
|[CFrameWnd :: LoadFrame](#loadframe)|Appelez pour créer dynamiquement une fenêtre frame à partir d’informations sur les ressources.|
|[CFrameWnd :: NegotiateBorderSpace](#negotiateborderspace)|Négocie l’espace de bordure dans la fenêtre frame.|
|[CFrameWnd :: OnBarCheck](#onbarcheck)|Appelé chaque fois qu’une action est exécutée sur la barre de contrôle spécifiée.|
|[CFrameWnd :: OnContextHelp](#oncontexthelp)|Gère l’aide de MAJ + F1 pour les éléments sur place.|
|[CFrameWnd :: OnSetPreviewMode](#onsetpreviewmode)|Définit la fenêtre frame principale de l’application dans et hors du mode d’aperçu avant impression.|
|[CFrameWnd :: OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Appelé par le Framework lorsque le menu associé est mis à jour.|
|[CFrameWnd :: RecalcLayout](#recalclayout)|Repositionne les barres de contrôles de l' `CFrameWnd` objet.|
|[CFrameWnd :: SaveBarState](#savebarstate)|Appelez pour enregistrer les paramètres de la barre de contrôle.|
|[CFrameWnd :: SetActivePreviewView](#setactivepreviewview)|Désigne la vue spécifiée comme étant la vue active de la version préliminaire complète.|
|[CFrameWnd :: SetActiveView](#setactiveview)|Définit l' `CView` objet actif.|
|[CFrameWnd :: SetDockState](#setdockstate)|Appelez pour ancrer la fenêtre frame dans la fenêtre principale.|
|[CFrameWnd :: SetMenuBarState](#setmenubarstate)|Définit l’état d’affichage du menu dans l’application MFC actuelle sur masqué ou affiché.|
|[CFrameWnd :: SetMenuBarVisibility](#setmenubarvisibility)|Définit le comportement par défaut du menu dans l’application MFC actuelle pour qu’il soit masqué ou visible.|
|[CFrameWnd :: SetMessageText](#setmessagetext)|Définit le texte d’une barre d’état standard.|
|[CFrameWnd :: SetProgressBarPosition](#setprogressbarposition)|Définit la position actuelle pour la barre de progression Windows 7 affichée sur la barre des tâches.|
|[CFrameWnd :: SetProgressBarRange](#setprogressbarrange)|Définit la plage de la barre de progression Windows 7 affichée sur la barre des tâches.|
|[CFrameWnd :: SetProgressBarState](#setprogressbarstate)|Définit le type et l’état de l’indicateur de progression affiché sur un bouton de la barre des tâches.|
|[CFrameWnd :: SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Surchargé. Applique une superposition à un bouton de la barre des tâches pour indiquer l’état de l’application ou une notification à l’utilisateur.|
|[CFrameWnd :: SetTitle](#settitle)|Définit le titre de la barre de contrôle associée.|
|[CFrameWnd :: ShowControlBar](#showcontrolbar)|Appelez pour afficher la barre de contrôle.|
|[CFrameWnd :: ShowOwnedWindows](#showownedwindows)|Affiche toutes les fenêtres qui sont des descendants de l' `CFrameWnd` objet.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CFrameWnd :: OnCreateClient](#oncreateclient)|Crée une fenêtre cliente pour le frame.|
|[CFrameWnd :: OnHideMenuBar](#onhidemenubar)|Appelé avant que le menu de l’application MFC actuelle soit masqué.|
|[CFrameWnd :: OnShowMenuBar](#onshowmenubar)|Appelé avant l’affichage du menu dans l’application MFC actuelle.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFrameWnd :: m_bAutoMenuEnable](#m_bautomenuenable)|Contrôle la fonctionnalité d’activation et de désactivation automatique pour les éléments de menu.|
|[CFrameWnd :: rectDefault](#rectdefault)|Transmettez cette `CRect` valeur statique en tant que paramètre lors de la création d’un `CFrameWnd` objet pour permettre aux fenêtres de choisir la taille et la position initiales de la fenêtre.|

## <a name="remarks"></a>Notes

Pour créer une fenêtre frame utile pour votre application, dérivez une classe de `CFrameWnd` . Ajoutez des variables membres à la classe dérivée pour stocker des données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Il existe trois façons de construire une fenêtre frame :

- Construisez-le directement à l’aide de [Create](#create).

- Construisez-le directement à l’aide de [LoadFrame](#loadframe).

- Créez-le indirectement à l’aide d’un modèle de document.

Avant `Create` d’appeler ou `LoadFrame` , vous devez construire l’objet de fenêtre frame sur le tas à l’aide de l’opérateur C++ **`new`** . Avant d’appeler `Create` , vous pouvez également inscrire une classe de fenêtre à l’aide de la fonction globale [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) pour définir les styles de l’icône et de la classe du frame.

Utilisez la `Create` fonction membre pour passer les paramètres de création du frame comme arguments immédiats.

`LoadFrame` requiert moins d’arguments que `Create` et récupère à la place la plupart de ses valeurs par défaut des ressources, y compris la légende, l’icône, la table d’accélérateur et le menu du frame. Pour être accessible par `LoadFrame` , toutes ces ressources doivent avoir le même ID de ressource (par exemple, IDR_MAINFRAME).

Lorsqu’un `CFrameWnd` objet contient des vues et des documents, ceux-ci sont créés indirectement par le Framework plutôt que directement par le programmeur. L' `CDocTemplate` objet orchestre la création du frame, la création des vues conteneur et la connexion des vues au document approprié. Les paramètres du `CDocTemplate` constructeur spécifient le `CRuntimeClass` des trois classes impliquées (document, Frame et vue). Un `CRuntimeClass` objet est utilisé par l’infrastructure pour créer dynamiquement des frames lorsqu’ils sont spécifiés par l’utilisateur (par exemple, à l’aide de la commande fichier nouveau ou de la fenêtre interface multidocument (MDI) nouvelle commande).

Une classe de fenêtre frame dérivée de `CFrameWnd` doit être déclarée avec DECLARE_DYNCREATE pour que le mécanisme de RUNTIME_CLASS ci-dessus fonctionne correctement.

Un `CFrameWnd` contient des implémentations par défaut pour exécuter les fonctions suivantes d’une fenêtre principale dans une application classique pour Windows :

- Une `CFrameWnd` fenêtre frame effectue le suivi d’une vue actuellement active qui est indépendante de la fenêtre active de Windows ou du focus d’entrée actuel. Lorsque le frame est réactivé, la vue active est notifiée en appelant `CView::OnActivateView` .

- Les messages de commande et de nombreux messages de notification de frame courants, y compris ceux qui sont gérés par les `OnSetFocus` `OnHScroll` fonctions, et `OnVScroll` de `CWnd` , sont délégués par une `CFrameWnd` fenêtre frame à la vue actuellement active.

- La vue actuellement active (ou la fenêtre frame enfant MDI active dans le cas d’un frame MDI) peut déterminer la légende de la fenêtre frame. Cette fonctionnalité peut être désactivée en désactivant le bit de style FWS_ADDTOTITLE de la fenêtre frame.

- Une `CFrameWnd` fenêtre frame gère le positionnement des barres de contrôles, des vues et d’autres fenêtres enfants dans la zone cliente de la fenêtre frame. Une fenêtre frame effectue également une mise à jour du temps d’inactivité de la barre d’outils et d’autres boutons de la barre de contrôle. Une `CFrameWnd` fenêtre frame possède également des implémentations par défaut de commandes pour activer et désactiver la barre d’outils et la barre d’État.

- Une `CFrameWnd` fenêtre frame gère la barre de menus principale. Lorsqu’un menu contextuel s’affiche, la fenêtre frame utilise le mécanisme UPDATE_COMMAND_UI pour déterminer les éléments de menu qui doivent être activés, désactivés ou activés. Lorsque l’utilisateur sélectionne un élément de menu, la fenêtre frame met à jour la barre d’État avec la chaîne de message de cette commande.

- Une `CFrameWnd` fenêtre frame a une table d’accélérateurs facultative qui convertit automatiquement les accélérateurs clavier.

- Une `CFrameWnd` fenêtre frame a un ID d’aide facultatif défini avec `LoadFrame` qui est utilisé pour l’aide contextuelle. Une fenêtre frame est l’orchestrateur principal d’États semimodal tels que l’aide contextuelle (MAJ + F1) et les modes d’aperçu avant impression.

- Une `CFrameWnd` fenêtre frame ouvre un fichier déplacé à partir du gestionnaire de fichiers et déposé dans la fenêtre frame. Si une extension de fichier est enregistrée et associée à l’application, la fenêtre frame répond à la demande d’ouverture DDE (Dynamic Data Exchange) qui se produit lorsque l’utilisateur ouvre un fichier de données dans le gestionnaire de fichiers ou lorsque la `ShellExecute` fonction Windows est appelée.

- Si la fenêtre frame est la fenêtre d’application principale (autrement dit, `CWinThread::m_pMainWnd` ), lorsque l’utilisateur ferme l’application, la fenêtre frame invite l’utilisateur à enregistrer tous les documents modifiés (pour `OnClose` et `OnQueryEndSession` ).

- Si la fenêtre frame est la fenêtre d’application principale, la fenêtre frame est le contexte pour l’exécution de WinHelp. La fermeture de la fenêtre frame s’arrête WINHELP.EXE si elle a été lancée pour obtenir de l’aide pour cette application.

N’utilisez pas l' **`delete`** opérateur C++ pour détruire une fenêtre frame. Utilisez `CWnd::DestroyWindow` à la place. L' `CFrameWnd` implémentation de `PostNcDestroy` supprimera l’objet C++ lorsque la fenêtre sera détruite. Lorsque l’utilisateur ferme la fenêtre frame, le gestionnaire par défaut `OnClose` appellera `DestroyWindow` .

Pour plus d’informations sur `CFrameWnd` , consultez [fenêtres Frame](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a> CFrameWnd :: ActivateFrame

Appelez cette fonction membre pour activer et restaurer la fenêtre frame afin qu’elle soit visible et accessible à l’utilisateur.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Paramètres

*nCmdShow*<br/>
Spécifie le paramètre à passer à [CWnd :: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Par défaut, le frame est affiché et correctement restauré.

### <a name="remarks"></a>Notes

Cette fonction membre est généralement appelée après un événement d’interface non utilisateur, tel qu’un événement DDE, OLE ou autre, qui peut afficher la fenêtre frame ou son contenu à l’utilisateur.

L’implémentation par défaut active le frame et l’affiche en haut de l’ordre de plan et, si nécessaire, effectue les mêmes étapes pour la fenêtre frame principale de l’application.

Substituez cette fonction membre pour modifier la façon dont un frame est activé. Par exemple, vous pouvez forcer les fenêtres enfants MDI à être agrandies. Ajoutez la fonctionnalité appropriée, puis appelez la version de la classe de base avec un *nCmdShow*explicite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a> CFrameWnd :: BeginModalState

Appelez cette fonction membre pour rendre modale une fenêtre frame.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a> CFrameWnd :: CFrameWnd

Construit un `CFrameWnd` objet, mais ne crée pas la fenêtre frame visible.

```
CFrameWnd();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer la fenêtre visible.

## <a name="cframewndcreate"></a><a name="create"></a> CFrameWnd :: Create

Appelez pour créer et initialiser la fenêtre frame Windows associée à l' `CFrameWnd` objet.

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

*lpszClassName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui nomme la classe Windows. Le nom de la classe peut être n’importe quel nom enregistré avec la `AfxRegisterWndClass` fonction globale ou la `RegisterClass` fonction Windows. Si la valeur est NULL, utilise les attributs par défaut prédéfinis `CFrameWnd` .

*lpszWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui représente le nom de la fenêtre. Utilisé comme texte pour la barre de titre.

*dwStyle*<br/>
Spécifie les attributs de [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) de fenêtre. Incluez le style de FWS_ADDTOTITLE si vous souhaitez que la barre de titre affiche automatiquement le nom du document représenté dans la fenêtre.

*rectangulaire*<br/>
Spécifie la taille et la position de la fenêtre. La valeur *rectDefault* permet à Windows de spécifier la taille et la position de la nouvelle fenêtre.

*pParentWnd*<br/>
Spécifie la fenêtre parente de cette fenêtre frame. Ce paramètre doit avoir la valeur NULL pour les fenêtres frame de niveau supérieur.

*lpszMenuName*<br/>
Identifie le nom de la ressource de menu à utiliser avec la fenêtre. Utilisez MAKEINTRESOURCE si le menu a un ID d’entier au lieu d’une chaîne. Ce paramètre peut avoir la valeur NULL.

*dwExStyle*<br/>
Spécifie les attributs de [style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) étendu de la fenêtre.

*pContext*<br/>
Spécifie un pointeur vers une structure [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ce paramètre peut avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’initialisation réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Construisez un `CFrameWnd` objet en deux étapes. Tout d’abord, appelez le constructeur, qui construit l' `CFrameWnd` objet, puis appelle `Create` , qui crée la fenêtre frame Windows et l’attache à l' `CFrameWnd` objet. `Create` Initialise le nom de la classe et le nom de la fenêtre de la fenêtre et enregistre les valeurs par défaut pour son style, son parent et son menu associé.

Utilisez `LoadFrame` plutôt que de `Create` charger la fenêtre frame à partir d’une ressource au lieu de spécifier ses arguments.

## <a name="cframewndcreateview"></a><a name="createview"></a> CFrameWnd :: CreateView

Appelez `CreateView` pour créer une vue dans un frame.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Spécifie le type de vue et de document.

*nID*<br/>
Numéro d’identification d’une vue.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CWnd` objet en cas de réussite ; sinon, null.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre pour créer des « vues » qui ne sont pas `CView` dérivées dans un frame. Après avoir appelé `CreateView` , vous devez définir manuellement la vue sur active et la définir pour qu’elle soit visible ; ces tâches ne sont pas exécutées automatiquement par `CreateView` .

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a> CFrameWnd ::D ockControlBar

Entraîne l’ancrage d’une barre de contrôle à la fenêtre frame.

```cpp
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
Pointe vers la barre de contrôle à ancrer.

*nDockBarID*<br/>
Détermine les côtés de la fenêtre frame à prendre en compte pour l’ancrage. Il peut être égal à 0 ou à un ou plusieurs des éléments suivants :

- AFX_IDW_DOCKBAR_TOP ancrer sur le côté supérieur de la fenêtre frame.

- AFX_IDW_DOCKBAR_BOTTOM ancrer sur le côté inférieur de la fenêtre frame.

- AFX_IDW_DOCKBAR_LEFT ancrer sur le côté gauche de la fenêtre frame.

- AFX_IDW_DOCKBAR_RIGHT ancrer sur le côté droit de la fenêtre frame.

Si la valeur est égale à 0, la barre de contrôle peut être ancrée à n’importe quel côté activé pour l’ancrage dans la fenêtre frame de destination.

*lpRect*<br/>
Détermine, en coordonnées d’écran, où la barre de contrôle sera ancrée dans la zone non cliente de la fenêtre frame de destination.

### <a name="remarks"></a>Notes

La barre de contrôle sera ancrée à l’un des côtés de la fenêtre frame spécifiée dans les appels à [CControlBar :: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) et [CFrameWnd :: EnableDocking](#enabledocking). Le côté choisi est déterminé par *nDockBarID*.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a> CFrameWnd :: EnableDocking

Appelez cette fonction pour activer les barres de contrôle ancrables dans une fenêtre frame.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

*dwDockStyle*<br/>
Spécifie les côtés de la fenêtre frame qui peuvent servir de sites d’ancrage pour les barres de contrôles. Il peut s’agir d’un ou plusieurs des éléments suivants :

- CBRS_ALIGN_TOP permet l’ancrage en haut de la zone cliente.

- CBRS_ALIGN_BOTTOM permet l’ancrage en bas de la zone cliente.

- CBRS_ALIGN_LEFT autorise l’ancrage sur le côté gauche de la zone cliente.

- CBRS_ALIGN_RIGHT autorise l’ancrage sur le côté droit de la zone cliente.

- CBRS_ALIGN_ANY autorise l’ancrage de n’importe quel côté de la zone cliente.

### <a name="remarks"></a>Notes

Par défaut, les barres de contrôle sont ancrées à un côté de la fenêtre frame dans l’ordre suivant : haut, bas, gauche, droite.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CToolBar :: Create](../../mfc/reference/ctoolbar-class.md#create).

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a> CFrameWnd :: EndModalState

Appelez cette fonction membre pour changer une fenêtre frame modale en fenêtre frame non modale.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Notes

`EndModalState` Active toutes les fenêtres désactivées par [BeginModalState](#beginmodalstate).

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a> CFrameWnd :: FloatControlBar

Appelez cette fonction pour empêcher l’ancrage d’une barre de contrôle à la fenêtre frame.

```cpp
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
Pointe vers la barre de contrôle à flotter.

*point*<br/>
Emplacement, en coordonnées d’écran, où l’angle supérieur gauche de la barre de contrôle sera placé.

*dwStyle*<br/>
Spécifie s’il faut aligner la barre de contrôle horizontalement ou verticalement dans sa nouvelle fenêtre frame. Il peut s’agir de l’un des éléments suivants :

- CBRS_ALIGN_TOP oriente la barre de contrôle verticalement.

- CBRS_ALIGN_BOTTOM oriente la barre de contrôle verticalement.

- CBRS_ALIGN_LEFT oriente la barre de contrôle horizontalement.

- CBRS_ALIGN_RIGHT oriente la barre de contrôle horizontalement.

Si les styles sont passés en spécifiant à la fois l’orientation horizontale et la position verticale, la barre d’outils est orientée horizontalement.

### <a name="remarks"></a>Notes

En règle générale, cette opération est effectuée au démarrage de l’application lorsque le programme restaure les paramètres de l’exécution précédente.

Cette fonction est appelée par l’infrastructure quand l’utilisateur provoque une opération de déplacement en relâchant le bouton gauche de la souris tout en faisant glisser la barre de contrôle sur un emplacement qui n’est pas disponible pour l’ancrage.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a> CFrameWnd :: GetActiveDocument

Appelez cette fonction membre pour obtenir un pointeur vers le actuel `CDocument` attaché à la vue active actuelle.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le [CDocument](../../mfc/reference/cdocument-class.md)actuel. S’il n’y a aucun document actif, retourne la valeur NULL.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a> CFrameWnd :: GetActiveFrame

Appelez cette fonction membre pour obtenir un pointeur vers la fenêtre enfant MDI (multiple document interface) active d’une fenêtre frame MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre enfant MDI active. Si l’application est une application SDI ou si la fenêtre frame MDI n’a aucun document actif, le pointeur implicite est **`this`** retourné.

### <a name="remarks"></a>Notes

S’il n’existe aucun enfant MDI actif ou si l’application est une interface SDI (single document interface), le pointeur implicite **`this`** est retourné.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a> CFrameWnd :: GetActiveView

Appelez cette fonction membre pour obtenir un pointeur vers la vue active (le cas échéant) attachée à une fenêtre frame ( `CFrameWnd` ).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le [CView](../../mfc/reference/cview-class.md)actuel. S’il n’existe pas d’affichage actuel, retourne la valeur NULL.

### <a name="remarks"></a>Notes

Cette fonction retourne la valeur NULL lorsqu’elle est appelée pour une fenêtre frame principale MDI ( `CMDIFrameWnd` ). Dans une application MDI, la fenêtre frame principale MDI n’est associée à aucune vue. Au lieu de cela, chaque fenêtre enfant individuelle ( `CMDIChildWnd` ) possède une ou plusieurs vues associées. L’affichage actif dans une application MDI peut être obtenu en recherchant d’abord la fenêtre enfant MDI active, puis en recherchant la vue active de cette fenêtre enfant. La fenêtre enfant MDI active est accessible en appelant la fonction `MDIGetActive` ou `GetActiveFrame` comme illustré dans l’exemple suivant :

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a> CFrameWnd :: GetControlBar

Appelez `GetControlBar` pour accéder à la barre de contrôle associée à l’ID.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Numéro d’identification d’une barre de contrôle.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la barre de contrôle associée à l’ID.

### <a name="remarks"></a>Notes

Le paramètre *nid* fait référence à l’identificateur unique passé à la `Create` méthode de la barre de contrôle. Pour plus d’informations sur les barres de contrôles, reportez-vous à la rubrique intitulée [barres de contrôles](../../mfc/control-bars.md).

`GetControlBar` retourne la barre de contrôle même si elle est flottante et, par conséquent, n’est pas une fenêtre enfant du frame.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a> CFrameWnd :: GetDockState

Appelez cette fonction membre pour stocker des informations d’État sur les barres de contrôle de la fenêtre frame dans un `CDockState` objet.

```cpp
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Contient l’état actuel des barres de contrôles de la fenêtre frame lors du retour.

### <a name="remarks"></a>Notes

Vous pouvez ensuite écrire le contenu de `CDockState` dans le stockage à l’aide de `CDockState::SaveState` ou de `Serialize` . Si, par la suite, vous souhaitez restaurer les barres de contrôle à un état précédent, chargez l’état avec `CDockState::LoadState` ou `Serialize` , puis appelez `SetDockState` pour appliquer l’état précédent aux barres de contrôles de la fenêtre frame.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a> CFrameWnd :: GetMenuBarState

Récupère l’état d’affichage du menu dans l’application MFC actuelle.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour peut avoir les valeurs suivantes :

- AFX_MBS_VISIBLE (0x01)-le menu est visible.

- AFX_MBS_HIDDEN (0x02)-le menu est masqué.

### <a name="remarks"></a>Notes

Si une erreur d’exécution se produit, cette méthode effectue une assertion en mode débogage et lève une exception dérivée de la classe [CException](../../mfc/reference/cexception-class.md) .

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a> CFrameWnd :: GetMenuBarVisibility

Indique si l’État par défaut du menu dans l’application MFC actuelle est masqué ou visible.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Valeur de retour

La méthode retourne l'une des valeurs suivantes :

- AFX_MBV_KEEPVISIBLE (0x01)-le menu s’affiche à tout moment et, par défaut, n’a pas le focus.

- AFX_MBV_DISPLAYONFOCUS (0x02) : le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche ALT pour afficher le menu et lui attribuer le focus. Si le menu s’affiche, appuyez sur la touche ALT ou ÉCHAP pour le masquer.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (combinaison au niveau du bit (ou))-le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche F10 pour afficher le menu et lui attribuer le focus. Si le menu s’affiche, appuyez sur la touche F10 pour activer ou désactiver le menu. Le menu s’affiche jusqu’à ce que vous appuyiez sur la touche ALT ou ÉCHAP pour le masquer.

### <a name="remarks"></a>Notes

Si une erreur d’exécution se produit, cette méthode effectue une assertion en mode débogage et lève une exception dérivée de la classe [CException](../../mfc/reference/cexception-class.md) .

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a> CFrameWnd :: GetMessageBar

Appelez cette fonction membre pour obtenir un pointeur vers la barre d’État.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Valeur de retour

Pointeur désignant la fenêtre de la barre d’État.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a> CFrameWnd :: GetMessageString

Substituez cette fonction pour fournir des chaînes personnalisées pour les ID de commande.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID de ressource du message souhaité.

*rMessage*<br/>
`CString` objet dans lequel placer le message.

### <a name="remarks"></a>Notes

L’implémentation par défaut charge simplement la chaîne spécifiée par *nid* à partir du fichier de ressources. Cette fonction est appelée par l’infrastructure lorsque la chaîne de message de la barre d’État doit être mise à jour.

## <a name="cframewndgettitle"></a><a name="gettitle"></a> CFrameWnd :: GetTitle

Récupère le titre de l’objet Window.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le titre actuel de l’objet Window.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a> CFrameWnd :: InitialUpdateFrame

Appelez `IntitialUpdateFrame` après avoir créé un nouveau Frame avec `Create` .

```cpp
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Paramètres

*pDoc*<br/>
Pointe vers le document auquel la fenêtre frame est associée. Sa valeur peut être NULL.

*bMakeVisible*<br/>
Si la valeur est TRUE, indique que le frame doit devenir visible et actif. Si la valeur est FALSe, aucun descendant n’est rendu visible.

### <a name="remarks"></a>Notes

Toutes les vues de cette fenêtre frame reçoivent alors leurs `OnInitialUpdate` appels.

En outre, s’il n’y avait pas précédemment une vue active, la vue principale de la fenêtre frame est rendue active. La vue principale est une vue avec un ID enfant de AFX_IDW_PANE_FIRST. Enfin, la fenêtre frame est rendue visible si *bMakeVisible* est différent de zéro. Si *bMakeVisible* a la valeur 0, le focus actuel et l’état visible de la fenêtre frame restent inchangés. Il n’est pas nécessaire d’appeler cette fonction lors de l’utilisation de l’implémentation du fichier New et du fichier ouvert de l’infrastructure.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a> CFrameWnd :: InModalState

Appelez cette fonction membre pour vérifier si une fenêtre frame est modale ou non modale.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si oui ; Sinon, 0.

## <a name="cframewndistracking"></a><a name="istracking"></a> CFrameWnd :: IsTracking

Appelez cette fonction membre pour déterminer si la barre de fractionnement dans la fenêtre est en cours de déplacement.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si une opération de fractionnement est en cours ; Sinon, 0.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a> CFrameWnd :: LoadAccelTable

Appelez pour charger la table d’accélérateurs spécifiée.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Identifie le nom de la ressource d’accélérateur. Utilisez MAKEINTRESOURCE si la ressource est identifiée par un ID d’entier.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la table d’accélérateurs a été chargée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Une seule table peut être chargée à la fois.

Les tables d’accélérateurs chargées à partir des ressources sont automatiquement libérées lorsque l’application se termine.

Si vous appelez `LoadFrame` pour créer la fenêtre frame, le Framework charge une table d’accélérateurs avec les ressources de menu et d’icône, et un appel ultérieur à cette fonction membre est alors inutile.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a> CFrameWnd :: LoadBarState

Appelez cette fonction pour restaurer les paramètres de chaque barre de contrôles appartenant à la fenêtre frame.

```cpp
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Nom d’une section dans le fichier d’initialisation (INI) ou clé dans le Registre Windows où les informations d’État sont stockées.

### <a name="remarks"></a>Notes

Les informations restaurées incluent la visibilité, l’orientation horizontale/verticale, l’état d’ancrage et la position de la barre de contrôle.

Les paramètres que vous souhaitez restaurer doivent être écrits dans le registre avant d’appeler `LoadBarState` . Écrivez les informations dans le registre en appelant [CWinApp :: SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Écrivez les informations dans le fichier INI en appelant [SaveBarState](#savebarstate).

## <a name="cframewndloadframe"></a><a name="loadframe"></a> CFrameWnd :: LoadFrame

Appelez pour créer dynamiquement une fenêtre frame à partir d’informations sur les ressources.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*nIDResource*<br/>
ID des ressources partagées associées à la fenêtre frame.

*dwDefaultStyle*<br/>
[Style](../../mfc/reference/styles-used-by-mfc.md#window-styles)du frame. Incluez le style de FWS_ADDTOTITLE si vous souhaitez que la barre de titre affiche automatiquement le nom du document représenté dans la fenêtre.

*pParentWnd*<br/>
Pointeur vers le parent du frame.

*pContext*<br/>
Pointeur vers une structure [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ce paramètre peut avoir la valeur NULL.

### <a name="remarks"></a>Notes

Construisez un `CFrameWnd` objet en deux étapes. Tout d’abord, appelez le constructeur, qui construit l' `CFrameWnd` objet, puis appelle `LoadFrame` , qui charge la fenêtre frame Windows et les ressources associées et attache la fenêtre frame à l' `CFrameWnd` objet. Le paramètre *nIDResource* spécifie le menu, la table d’accélérateurs, l’icône et la ressource de type chaîne du titre de la fenêtre frame.

Utilisez la `Create` fonction membre plutôt que `LoadFrame` lorsque vous souhaitez spécifier tous les paramètres de création de la fenêtre frame.

Le Framework appelle `LoadFrame` lorsqu’il crée une fenêtre frame à l’aide d’un objet modèle de document.

L’infrastructure utilise l’argument *pContext* pour spécifier les objets à connecter à la fenêtre frame, y compris tous les objets de vue contenus. Vous pouvez affecter la valeur NULL à l’argument *pContext* lorsque vous appelez `LoadFrame` .

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a> CFrameWnd :: m_bAutoMenuEnable

Lorsque ce membre de données est activé (valeur par défaut), les éléments de menu qui n’ont pas de gestionnaires ON_UPDATE_COMMAND_UI ou ON_COMMAND sont automatiquement désactivés lorsque l’utilisateur extrait un menu.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Notes

Éléments de menu qui ont un gestionnaire de ON_COMMAND mais aucun gestionnaire de ON_UPDATE_COMMAND_UI n’est automatiquement activé.

Lorsque ce membre de données est défini, les éléments de menu sont automatiquement activés de la même façon que les boutons de la barre d’outils.

> [!NOTE]
> `m_bAutoMenuEnable` n’a aucun effet sur les éléments de menu de niveau supérieur.

Ce membre de données simplifie l’implémentation des commandes facultatives en fonction de la sélection actuelle et réduit la nécessité d’écrire des gestionnaires ON_UPDATE_COMMAND_UI pour l’activation et la désactivation des éléments de menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a> CFrameWnd :: NegotiateBorderSpace

Appelez cette fonction membre pour négocier l’espace de bordure dans une fenêtre frame pendant l’activation d’OLE InPlace.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Paramètres

*nBorderCmd*<br/>
Contient l’une des valeurs suivantes à partir de `enum BorderCmd` :

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie les coordonnées de la bordure.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est l' `CFrameWnd` implémentation de la négociation de l’espace de bordure OLE.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a> CFrameWnd :: OnBarCheck

Appelé chaque fois qu’une action est exécutée sur la barre de contrôle spécifiée.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID de la barre de contrôle affichée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre de contrôle existait ; Sinon, 0.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a> CFrameWnd :: OnContextHelp

Gère l’aide de MAJ + F1 pour les éléments sur place.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Notes

Pour activer l’aide contextuelle, vous devez ajouter un

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

dans votre table `CFrameWnd` des messages de classe et ajoutez également une entrée de table d’accélérateurs, en général Shift + F1, pour activer cette fonction membre.

Si votre application est un conteneur OLE, `OnContextHelp` place tous les éléments sur place contenus dans l’objet de fenêtre frame en mode d’aide. Le curseur se transforme en flèche et en point d’interrogation, et l’utilisateur peut déplacer le pointeur de la souris et appuyer sur le bouton gauche de la souris pour sélectionner une boîte de dialogue, une fenêtre, un menu ou un bouton de commande. Cette fonction membre appelle la fonction Windows `WinHelp` avec le contexte d’aide de l’objet situé sous le curseur.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a> CFrameWnd :: OnCreateClient

Appelé par le Framework pendant l’exécution de `OnCreate` .

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Paramètres

*lpcs*<br/>
Pointeur vers une structure Windows [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) .

*pContext*<br/>
Pointeur vers une structure [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

N’appelez jamais cette fonction.

L’implémentation par défaut de cette fonction crée un `CView` objet à partir des informations fournies dans *pContext*, si possible.

Substituez cette fonction pour substituer les valeurs passées dans l' `CCreateContext` objet ou pour modifier la façon dont les contrôles dans la zone cliente principale de la fenêtre frame sont créés. Les `CCreateContext` membres que vous pouvez substituer sont décrits dans la classe [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

> [!NOTE]
> Ne remplacez pas les valeurs passées dans la `CREATESTRUCT` structure. Ils sont destinés à un usage informatif uniquement. Si vous souhaitez substituer le rectangle de fenêtre initial, par exemple, remplacez la `CWnd` fonction membre [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a> CFrameWnd :: OnHideMenuBar

Cette fonction est appelée lorsque le système est sur le paragraphe de masquer la barre de menus dans l’application MFC actuelle.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Notes

Ce gestionnaire d’événements permet à votre application d’effectuer des actions personnalisées lorsque le système est sur le paragraphe de masquer le menu. Vous ne pouvez pas empêcher le menu d’être masqué, mais vous pouvez, par exemple, appeler d’autres méthodes pour récupérer le style de menu ou l’État.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a> CFrameWnd :: OnSetPreviewMode

Appelez cette fonction membre pour définir la fenêtre frame principale de l’application dans et en dehors du mode Aperçu avant impression.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Paramètres

*bPreview*<br/>
Spécifie s’il faut ou non placer l’application en mode aperçu avant impression. Définir sur TRUE pour passer en mode aperçu avant impression, FALSe pour annuler le mode aperçu.

*pState*<br/>
Pointeur vers une `CPrintPreviewState` structure.

### <a name="remarks"></a>Notes

L’implémentation par défaut désactive toutes les barres d’outils standard et masque le menu principal et la fenêtre cliente principale. Cela permet de transformer les fenêtres frame MDI en fenêtres frames SDI temporaires.

Substituez cette fonction membre pour personnaliser le masquage et l’affichage des barres de contrôles et d’autres parties de fenêtre frame pendant l’aperçu avant impression. Appelez l’implémentation de la classe de base à partir de la version substituée.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a> CFrameWnd :: OnShowMenuBar

Cette fonction est appelée lorsque le système est sur le présent d’afficher la barre de menus dans l’application MFC actuelle.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Notes

Ce gestionnaire d’événements permet à votre application d’effectuer des actions personnalisées lorsque le menu est sur le présent affiché. Vous ne pouvez pas empêcher l’affichage du menu, mais vous pouvez, par exemple, appeler d’autres méthodes pour récupérer le style de menu ou l’État.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a> CFrameWnd :: OnUpdateControlBarMenu

Appelé par le Framework lorsque le menu associé est mis à jour.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) représentant le menu qui a généré la commande de mise à jour. Le gestionnaire de mise à jour appelle la fonction membre [Enable](../../mfc/reference/ccmdui-class.md#enable) de l' `CCmdUI` objet par le biais de *pCmdUI* pour mettre à jour l’interface utilisateur.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a> CFrameWnd :: RecalcLayout

Appelé par le Framework lorsque les barres de contrôles standard sont activées ou désactivées ou lorsque la fenêtre frame est redimensionnée.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

*bNotify*<br/>
Détermine si l’élément sur place actif pour la fenêtre frame reçoit une notification de la modification de la disposition. Si la valeur est TRUE, l’élément est notifié ; Sinon, FALSe.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction membre appelle la `CWnd` fonction membre `RepositionBars` pour repositionner toutes les barres de contrôle dans le frame et dans la fenêtre cliente principale (généralement a `CView` ou MdiClient).

Substituez cette fonction membre pour contrôler l’apparence et le comportement des barres de contrôle après la modification de la disposition de la fenêtre frame. Par exemple, appelez-le quand vous activez ou désactivez les barres de contrôle ou ajoutez une autre barre de contrôle.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a> CFrameWnd :: rectDefault

Transmettez cette `CRect` valeur statique en tant que paramètre lors de la création d’une fenêtre pour permettre aux fenêtres de choisir la taille et la position initiales de la fenêtre.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a> CFrameWnd :: SaveBarState

Appelez cette fonction pour stocker des informations sur chaque barre de contrôles appartenant à la fenêtre frame.

```cpp
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Nom d’une section dans le fichier d’initialisation ou clé dans le Registre Windows où les informations d’État sont stockées.

### <a name="remarks"></a>Notes

Ces informations peuvent être lues à partir du fichier d’initialisation à l’aide de [LoadBarState](#loadbarstate). Les informations stockées incluent la visibilité, l’orientation horizontale/verticale, l’état de l’ancrage et la position de la barre de contrôle.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a> CFrameWnd :: SetActivePreviewView

Désigne la vue spécifiée comme étant la vue active de la version préliminaire complète.

```cpp
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Paramètres

*pViewNew*<br/>
Pointeur vers une vue à activer.

### <a name="remarks"></a>Notes

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a> CFrameWnd :: SetActiveView

Appelez cette fonction membre pour définir la vue active.

```cpp
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

*pViewNew*<br/>
Spécifie un pointeur vers un objet [CView](../../mfc/reference/cview-class.md) , ou null pour aucune vue active.

*bNotify*<br/>
Spécifie si la vue doit être notifiée de l’activation. Si la valeur `OnActivateView` est true, est appelé pour la nouvelle vue ; si la valeur est false, ce n’est pas le cas.

### <a name="remarks"></a>Notes

L’infrastructure appellera cette fonction automatiquement lorsque l’utilisateur change le focus en vue dans la fenêtre frame. Vous pouvez appeler explicitement `SetActiveView` pour définir le focus sur la vue spécifiée.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a> CFrameWnd :: SetDockState

Appelez cette fonction membre pour appliquer les informations d’État stockées dans un `CDockState` objet aux barres de contrôles de la fenêtre frame.

```cpp
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Appliquez l’État stocké aux barres de contrôles de la fenêtre frame.

### <a name="remarks"></a>Notes

Pour restaurer un état précédent des barres de contrôles, vous pouvez charger l’État stocké avec `CDockState::LoadState` ou `Serialize` , puis utiliser `SetDockState` pour l’appliquer aux barres de contrôles de la fenêtre frame. L’état précédent est stocké dans l' `CDockState` objet avec `GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a> CFrameWnd :: SetMenuBarState

Définit l’état d’affichage du menu dans l’application MFC actuelle sur masqué ou affiché.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Paramètres

*nState*\
dans Spécifie s’il faut afficher ou masquer le menu. Le paramètre *nState* peut avoir les valeurs suivantes :

- `AFX_MBS_VISIBLE` (0x01) : affiche le menu s’il est masqué, mais n’a aucun effet s’il est visible.
- `AFX_MBS_HIDDEN` (0x02) : masque le menu s’il est visible, mais n’a aucun effet s’il est masqué.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode modifie correctement l’état du menu ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si une erreur d’exécution se produit, cette méthode effectue une assertion en mode débogage et lève une exception dérivée de la classe [CException](../../mfc/reference/cexception-class.md) .

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a> CFrameWnd :: SetMenuBarVisibility

Définit le comportement par défaut du menu dans l’application MFC actuelle pour qu’il soit masqué ou visible.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*\
dans Spécifie si le menu est masqué par défaut, ou s’il est visible et a le focus. Le paramètre *nStyle* peut avoir les valeurs suivantes :

- `AFX_MBV_KEEPVISIBLE` (0x01)-le menu s’affiche à tout moment et, par défaut, n’a pas le focus.

- `AFX_MBV_DISPLAYONFOCUS` (0x02)-le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche ALT pour afficher le menu et lui attribuer le focus. Si le menu s’affiche, appuyez sur la touche ALT ou ÉCHAP pour masquer le menu.

- `AFX_MBV_DISPLAYONFOCUS` (0x02) &#124; `AFX_MBV_DISPLAYONF10` (0x04) (combinaison de bits (or))-le menu est masqué par défaut. Si le menu est masqué, appuyez sur la touche F10 pour afficher le menu et lui attribuer le focus. Si le menu s’affiche, appuyez sur la touche F10 pour activer ou désactiver le menu. Le menu s’affiche jusqu’à ce que vous appuyiez sur la touche ALT ou ÉCHAP pour le masquer.

### <a name="remarks"></a>Notes

Si la valeur du paramètre *nStyle* n’est pas valide, cette méthode déclare en mode débogage et déclenche [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en mode release. En cas d’autres erreurs d’exécution, cette méthode déclare en mode débogage et lève une exception dérivée de la classe [CException](../../mfc/reference/cexception-class.md) .

Cette méthode affecte l’état des menus dans les applications écrites pour Windows Vista et versions ultérieures.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a> CFrameWnd :: SetMessageText

Appelez cette fonction pour placer une chaîne dans le volet de la barre d’État dont l’ID est égal à 0.

```cpp
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Pointe vers la chaîne à placer dans la barre d’État.

*nID*<br/>
ID de ressource de chaîne de la chaîne à placer dans la barre d’État.

### <a name="remarks"></a>Notes

Il s’agit généralement du volet le plus à gauche et le plus long de la barre d’État.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a> CFrameWnd :: SetProgressBarPosition

Définit la position actuelle de la barre de progression Windows 7 affichée sur la barre des tâches.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Paramètres

*nProgressPos*<br/>
Spécifie la position à définir. Elle doit être comprise dans la plage définie par `SetProgressBarRange` .

### <a name="remarks"></a>Notes

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a> CFrameWnd :: SetProgressBarRange

Définit la plage de la barre de progression Windows 7 affichée sur la barre des tâches.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Paramètres

*nRangeMin*<br/>
Valeur minimale.

*nRangeMax*<br/>
Valeur maximale.

### <a name="remarks"></a>Notes

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a> CFrameWnd :: SetProgressBarState

Définit le type et l’état de l’indicateur de progression affiché sur un bouton de la barre des tâches.

```cpp
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Paramètres

*tbpFlags*<br/>
Indicateurs qui contrôlent l’état actuel du bouton de progression. Spécifiez un seul des indicateurs suivants, car tous les États sont mutuellement exclusifs : TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Notes

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a> CFrameWnd :: SetTaskbarOverlayIcon

Surchargé. Applique une superposition à un bouton de la barre des tâches pour indiquer l’état de l’application ou pour notifier l’utilisateur.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Paramètres

*nIDResource*<br/>
Spécifie l’ID de ressource d’une icône à utiliser comme superposition. Pour plus d’informations, consultez la description de *HICON* .

*lpcszDescr*<br/>
Pointeur vers une chaîne qui fournit une version texte de remplacement des informations communiquées par la superposition, à des fins d’accessibilité.

*hIcon*<br/>
Handle d’une icône à utiliser comme superposition. Il doit s’agir d’une petite icône, mesurant 16x16 pixels à 96 points par pouce (dpi). Si une icône de superposition est déjà appliquée au bouton de la barre des tâches, cette superposition existante est remplacée. Cette valeur peut être NULL. La façon dont une valeur NULL est gérée varie selon que le bouton de la barre des tâches représente une fenêtre unique ou un groupe de fenêtres. Il incombe à l’application appelante de libérer *HICON* lorsqu’elle n’est plus nécessaire.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite ; FALSe si la version du système d’exploitation est inférieure à Windows 7 ou si une erreur se produit lors de la définition de l’icône.

### <a name="remarks"></a>Notes

## <a name="cframewndsettitle"></a><a name="settitle"></a> CFrameWnd :: SetTitle

Définit le titre de l’objet Window.

```cpp
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Paramètres

*lpszTitle*<br/>
Pointeur vers une chaîne de caractères contenant le titre de l’objet Window.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a> CFrameWnd :: ShowControlBar

Appelez cette fonction membre pour afficher ou masquer la barre de contrôle.

```cpp
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
Pointeur vers la barre de contrôle à afficher ou à masquer.

*bShow*<br/>
Si la valeur est TRUE, spécifie que la barre de contrôle doit être affichée. Si la valeur est FALSe, spécifie que la barre de contrôle doit être masquée.

*bDelay*<br/>
Si la valeur est TRUE, retarde l’affichage de la barre de contrôle. Si la valeur est FALSe, affiche immédiatement la barre de contrôle.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a> CFrameWnd :: ShowOwnedWindows

Appelez cette fonction membre pour afficher toutes les fenêtres qui sont des descendants de l' `CFrameWnd` objet.

```cpp
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
Spécifie si les fenêtres détenues doivent être affichées ou masquées.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd, classe](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd (classe)](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Structure CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)
