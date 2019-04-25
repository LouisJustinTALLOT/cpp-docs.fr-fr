---
title: CMDIFrameWnd (classe)
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
ms.openlocfilehash: 9f5289491a7c14749865cfd163417440bc542aba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164187"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd (classe)

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
|[CMDIFrameWnd::CreateClient](#createclient)|Crée une fenêtre MDICLIENT de Windows pour ce `CMDIFrameWnd`. Appelé par le `OnCreate` fonction membre de `CWnd`.|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crée une nouvelle fenêtre enfant.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Retourne le menu contextuel de la fenêtre.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Active une autre fenêtre d’enfant MDI.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Réorganise toutes les fenêtres enfants dans un format en cascade.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Récupère la fenêtre enfant MDI active, ainsi que d’un indicateur qui spécifie si l’enfant est agrandie.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Réorganise toutes les fenêtres enfants de document réduite.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Agrandit une fenêtre enfant MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Active la fenêtre enfant immédiatement derrière la fenêtre enfant active et place la fenêtre enfant active derrière tous les autres fenêtres enfants.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Active la fenêtre enfant précédente et place la fenêtre enfant active immédiatement derrière lui.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaure une fenêtre enfant MDI à partir de taille réduite ou agrandie.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Remplace le menu d’une fenêtre frame MDI, le menu contextuel de la fenêtre ou les deux.|
|[CMDIFrameWnd::MDITile](#mditile)|Réorganise toutes les fenêtres enfants dans un format en mosaïque.|

## <a name="remarks"></a>Notes

Pour créer une fenêtre de frame MDI utile pour votre application, dérivez une classe de `CMDIFrameWnd`. Ajoutez des variables membres à la classe dérivée pour stocker les données propres à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Vous pouvez construire une fenêtre frame MDI en appelant le [créer](../../mfc/reference/cframewnd-class.md#create) ou [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) fonction membre de `CFrameWnd`.

Avant d’appeler `Create` ou `LoadFrame`, vous devez construire l’objet de fenêtre frame sur le tas à l’aide de C++ **nouveau** opérateur. Avant d’appeler `Create` vous pouvez également enregistrer une classe de fenêtre avec le [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction globale pour définir les styles d’icône et de classe pour le frame.

Utilisez le `Create` fonction membre pour passer des arguments comme immédiats de paramètres de création de l’image.

`LoadFrame` nécessite moins d’arguments que `Create`et récupère à la place de la plupart de ses valeurs par défaut à partir de ressources, y compris la légende du frame, icône, table d’accélérateurs et menu. Accessible par `LoadFrame`, toutes ces ressources doivent avoir le même ID de ressource (par exemple, IDR_MAINFRAME).

Bien que `MDIFrameWnd` est dérivée de `CFrameWnd`, une classe de fenêtre frame dérivée de `CMDIFrameWnd` ne doivent pas être déclaré avec `DECLARE_DYNCREATE`.

Le `CMDIFrameWnd` classe hérite de son implémentation par défaut à partir de `CFrameWnd`. Pour obtenir une liste détaillée de ces fonctionnalités, reportez-vous à la [CFrameWnd](../../mfc/reference/cframewnd-class.md) description de classe. Le `CMDIFrameWnd` classe a les fonctionnalités supplémentaires suivantes :

- Une fenêtre frame MDI gère la fenêtre MDICLIENT, il conjointement avec les barres de contrôles. La fenêtre cliente MDI est le parent direct des fenêtres de frame enfants MDI. Les styles de fenêtre WS_HSCROLL et WS_VSCROLL spécifiés sur un `CMDIFrameWnd` s’appliquent à la fenêtre cliente MDI au lieu de la fenêtre frame principale pour l’utilisateur peut faire défiler la zone du client MDI (comme dans le Windows responsable de programme, par exemple).

- Une fenêtre frame MDI possède un menu par défaut qui est utilisé en tant que la barre de menus lorsqu’il n’existe aucune fenêtre MDI enfant active. Lorsqu’il existe un enfant MDI actif, la barre de menus de la fenêtre frame MDI est automatiquement remplacée par le menu de fenêtre enfant MDI.

- Une fenêtre frame MDI fonctionne conjointement avec la fenêtre enfant MDI en cours, le cas échéant. Par exemple, les messages de commande sont déléguées à l’enfant MDI actif avant la fenêtre frame MDI.

- Une fenêtre frame MDI possède des gestionnaires par défaut pour les commandes de menu de fenêtre standards suivantes :

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Une fenêtre frame MDI possède également une implémentation de ID_WINDOW_NEW, ce qui crée un nouveau frame et les afficher sur le document actif. Une application peut remplacer ces implémentations de la commande par défaut pour personnaliser le traitement de fenêtre MDI.

N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame. Utilisez plutôt `CWnd::DestroyWindow`. Le `CFrameWnd` implémentation de `PostNcDestroy` supprime l’objet C++ lorsque la fenêtre est détruite. Lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut `OnClose` Gestionnaire appellera `DestroyWindow`.

Pour plus d’informations sur `CMDIFrameWnd`, consultez [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cmdiframewnd"></a>  CMDIFrameWnd::CMDIFrameWnd

Construit un objet `CMDIFrameWnd`.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Notes

Appelez le `Create` ou `LoadFrame` fonction membre pour créer la fenêtre frame MDI visible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient

Crée la fenêtre cliente MDI qui gère la `CMDIChildWnd` objets.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Paramètres

*lpCreateStruct*<br/>
Un pointeur long désignant un [CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) structure.

*pWindowMenu*<br/>
Pointeur vers le menu contextuel de la fenêtre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre doit être appelée si vous remplacez le `OnCreate` directement à la fonction de membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild

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
La classe d’exécution de la fenêtre enfant doit être créé.

*nResource*<br/>
ID de ressources partagées associées à la fenêtre enfant.

*hMenu*<br/>
Menu de la fenêtre enfant.

*hAccel*<br/>
Accélérateur de la fenêtre enfant.

### <a name="remarks"></a>Notes

Cette fonction permet de créer des fenêtres d’une fenêtre frame MDI enfants.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup

Appelez cette fonction membre pour obtenir un handle vers le menu contextuel actuel nommé « Fenêtre » (le menu contextuel des éléments de menu pour la gestion des fenêtres MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Paramètres

*hMenuBar*<br/>
La barre de menus en cours.

### <a name="return-value"></a>Valeur de retour

Le menu de fenêtre contextuels s’il existe ; Sinon, NULL.

### <a name="remarks"></a>Notes

L’implémentation par défaut recherche un menu contextuel contenant des commandes du menu Fenêtre standards tels que ID_WINDOW_NEW et ID_WINDOW_TILE_HORZ.

Remplacez cette fonction membre, si vous avez un menu Fenêtre qui n’utilise pas l’ID de commande de menu standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate

Active une autre fenêtre d’enfant MDI.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Paramètres

*pWndActivate*<br/>
Pointe vers la fenêtre MDI enfant à activer.

### <a name="remarks"></a>Notes

Cette fonction membre envoie le [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) message à la fenêtre enfant en cours d’activation et de la fenêtre enfant en cours de désactivation.

Il s’agit du même message est envoyé si l’utilisateur met le focus sur une fenêtre enfant MDI à l’aide de la souris ou le clavier.

> [!NOTE]
>  Une fenêtre enfant MDI est activée indépendamment de la fenêtre frame MDI. Lorsque le frame devient actif, la fenêtre enfant qui a été activée en dernier est envoyée une [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) message pour dessiner un frame de fenêtre active et la barre de légende, mais il ne reçoit pas d’un autre message WM_MDIACTIVATE.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade

Réorganise toutes les fenêtres MDI enfants dans un format en cascade.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie un indicateur en cascade. Peut être spécifié uniquement l’indicateur suivant : MDITILE_SKIPDISABLED, ce qui empêche des fenêtres MDI enfants désactivés en cours en cascade.

### <a name="remarks"></a>Notes

La première version de `MDICascade`, sans paramètres, se répercute toutes les fenêtres enfants MDI, y compris désactivé ceux. La deuxième version est éventuellement pas cascade désactivé MDI enfant windows si vous spécifiez MDITILE_SKIPDISABLED pour la *%nLes* paramètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive

Récupère la courante fenêtre enfant MDI active, ainsi que d’un indicateur qui spécifie si la fenêtre enfant est agrandie.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Paramètres

*pbMaximized*<br/>
Pointeur vers une valeur de retour de BOOL. La valeur TRUE au retour si la fenêtre est agrandie ; Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre enfant MDI active.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange

Réorganise toutes les fenêtres enfants de document réduite.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Notes

Il n’affecte pas les fenêtres enfants qui ne sont pas réduits.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMDIFrameWnd::MDICascade](#mdicascade).

##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize

Agrandit la fenêtre MDI enfant spécifiée.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre à agrandir.

### <a name="remarks"></a>Notes

Lorsqu’une fenêtre enfant est agrandie, Windows redimensionne pour le rendre sa zone cliente à remplir la fenêtre du client. Windows place le menu de contrôle de la fenêtre enfant dans la barre de menus du frame afin que l’utilisateur peut restaurer ou fermer la fenêtre enfant. Il ajoute également le titre de la fenêtre enfant pour le titre de fenêtre frame.

Si une autre fenêtre MDI enfant est activée lorsque la fenêtre enfant MDI active est agrandie, Windows restaure l’enfant actuellement actif et agrandit la fenêtre enfant qui vient d’être activée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext

Active la fenêtre enfant immédiatement derrière la fenêtre enfant active et place la fenêtre enfant active derrière tous les autres fenêtres enfants.

```
void MDINext();
```

### <a name="remarks"></a>Notes

Si la fenêtre enfant MDI active est réduite, la fonction membre restaure l’enfant actuellement actif et optimise l’enfant qui vient d’être activée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev

Active la fenêtre enfant précédente et place la fenêtre enfant active immédiatement derrière lui.

```
void MDIPrev();
```

### <a name="remarks"></a>Notes

Si la fenêtre enfant MDI active est réduite, la fonction membre restaure l’enfant actuellement actif et optimise l’enfant qui vient d’être activée.

##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore

Restaure une fenêtre enfant MDI à partir de taille réduite ou agrandie.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre à restaurer.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu

Remplace le menu d’une fenêtre frame MDI, le menu contextuel de la fenêtre ou les deux.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Paramètres

*pFrameMenu*<br/>
Spécifie le menu du nouveau menu fenêtre frame. Si NULL, le menu n’est pas modifié.

*pWindowMenu*<br/>
Spécifie le menu de la nouvelle fenêtre, menu contextuel. Si NULL, le menu n’est pas modifié.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le menu fenêtre frame remplacé par ce message. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.

### <a name="remarks"></a>Notes

Après avoir appelé `MDISetMenu`, une application doit appeler la [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) fonction membre de `CWnd` pour mettre à jour de la barre de menus.

Si cet appel remplace le menu contextuel de la fenêtre, les éléments de menu de fenêtre enfant MDI sont supprimées dans le menu fenêtre précédent et ajoutés à la nouvelle fenêtre, menu contextuel.

Si une fenêtre enfant MDI est agrandie et que cet appel remplace le menu de la fenêtre frame MDI, les contrôles menu et de restauration de contrôle sont supprimés dans le menu fenêtre frame précédent et ajoutés au nouveau menu.

N’appelez pas cette fonction membre si vous utilisez l’infrastructure pour gérer vos fenêtres MDI enfants.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

##  <a name="mditile"></a>  CMDIFrameWnd::MDITile

Réorganise toutes les fenêtres enfants dans un format en mosaïque.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie un indicateur de mosaïque. Ce paramètre peut être l’un des indicateurs suivants :

- Fenêtres enfants MDI de vignettes MDITILE_HORIZONTAL afin qu’une fenêtre s’affiche au-dessus d’un autre.

- MDITILE_SKIPDISABLED empêche désactivé des fenêtres MDI enfants à partir d’en cours en mosaïque.

- Fenêtres enfants MDI de vignettes MDITILE_VERTICAL afin qu’une fenêtre s’affiche en regard d’un autre.

### <a name="remarks"></a>Notes

La première version de `MDITile`, les vignettes sans paramètres, les fenêtres verticalement sous Windows 3.1 et versions ultérieures. La deuxième version vignettes windows verticalement ou horizontalement, selon la valeur de la *%nLes* paramètre.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)
