---
title: CMDIChildWnd (classe)
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: efcf5057481345c001cc48224f53c666623d0780
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304988"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd (classe)

Fournit les fonctionnalités d'une fenêtre enfant d'interface multidocument (MDI) Windows, ainsi que des membres permettant de gérer la fenêtre.

## <a name="syntax"></a>Syntaxe

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construit un objet `CMDIChildWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|Crée la fenêtre enfant MDI de Windows associée à la `CMDIChildWnd` objet.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Retourne le parent de frame MDI de la fenêtre du client MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Active cette fenêtre MDI enfant.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Détruit cette fenêtre MDI enfant.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Agrandit cette fenêtre MDI enfant.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaure cette fenêtre MDI enfant à partir de taille réduite ou agrandie.|
|[CMDIChildWnd::SetHandles](#sethandles)|Définit les descripteurs pour les ressources de menu et d’accélérateur.|

## <a name="remarks"></a>Notes

Une fenêtre enfant MDI ressemble beaucoup à une fenêtre frame classique, à ceci près que la fenêtre MDI enfant s’affiche à l’intérieur d’une fenêtre frame MDI plutôt que sur le bureau. Une fenêtre enfant MDI n’a pas d’une barre de menus de son propre, mais au lieu de cela partage le menu de la fenêtre frame MDI. Le framework modifie automatiquement le menu de frame MDI pour représenter la fenêtre enfant MDI active.

Pour créer une fenêtre d’enfant MDI utile pour votre application, dérivez une classe de `CMDIChildWnd`. Ajoutez des variables membres à la classe dérivée pour stocker les données propres à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Il existe trois manières de construire une fenêtre enfant MDI :

- Construire directement à l’aide de `Create`.

- Construire directement à l’aide de `LoadFrame`.

- Construire indirectement via un modèle de document.

Avant d’appeler `Create` ou `LoadFrame`, vous devez construire l’objet de fenêtre frame sur le tas à l’aide de C++ **nouveau** opérateur. Avant d’appeler `Create` vous pouvez également enregistrer une classe de fenêtre avec le [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction globale pour définir les styles d’icône et de classe pour le frame.

Utilisez le `Create` fonction membre pour passer des arguments comme immédiats de paramètres de création de l’image.

`LoadFrame` nécessite moins d’arguments que `Create`et récupère à la place de la plupart de ses valeurs par défaut à partir de ressources, y compris la légende du frame, icône, table d’accélérateurs et menu. Pour être accessible par `LoadFrame`, toutes ces ressources doivent avoir le même ID de ressource (par exemple, IDR_MAINFRAME).

Quand un `CMDIChildWnd` objet contient des vues et des documents, elles sont créées indirectement par le framework au lieu de directement par le programmeur. Le `CDocTemplate` objet orchestre la création de l’image, la création des vues contenants et la connexion des vues au document approprié. Les paramètres de la `CDocTemplate` constructeur spécifie le `CRuntimeClass` des trois classes impliquées (document, le frame et affichage). Un `CRuntimeClass` objet est utilisé par l’infrastructure pour créer dynamiquement des nouvelles images lorsque spécifié par l’utilisateur (par exemple, en utilisant la commande fichier nouveau ou la commande Nouveau de fenêtre MDI).

Une classe de fenêtre frame dérivée de `CMDIChildWnd` doit être déclaré avec DECLARE_DYNCREATE afin que le mécanisme RUNTIME_CLASS ci-dessus fonctionne correctement.

Le `CMDIChildWnd` classe hérite de son implémentation par défaut à partir de `CFrameWnd`. Pour obtenir une liste détaillée de ces fonctionnalités, reportez-vous à la [CFrameWnd](../../mfc/reference/cframewnd-class.md) description de classe. Le `CMDIChildWnd` classe a les fonctionnalités supplémentaires suivantes :

- Conjointement avec le `CMultiDocTemplate` (classe), plusieurs `CMDIChildWnd` objets à partir du même modèle de document partagent le même menu, l’enregistrement de ressources système Windows.

- Menu fenêtre enfant MDI actif remplace entièrement les menus de la fenêtre frame MDI et la légende de la fenêtre enfant MDI active est ajoutée à la légende de la fenêtre de frame MDI. Pour plus d’exemples de fonctions de fenêtre enfant MDI qui sont implémentées en association avec une fenêtre frame MDI, consultez le `CMDIFrameWnd` description de classe.

N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame. Utilisez plutôt `CWnd::DestroyWindow`. Le `CFrameWnd` implémentation de `PostNcDestroy` supprime l’objet C++ lorsque la fenêtre est détruite. Lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut `OnClose` Gestionnaire appellera `DestroyWindow`.

Pour plus d’informations sur `CMDIChildWnd`, consultez [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

Appel à construire un `CMDIChildWnd` objet.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer la fenêtre visible.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMDIChildWnd::Create](#create).

##  <a name="create"></a>  CMDIChildWnd::Create

Appelez cette fonction membre pour créer une fenêtre enfant MDI de Windows et l’attacher à la `CMDIChildWnd` objet.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszClassName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui nomme la classe Windows (un [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) structure). Le nom de classe peut être n’importe quel nom inscrit avec le [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction globale. Doit être NULL pour une norme `CMDIChildWnd`.

*lpszWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui représente le nom de la fenêtre. Utilisé en tant que texte pour la barre de titre.

*dwStyle*<br/>
Spécifie la fenêtre [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) attributs. Le style WS_CHILD est requis.

*rect*<br/>
Contient la taille et la position de la fenêtre. Le `rectDefault` permet à Windows spécifier la taille et la position de la nouvelle valeur `CMDIChildWnd`.

*pParentWnd*<br/>
Spécifie le parent de la fenêtre. Si NULL, la fenêtre principale de l’application est utilisée.

*pContext*<br/>
Spécifie un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure. Ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fenêtre de frame enfant MDI active peut déterminer la légende de la fenêtre frame parente. Cette fonctionnalité est désactivée en désactivant le bit de style FWS_ADDTOTITLE de la fenêtre frame enfant.

L’infrastructure appelle cette fonction membre en réponse à une commande de l’utilisateur pour créer une fenêtre enfant, et l’infrastructure utilise le *pContext* paramètre pour se connecter correctement la fenêtre enfant à l’application. Lorsque vous appelez `Create`, *pContext* peut être NULL.

### <a name="example"></a>Exemple

Exemple 1 :

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Exemple

Exemple 2 :

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

Appelez cette fonction pour retourner le frame parent MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre de frame MDI parent.

### <a name="remarks"></a>Notes

Le frame retourné est deux parents retirés le `CMDIChildWnd` et est le parent de la fenêtre de type MDICLIENT qui gère la `CMDIChildWnd` objet. Appelez le [GetParent](../../mfc/reference/cwnd-class.md#getparent) fonction membre pour retourner le `CMDIChildWnd` parent MDICLIENT immédiat de l’objet en tant qu’une table temporaire `CWnd` pointeur.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

Appelez cette fonction membre pour activer une fenêtre MDI enfant indépendamment de la fenêtre frame MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Notes

Lorsque le frame devient actif, la fenêtre enfant qui a été activée en dernier est également activée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy

Appelez cette fonction membre pour détruire une fenêtre enfant MDI.

```
void MDIDestroy();
```

### <a name="remarks"></a>Notes

La fonction membre supprime le titre de la fenêtre enfant de la fenêtre frame et désactive la fenêtre enfant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize

Appelez cette fonction membre pour optimiser une fenêtre enfant MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Notes

Lorsqu’une fenêtre enfant est agrandie, Windows redimensionne pour le rendre sa zone cliente de remplir la zone cliente de la fenêtre frame. Windows place le menu de contrôle de la fenêtre enfant dans la barre de menus du frame afin que l’utilisateur peut restaurer ou fermer la fenêtre enfant et ajoute le titre de la fenêtre enfant pour le titre de fenêtre frame.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore

Appelez cette fonction membre pour restaurer une fenêtre enfant MDI à partir de taille réduite ou agrandie.

```
void MDIRestore();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles

Définit les descripteurs pour les ressources de menu et d’accélérateur.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
Le handle d’une ressource de menu.

*hAccel*<br/>
Le handle d’une ressource de l’accélérateur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir les ressources de menu et d’accélérateur utilisées par l’objet de fenêtre enfant MDI.

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../visual-cpp-samples.md)<br/>
[Exemple MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd, classe](../../mfc/reference/cmdiframewnd-class.md)
