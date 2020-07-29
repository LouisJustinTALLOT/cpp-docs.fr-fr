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
ms.openlocfilehash: 321ad0364257d7c20d54f9fdc884073381117c6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222951"
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
|[CMDIFrameWnd :: CMDIFrameWnd](#cmdiframewnd)|Construit un objet `CMDIFrameWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMDIFrameWnd :: CreateClient](#createclient)|Crée une fenêtre MDICLIENT Windows pour ce `CMDIFrameWnd` . Appelé par la `OnCreate` fonction membre de `CWnd` .|
|[CMDIFrameWnd :: CreateNewChild](#createnewchild)|Crée une nouvelle fenêtre enfant.|
|[CMDIFrameWnd :: GetWindowMenuPopup](#getwindowmenupopup)|Retourne le menu contextuel de la fenêtre.|
|[CMDIFrameWnd :: MDIActivate](#mdiactivate)|Active une autre fenêtre enfant MDI.|
|[CMDIFrameWnd :: MDICascade](#mdicascade)|Réorganise toutes les fenêtres enfants dans un format en cascade.|
|[CMDIFrameWnd :: MDIGetActive](#mdigetactive)|Récupère la fenêtre enfant MDI active, ainsi qu’un indicateur qui spécifie si l’enfant est agrandi ou non.|
|[CMDIFrameWnd :: MDIIconArrange](#mdiiconarrange)|Réorganise toutes les fenêtres enfants de document réduites.|
|[CMDIFrameWnd :: MDIMaximize](#mdimaximize)|Agrandit une fenêtre enfant MDI.|
|[CMDIFrameWnd :: MDINext](#mdinext)|Active la fenêtre enfant immédiatement derrière la fenêtre enfant actuellement active et place la fenêtre enfant actuellement active derrière toutes les autres fenêtres enfants.|
|[CMDIFrameWnd :: MDIPrev](#mdiprev)|Active la fenêtre enfant précédente et place la fenêtre enfant actuellement active immédiatement derrière elle.|
|[CMDIFrameWnd :: MDIRestore](#mdirestore)|Restaure une fenêtre enfant MDI à partir de la taille agrandie ou réduite.|
|[CMDIFrameWnd :: MDISetMenu](#mdisetmenu)|Remplace le menu d’une fenêtre frame MDI, du menu contextuel fenêtre ou des deux.|
|[CMDIFrameWnd :: MDITile](#mditile)|Réorganise toutes les fenêtres enfants dans un format en mosaïque.|

## <a name="remarks"></a>Notes

Pour créer une fenêtre frame MDI utile pour votre application, dérivez une classe de `CMDIFrameWnd` . Ajoutez des variables membres à la classe dérivée pour stocker des données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Vous pouvez construire une fenêtre frame MDI en appelant la fonction membre [Create](../../mfc/reference/cframewnd-class.md#create) ou [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) de `CFrameWnd` .

Avant d’appeler `Create` ou `LoadFrame` , vous devez construire l’objet de fenêtre frame sur le tas à l’aide de l' **`new`** opérateur C++. Avant `Create` d’appeler, vous pouvez également inscrire une classe de fenêtre à l’aide de la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) pour définir les styles de l’icône et de la classe du frame.

Utilisez la `Create` fonction membre pour passer les paramètres de création du frame comme arguments immédiats.

`LoadFrame`requiert moins d’arguments que `Create` et récupère à la place la plupart de ses valeurs par défaut des ressources, y compris la légende, l’icône, la table d’accélérateur et le menu du frame. Pour être accessible par `LoadFrame` , toutes ces ressources doivent avoir le même ID de ressource (par exemple, IDR_MAINFRAME).

Bien que `MDIFrameWnd` soit dérivée de `CFrameWnd` , une classe de fenêtre frame dérivée de `CMDIFrameWnd` ne doit pas être déclarée avec `DECLARE_DYNCREATE` .

La `CMDIFrameWnd` classe hérite de la majeure partie de son implémentation par défaut de `CFrameWnd` . Pour obtenir une liste détaillée de ces fonctionnalités, reportez-vous à la description de la classe [CFrameWnd](../../mfc/reference/cframewnd-class.md) . La `CMDIFrameWnd` classe possède les fonctionnalités supplémentaires suivantes :

- Une fenêtre frame MDI gère la fenêtre MDICLIENT, en la repositionnant en même temps que les barres de contrôles. La fenêtre cliente MDI est le parent direct des fenêtres frame MDI enfant. Les styles de fenêtre WS_HSCROLL et WS_VSCROLL spécifiés sur un `CMDIFrameWnd` s’appliquent à la fenêtre cliente MDI plutôt qu’à la fenêtre frame principale afin que l’utilisateur puisse faire défiler la zone cliente MDI (comme dans le gestionnaire de programmes Windows, par exemple).

- Une fenêtre frame MDI possède un menu par défaut qui est utilisé comme barre de menus lorsqu’il n’y a aucune fenêtre enfant MDI active. Lorsqu’il existe un enfant MDI actif, la barre de menus de la fenêtre frame MDI est automatiquement remplacée par le menu fenêtre enfant MDI.

- Une fenêtre frame MDI fonctionne conjointement avec la fenêtre enfant MDI active, le cas échéant. Par exemple, les messages de commande sont délégués à l’enfant MDI actuellement actif avant la fenêtre frame MDI.

- Une fenêtre frame MDI possède des gestionnaires par défaut pour les commandes de menu de fenêtre standard suivantes :

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Une fenêtre frame MDI a également une implémentation de ID_WINDOW_NEW, qui crée un nouveau Frame et une nouvelle vue sur le document actif. Une application peut remplacer ces implémentations de commandes par défaut pour personnaliser la gestion des fenêtres MDI.

N’utilisez pas l' **`delete`** opérateur C++ pour détruire une fenêtre frame. Utilisez `CWnd::DestroyWindow` à la place. L' `CFrameWnd` implémentation de `PostNcDestroy` supprimera l’objet C++ lorsque la fenêtre sera détruite. Lorsque l’utilisateur ferme la fenêtre frame, le gestionnaire par défaut `OnClose` appellera `DestroyWindow` .

Pour plus d’informations sur `CMDIFrameWnd` , consultez [fenêtres Frame](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd :: CMDIFrameWnd

Construit un objet `CMDIFrameWnd`.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Notes

Appelez la `Create` `LoadFrame` fonction membre ou pour créer la fenêtre frame MDI visible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd :: CreateClient

Crée la fenêtre cliente MDI qui gère les `CMDIChildWnd` objets.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Paramètres

*lpCreateStruct*<br/>
Pointeur long vers une structure [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) .

*pWindowMenu*<br/>
Pointeur vers le menu contextuel de la fenêtre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre doit être appelée si vous substituez `OnCreate` directement la fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd :: CreateNewChild

Crée une nouvelle fenêtre enfant.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Paramètres

*pClass*<br/>
Classe Runtime de la fenêtre enfant à créer.

*nResource*<br/>
ID des ressources partagées associées à la fenêtre enfant.

*hMenu*<br/>
Menu de la fenêtre enfant.

*hAccel*<br/>
Accélérateur de la fenêtre enfant.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour créer des fenêtres enfants d’une fenêtre frame MDI.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd :: GetWindowMenuPopup

Appelez cette fonction membre pour obtenir un handle du menu contextuel actuel nommé « Window » (le menu contextuel avec les éléments de menu pour la gestion des fenêtres MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Paramètres

*hMenuBar*<br/>
Barre de menus actuelle.

### <a name="return-value"></a>Valeur de retour

Le menu contextuel de la fenêtre, le cas échéant ; Sinon, NULL.

### <a name="remarks"></a>Notes

L’implémentation par défaut recherche un menu contextuel contenant des commandes de menu de fenêtre standard, telles que ID_WINDOW_NEW et ID_WINDOW_TILE_HORZ.

Remplacez cette fonction membre si vous disposez d’un menu fenêtre qui n’utilise pas les ID de commande de menu standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd :: MDIActivate

Active une autre fenêtre enfant MDI.

```cpp
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Paramètres

*pWndActivate*<br/>
Pointe vers la fenêtre enfant MDI à activer.

### <a name="remarks"></a>Notes

Cette fonction membre envoie le message [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) à la fois à la fenêtre enfant activée et à la fenêtre enfant désactivée.

Il s’agit du même message que celui envoyé si l’utilisateur change le focus en fenêtre enfant MDI à l’aide de la souris ou du clavier.

> [!NOTE]
> Une fenêtre enfant MDI est activée indépendamment de la fenêtre frame MDI. Lorsque le frame devient actif, la fenêtre enfant qui a été activée pour la dernière fois reçoit un message de [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) pour dessiner un cadre de fenêtre et une barre de légende active, mais il ne reçoit pas un autre message de WM_MDIACTIVATE.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CMDIFrameWnd :: GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd :: MDICascade

Réorganise toutes les fenêtres enfants MDI dans un format en cascade.

```cpp
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie un indicateur cascade. Seul l’indicateur suivant peut être spécifié : MDITILE_SKIPDISABLED, qui empêche les fenêtres enfants MDI désactivées d’être mises en cascade.

### <a name="remarks"></a>Notes

La première version de `MDICascade` , sans paramètre, cascade toutes les fenêtres enfants MDI, y compris celles qui sont désactivées. En option, la deuxième version ne met pas en cascade les fenêtres enfants MDI désactivées si vous spécifiez MDITILE_SKIPDISABLED pour le paramètre *ndéclarations* .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd :: MDIGetActive

Récupère la fenêtre enfant MDI active actuelle, ainsi qu’un indicateur qui spécifie si la fenêtre enfant est agrandie.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Paramètres

*pbMaximized*<br/>
Pointeur vers une valeur de retour BOOL. Affectez la valeur TRUE au retour si la fenêtre est agrandie ; Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre enfant MDI active.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CMDIChildWnd :: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd :: MDIIconArrange

Réorganise toutes les fenêtres enfants de document réduites.

```cpp
void MDIIconArrange();
```

### <a name="remarks"></a>Notes

Elle n’affecte pas les fenêtres enfants qui ne sont pas réduites.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CMDIFrameWnd :: MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd :: MDIMaximize

Agrandit la fenêtre enfant MDI spécifiée.

```cpp
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre à agrandir.

### <a name="remarks"></a>Notes

Quand une fenêtre enfant est agrandie, Windows la redimensionne pour que sa zone cliente remplisse la fenêtre cliente. Windows place le menu de contrôle de la fenêtre enfant dans la barre de menus du frame afin que l’utilisateur puisse restaurer ou fermer la fenêtre enfant. Elle ajoute également le titre de la fenêtre enfant au titre de la fenêtre frame.

Si une autre fenêtre enfant MDI est activée lorsque la fenêtre enfant MDI active est agrandie, Windows restaure l’enfant actuellement actif et agrandit la fenêtre enfant qui vient d’être activée.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CMDIChildWnd :: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd :: MDINext

Active la fenêtre enfant immédiatement derrière la fenêtre enfant actuellement active et place la fenêtre enfant actuellement active derrière toutes les autres fenêtres enfants.

```cpp
void MDINext();
```

### <a name="remarks"></a>Notes

Si la fenêtre enfant MDI active est agrandie, la fonction membre restaure l’enfant actuellement actif et maximise l’enfant qui vient d’être activé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd :: MDIPrev

Active la fenêtre enfant précédente et place la fenêtre enfant actuellement active immédiatement derrière elle.

```cpp
void MDIPrev();
```

### <a name="remarks"></a>Notes

Si la fenêtre enfant MDI active est agrandie, la fonction membre restaure l’enfant actuellement actif et maximise l’enfant qui vient d’être activé.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd :: MDIRestore

Restaure une fenêtre enfant MDI à partir de la taille agrandie ou réduite.

```cpp
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre à restaurer.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CMDIChildWnd :: MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd :: MDISetMenu

Remplace le menu d’une fenêtre frame MDI, du menu contextuel fenêtre ou des deux.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Paramètres

*pFrameMenu*<br/>
Spécifie le menu du nouveau menu de la fenêtre frame. Si la valeur est NULL, le menu n’est pas modifié.

*pWindowMenu*<br/>
Spécifie le menu du menu contextuel nouvelle fenêtre. Si la valeur est NULL, le menu n’est pas modifié.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le menu de la fenêtre frame remplacé par ce message. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.

### <a name="remarks"></a>Notes

Après `MDISetMenu` l’appel de, une application doit appeler la fonction membre [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) de `CWnd` pour mettre à jour la barre de menus.

Si cet appel remplace le menu contextuel fenêtre, les éléments de menu de la fenêtre enfant MDI sont supprimés du menu de la fenêtre précédente et ajoutés au menu contextuel nouvelle fenêtre.

Si une fenêtre enfant MDI est agrandie et que cet appel remplace le menu fenêtre frame MDI, le menu de contrôle et les contrôles de restauration sont supprimés du menu de la fenêtre frame précédente et ajoutés au menu nouveau.

N’appelez pas cette fonction membre si vous utilisez l’infrastructure pour gérer vos fenêtres enfants MDI.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd :: MDITile

Réorganise toutes les fenêtres enfants dans un format en mosaïque.

```cpp
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie un indicateur de mosaïque. Ce paramètre peut être l’un des indicateurs suivants :

- MDITILE_HORIZONTAL vignette les fenêtres enfants MDI afin qu’une fenêtre s’affiche au-dessus d’une autre.

- MDITILE_SKIPDISABLED empêche les fenêtres enfants MDI désactivées d’être en mosaïque.

- MDITILE_VERTICAL vignette les fenêtres enfants MDI afin qu’une fenêtre s’affiche en regard d’une autre.

### <a name="remarks"></a>Notes

La première version de `MDITile` , sans paramètres, vignette les fenêtres verticalement sous Windows versions 3,1 et ultérieures. La deuxième version mosaïque verticalement ou horizontalement, selon la valeur du paramètre *ndéclarations* .

### <a name="example"></a>Exemple

Consultez l’exemple pour [CMDIFrameWnd :: MDICascade](#mdicascade).

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (classe)](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd (classe)](../../mfc/reference/cmdichildwnd-class.md)
