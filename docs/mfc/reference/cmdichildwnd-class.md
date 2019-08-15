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
ms.openlocfilehash: 09a9846cc3d242ef7d812cb31b4dcdd515d5f6ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506078"
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
|[CMDIChildWnd::Create](#create)|Crée la fenêtre enfant MDI Windows associée à l' `CMDIChildWnd` objet.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Retourne le frame MDI parent de la fenêtre cliente MDI.|
|[CMDIChildWnd:: MDIActivate](#mdiactivate)|Active cette fenêtre enfant MDI.|
|[CMDIChildWnd:: MDIDestroy](#mdidestroy)|Détruit cette fenêtre enfant MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Agrandit cette fenêtre enfant MDI.|
|[CMDIChildWnd:: MDIRestore](#mdirestore)|Restaure cette fenêtre enfant MDI à partir de la taille agrandie ou réduite.|
|[CMDIChildWnd::SetHandles](#sethandles)|Définit les descripteurs pour les ressources de menu et d’accélérateur.|

## <a name="remarks"></a>Notes

Une fenêtre enfant MDI ressemble à une fenêtre frame classique, à la différence près que la fenêtre enfant MDI apparaît à l’intérieur d’une fenêtre frame MDI plutôt que sur le bureau. Une fenêtre enfant MDI n’a pas de barre de menus propre, mais partage le menu de la fenêtre frame MDI. Le Framework change automatiquement le menu du frame MDI pour représenter la fenêtre enfant MDI active.

Pour créer une fenêtre enfant MDI utile pour votre application, dérivez une `CMDIChildWnd`classe de. Ajoutez des variables membres à la classe dérivée pour stocker des données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Il existe trois façons de construire une fenêtre enfant MDI:

- Construisez-le `Create`directement à l’aide de.

- Construisez-le `LoadFrame`directement à l’aide de.

- Créez-le indirectement par le biais d’un modèle de document.

Avant d’appeler `Create` ou `LoadFrame`, vous devez construire l’objet de fenêtre frame sur le tas à l' C++ aide de l’opérateur **New** . Avant d' `Create` appeler, vous pouvez également inscrire une classe de fenêtre à l’aide de la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) pour définir les styles de l’icône et de la classe du frame.

Utilisez la `Create` fonction membre pour passer les paramètres de création du frame comme arguments immédiats.

`LoadFrame`requiert moins d’arguments `Create`que et récupère à la place la plupart de ses valeurs par défaut des ressources, y compris la légende, l’icône, la table d’accélérateur et le menu du frame. Pour être accessible par `LoadFrame`, toutes ces ressources doivent avoir le même ID de ressource (par exemple, IDR_MAINFRAME).

Lorsqu’un `CMDIChildWnd` objet contient des vues et des documents, ceux-ci sont créés indirectement par le Framework plutôt que directement par le programmeur. L' `CDocTemplate` objet orchestre la création du frame, la création des vues conteneur et la connexion des vues au document approprié. Les paramètres du `CDocTemplate` constructeur spécifient le `CRuntimeClass` des trois classes impliquées (document, Frame et vue). Un `CRuntimeClass` objet est utilisé par l’infrastructure pour créer dynamiquement des frames lorsqu’ils sont spécifiés par l’utilisateur (par exemple, à l’aide de la commande fichier nouveau ou de la commande nouvelle fenêtre MDI).

Une classe de fenêtre frame dérivée `CMDIChildWnd` de doit être déclarée avec DECLARE_DYNCREATE pour que le mécanisme RUNTIME_CLASS ci-dessus fonctionne correctement.

La `CMDIChildWnd` classe hérite de la majeure partie de son `CFrameWnd`implémentation par défaut de. Pour obtenir une liste détaillée de ces fonctionnalités, reportez-vous à la description de la classe [CFrameWnd](../../mfc/reference/cframewnd-class.md) . La `CMDIChildWnd` classe possède les fonctionnalités supplémentaires suivantes:

- Conjointement avec la `CMultiDocTemplate` classe, plusieurs `CMDIChildWnd` objets du même modèle de document partagent le même menu, ce qui enregistre les ressources système Windows.

- Le menu de la fenêtre enfant MDI active remplace entièrement le menu de la fenêtre frame MDI, et la légende de la fenêtre enfant MDI active est ajoutée à la légende de la fenêtre frame MDI. Pour obtenir d’autres exemples de fonctions de fenêtre enfant MDI implémentées conjointement à une fenêtre frame MDI, consultez `CMDIFrameWnd` la description de la classe.

N’utilisez pas l' C++ opérateur **Delete** pour détruire une fenêtre frame. Utilisez plutôt `CWnd::DestroyWindow`. L' `CFrameWnd` implémentation de `PostNcDestroy` supprimera l' C++ objet lorsque la fenêtre sera détruite. Lorsque l’utilisateur ferme la fenêtre frame, le gestionnaire `OnClose` par défaut appellera `DestroyWindow`.

Pour plus d’informations `CMDIChildWnd`sur, consultez [fenêtres Frame](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

Appelez pour construire un `CMDIChildWnd` objet.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer la fenêtre visible.

### <a name="example"></a>Exemples

  Consultez l’exemple pour [CMDIChildWnd:: Create](#create).

##  <a name="create"></a>  CMDIChildWnd::Create

Appelez cette fonction membre pour créer une fenêtre enfant MDI Windows et l’attacher à l' `CMDIChildWnd` objet.

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
Pointe vers une chaîne de caractères se terminant par un caractère null qui nomme la classe Windows (structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) ). Le nom de la classe peut être n’importe quel nom enregistré avec la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) . Doit être NULL pour une norme `CMDIChildWnd`.

*lpszWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui représente le nom de la fenêtre. Utilisé comme texte pour la barre de titre.

*dwStyle*<br/>
Spécifie les attributs de [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) de fenêtre. Le style WS_CHILD est obligatoire.

*rect*<br/>
Contient la taille et la position de la fenêtre. La `rectDefault` valeur permet à Windows de spécifier la taille et la position du `CMDIChildWnd`nouvel.

*pParentWnd*<br/>
Spécifie le parent de la fenêtre. Si la valeur est NULL, la fenêtre principale de l’application est utilisée.

*pContext*<br/>
Spécifie une structure [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ce paramètre peut avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fenêtre frame enfant MDI active actuellement peut déterminer la légende de la fenêtre frame parente. Cette fonctionnalité est désactivée en désactivant le bit de style FWS_ADDTOTITLE de la fenêtre frame enfant.

L’infrastructure appelle cette fonction membre en réponse à une commande utilisateur pour créer une fenêtre enfant, et l’infrastructure utilise le paramètre *pContext* pour connecter correctement la fenêtre enfant à l’application. Quand vous appelez `Create`, *pContext* peut avoir la valeur null.

### <a name="example"></a>Exemple

Exemple 1 :

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Exemples

Exemple 2 :

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

Appelez cette fonction pour retourner le frame parent MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre frame parente MDI.

### <a name="remarks"></a>Notes

Le frame retourné est deux parents supprimés `CMDIChildWnd` du et est le parent de la fenêtre de type MdiClient qui gère l' `CMDIChildWnd` objet. Appelez la fonction membre [GetParent](../../mfc/reference/cwnd-class.md#getparent) pour retourner le `CMDIChildWnd` parent MdiClient immédiat de l’objet comme pointeur `CWnd` temporaire.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMDIFrameWnd:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

Appelez cette fonction membre pour activer une fenêtre enfant MDI indépendamment de la fenêtre frame MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Notes

Lorsque le frame devient actif, la fenêtre enfant qui a été activée pour la dernière fois est également activée.

### <a name="example"></a>Exemples

  Consultez l’exemple pour [CMDIFrameWnd:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

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

Appelez cette fonction membre pour agrandir une fenêtre enfant MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Notes

Quand une fenêtre enfant est agrandie, Windows la redimensionne pour que sa zone cliente remplisse la zone cliente de la fenêtre frame. Windows place le menu de contrôle de la fenêtre enfant dans la barre de menus du frame afin que l’utilisateur puisse restaurer ou fermer la fenêtre enfant et ajoute le titre de la fenêtre enfant au titre de la fenêtre frame.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>CMDIChildWnd:: MDIRestore

Appelez cette fonction membre pour restaurer une fenêtre enfant MDI à partir de la taille agrandie ou réduite.

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
Handle d’une ressource de menu.

*hAccel*<br/>
Handle d’une ressource d’accélérateur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir les ressources de menu et d’accélérateur utilisées par l’objet de fenêtre enfant MDI.

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd, classe](../../mfc/reference/cmdiframewnd-class.md)
