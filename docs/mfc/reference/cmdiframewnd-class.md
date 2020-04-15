---
title: CMDIFrameWnd, classe
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: a6e68f6368a7b45e0a566a7d2d12f23a9cd62b12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370058"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd, classe

Fournit les fonctionnalités d'une fenêtre frame d'interface multidocument (MDI) Windows, ainsi que des membres permettant de gérer la fenêtre.

## <a name="syntax"></a>Syntaxe

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Construit un objet `CMDIFrameWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMDIFrameWnd::CreateClient](#createclient)|Crée une fenêtre Windows MDICLIENT pour cela `CMDIFrameWnd`. Appelé par `OnCreate` la `CWnd`fonction membre de .|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crée une nouvelle fenêtre pour enfants.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Retourne le menu pop-up Window.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Active une fenêtre d’enfant MDI différente.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Dispose toutes les fenêtres des enfants dans un format en cascade.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Récupère la fenêtre d’enfant MDI actuellement active, ainsi qu’un drapeau indiquant si l’enfant est maximisé ou non.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Organise toutes les fenêtres d’enfants de documents réduites au minimum.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximise une fenêtre d’enfant MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Active la fenêtre de l’enfant immédiatement derrière la fenêtre de l’enfant actuellement actif et place la fenêtre de l’enfant actuellement actif derrière toutes les autres fenêtres d’enfant.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Active la fenêtre de l’enfant précédent et place la fenêtre de l’enfant actuellement actif immédiatement derrière elle.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaure une fenêtre d’enfant MDI de la taille maximisée ou minimisée.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Remplace le menu d’une fenêtre de cadre MDI, le menu pop-up Window, ou les deux.|
|[CMDIFrameWnd::MDITile](#mditile)|Arrange toutes les fenêtres des enfants dans un format carrelé.|

## <a name="remarks"></a>Notes

Pour créer une fenêtre de cadre MDI utile `CMDIFrameWnd`pour votre application, dérivez une classe de . Ajoutez des variables aux membres à la classe dérivée pour stocker des données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Vous pouvez construire une fenêtre de cadre MDI en `CFrameWnd`appelant la fonction membre [Create](../../mfc/reference/cframewnd-class.md#create) or [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) de .

Avant d’appeler `Create` ou `LoadFrame`, vous devez construire l’objet de fenêtre de cadre sur le tas à l’aide du **nouvel** opérateur C. Avant `Create` d’appeler, vous pouvez également enregistrer un cours de fenêtre avec la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) pour définir les styles d’icône et de classe pour le cadre.

Utilisez `Create` la fonction du membre pour passer les paramètres de création du cadre comme arguments immédiats.

`LoadFrame`nécessite moins `Create`d’arguments que , et récupère plutôt la plupart de ses valeurs par défaut à partir de ressources, y compris la légende du cadre, icône, table d’accélérateur, et le menu. Pour être consulté `LoadFrame`par , toutes ces ressources doivent avoir la même pièce d’identité de ressource (par exemple, IDR_MAINFRAME).

Bien `MDIFrameWnd` que `CFrameWnd`est dérivé de , `CMDIFrameWnd` une classe `DECLARE_DYNCREATE`de fenêtre cadre dérivée de besoin de ne pas être déclaré avec .

La `CMDIFrameWnd` classe hérite d’une `CFrameWnd`grande partie de sa mise en œuvre par défaut de . Pour une liste détaillée de ces fonctionnalités, consultez la description de classe [CFrameWnd.](../../mfc/reference/cframewnd-class.md) La `CMDIFrameWnd` classe a les caractéristiques supplémentaires suivantes:

- Une fenêtre de cadre MDI gère la fenêtre MDICLIENT, la repositionnant en conjonction avec les barres de commande. La fenêtre du client MDI est le parent direct des fenêtres de cadre pour enfants MDI. Les WS_HSCROLL et WS_VSCROLL les styles de fenêtre `CMDIFrameWnd` spécifiés sur une application à la fenêtre du client MDI plutôt que la fenêtre du cadre principal afin que l’utilisateur puisse faire défiler la zone client MDI (comme dans le gestionnaire de programme Windows, par exemple).

- Une fenêtre cadre MDI possède un menu par défaut qui est utilisé comme barre de menu quand il n’y a pas de fenêtre active pour enfants MDI. Lorsqu’il y a un enfant MDI actif, la barre de menu de la fenêtre de cadre MDI est automatiquement remplacée par le menu de fenêtre pour enfants MDI.

- Une fenêtre de cadre MDI fonctionne en conjonction avec la fenêtre actuelle de l’enfant MDI, s’il y en a une. Par exemple, les messages de commande sont délégués à l’enfant MDI actuellement actif avant la fenêtre de cadre MDI.

- Une fenêtre de cadre MDI dispose de gestionnaires par défaut pour les commandes de menu Windows standard suivantes :

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Une fenêtre de cadre MDI dispose également d’une mise en œuvre de ID_WINDOW_NEW, ce qui crée un nouveau cadre et une vue sur le document actuel. Une application peut remplacer ces implémentations de commandes par défaut pour personnaliser la manipulation des fenêtres MDI.

N’utilisez pas l’opérateur de **suppression** de C POUR détruire une fenêtre de cadre. Utilisez `CWnd::DestroyWindow` à la place. La `CFrameWnd` mise `PostNcDestroy` en œuvre de supprimera l’objet CMD lorsque la fenêtre sera détruite. Lorsque l’utilisateur ferme la fenêtre `OnClose` du `DestroyWindow`cadre, le gestionnaire par défaut appelle .

Pour plus `CMDIFrameWnd`d’informations sur , voir [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd

Construit un objet `CMDIFrameWnd`.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Notes

Appelez `Create` la `LoadFrame` fonction ou le membre pour créer la fenêtre visible du cadre MDI.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd::CreateClient

Crée la fenêtre client MDI qui gère les `CMDIChildWnd` objets.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Paramètres

*lpCreateStruct*<br/>
Un long pointeur vers une structure [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pWindowMenu*<br/>
Un pointeur pour le menu pop-up Fenêtre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre doit être `OnCreate` appelée si vous remplacez directement la fonction du membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild

Crée une nouvelle fenêtre pour enfants.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Paramètres

*pClasse*<br/>
La classe de temps d’exécution de la fenêtre de l’enfant à créer.

*nResource*<br/>
L’id des ressources partagées associées à la fenêtre de l’enfant.

*hMenu*<br/>
Le menu de la fenêtre de l’enfant.

*hAccel (en)*<br/>
L’accélérateur de la fenêtre de l’enfant.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour créer des fenêtres pour enfants d’une fenêtre de cadre MDI.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup

Appelez cette fonction de membre pour obtenir une poignée au menu pop-up actuel nommé "Window" (le menu pop-up avec des éléments de menu pour la gestion de fenêtre MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Paramètres

*hMenuBar*<br/>
La barre de menu actuelle.

### <a name="return-value"></a>Valeur de retour

Le menu pop-up fenêtre si l’on existe; autrement NULL.

### <a name="remarks"></a>Notes

L’implémentation par défaut recherche un menu pop-up contenant des commandes standard de menu fenêtre telles que ID_WINDOW_NEW et ID_WINDOW_TILE_HORZ.

Remplacez cette fonction de membre si vous avez un menu Fenêtre qui n’utilise pas les cartes d’ID de commande standard du menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate

Active une fenêtre d’enfant MDI différente.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Paramètres

*pWndActivate (en)*<br/>
Indique que la fenêtre de l’enfant MDI doit être activée.

### <a name="remarks"></a>Notes

Cette fonction de membre envoie le [message WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) à la fenêtre de l’enfant activée et à la fenêtre de l’enfant désactivée.

C’est le même message qui est envoyé si l’utilisateur change la mise au point sur une fenêtre d’enfant MDI en utilisant la souris ou le clavier.

> [!NOTE]
> Une fenêtre d’enfant MDI est activée indépendamment de la fenêtre de cadre MDI. Lorsque le cadre devient actif, la fenêtre de l’enfant qui a été activée pour la dernière fois reçoit un message [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) pour dessiner un cadre de fenêtre actif et une barre de légende, mais elle ne reçoit pas un autre message WM_MDIACTIVATE.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd::MDICascade

Organise toutes les fenêtres pour enfants MDI dans un format cascadeur.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie un drapeau en cascade. Seul le drapeau suivant peut être spécifié : MDITILE_SKIPDISABLED, ce qui empêche les fenêtres d’enfants MDI désactivées d’être en cascade.

### <a name="remarks"></a>Notes

La première `MDICascade`version de , sans paramètres, cascade toutes les fenêtres pour enfants MDI, y compris les handicapés. La deuxième version en option ne cascade pas les fenêtres d’enfant MDI désactivé si vous spécifiez MDITILE_SKIPDISABLED pour le *paramètre nType.*

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive

Récupère la fenêtre active actuelle de l’enfant MDI, ainsi qu’un drapeau indiquant si la fenêtre de l’enfant est maximisée.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Paramètres

*pbMaximized*<br/>
Un pointeur à une valeur de retour BOOL. Définissez-vous à TRUE au retour si la fenêtre est maximisée; autrement FALSE.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre active de l’enfant MDI.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange

Organise toutes les fenêtres d’enfants de documents réduites au minimum.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Notes

Il n’affecte pas les fenêtres des enfants qui ne sont pas minimisées.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize

Maximise la fenêtre spécifique pour enfants MDI.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre pour maximiser.

### <a name="remarks"></a>Notes

Lorsqu’une fenêtre pour enfants est maximisée, Windows la resize pour que sa zone client remplisse la fenêtre du client. Windows place le menu de contrôle de la fenêtre de l’enfant dans la barre de menu du cadre afin que l’utilisateur puisse restaurer ou fermer la fenêtre de l’enfant. Il ajoute également le titre de la fenêtre enfant au titre de la fenêtre de cadre.

Si une autre fenêtre d’enfant MDI est activée lorsque la fenêtre d’enfant MDI actuellement active est maximisée, Windows restaure l’enfant actuellement actif et maximise la fenêtre de l’enfant nouvellement activée.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd::MDINext

Active la fenêtre de l’enfant immédiatement derrière la fenêtre de l’enfant actuellement actif et place la fenêtre de l’enfant actuellement actif derrière toutes les autres fenêtres d’enfant.

```
void MDINext();
```

### <a name="remarks"></a>Notes

Si la fenêtre d’enfant MDI actuellement active est maximisée, la fonction membre restaure l’enfant actuellement actif et maximise l’enfant nouvellement activé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd::MDIPrev

Active la fenêtre de l’enfant précédent et place la fenêtre de l’enfant actuellement actif immédiatement derrière elle.

```
void MDIPrev();
```

### <a name="remarks"></a>Notes

Si la fenêtre d’enfant MDI actuellement active est maximisée, la fonction membre restaure l’enfant actuellement actif et maximise l’enfant nouvellement activé.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd::MDIRestore

Restaure une fenêtre d’enfant MDI de la taille maximisée ou minimisée.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre pour restaurer.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu

Remplace le menu d’une fenêtre de cadre MDI, le menu pop-up Window, ou les deux.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Paramètres

*pFrameMenu*<br/>
Spécifie le menu du nouveau menu frame-window. Si NULL, le menu n’est pas modifié.

*pWindowMenu*<br/>
Spécifie le menu du nouveau menu pop-up Window. Si NULL, le menu n’est pas modifié.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le menu frame-window remplacé par ce message. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.

### <a name="remarks"></a>Notes

Après `MDISetMenu`l’appel , une application doit appeler `CWnd` la fonction membre [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) de mettre à jour la barre de menu.

Si cet appel remplace le menu pop-up Window, les éléments de menu pour enfants MDI sont supprimés du menu Windows précédent et ajoutés au nouveau menu pop-up Window.

Si une fenêtre pour enfants MDI est maximisée et que cet appel remplace le menu MDI frame-window, le menu Contrôle et les commandes de restauration sont supprimés du menu précédent de la fenêtre de cadre et ajoutés au nouveau menu.

N’appelez pas cette fonction de membre si vous utilisez le cadre pour gérer vos fenêtres d’enfant MDI.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd::MDITile

Arrange toutes les fenêtres des enfants dans un format carrelé.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie un drapeau de carrelage. Ce paramètre peut être l’un des drapeaux suivants :

- MDITILE_HORIZONTAL Tiles MDI fenêtres d’enfant de sorte qu’une fenêtre apparaît au-dessus d’une autre.

- MDITILE_SKIPDISABLED empêche les fenêtres d’enfants MDI désactivées d’être carrelées.

- MDITILE_VERTICAL Tiles MDI fenêtres d’enfant de sorte qu’une fenêtre apparaît à côté d’une autre.

### <a name="remarks"></a>Notes

La première `MDITile`version de , sans paramètres, tuiles les fenêtres verticalement sous les versions Windows 3.1 et plus tard. La deuxième version tuiles fenêtres verticalement ou horizontalement, en fonction de la valeur du *paramètre nType.*

### <a name="example"></a>Exemple

Voir l’exemple pour [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)
