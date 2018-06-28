---
title: CMDIFrameWnd (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f3ba2a92ad523994a458abad9d4acee506e8e85
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038888"
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
|[CMDIFrameWnd::CreateClient](#createclient)|Crée une fenêtre **MDICLIENT** fenêtre pour ce `CMDIFrameWnd`. Appelée par le `OnCreate` fonction membre de `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crée une nouvelle fenêtre enfant.|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Retourne le menu contextuel de la fenêtre.|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Active la fenêtre enfant MDI différents.|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|Réorganise toutes les fenêtres enfants dans un format en cascade.|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Récupère la fenêtre enfant MDI actuellement active, ainsi que d’un indicateur qui signale l’enfant est agrandi ou non.|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Réorganise toutes les fenêtres enfants de document réduite.|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Agrandit une fenêtre enfant MDI.|  
|[CMDIFrameWnd::MDINext](#mdinext)|Active la fenêtre enfant immédiatement derrière la fenêtre enfant active et place la fenêtre enfant active derrière tous les autres fenêtres enfants.|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Active la fenêtre enfant précédente et place la fenêtre enfant actif immédiatement derrière lui.|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaure une fenêtre enfant MDI à partir de la taille agrandie ou réduite.|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Remplace le menu d’une fenêtre frame MDI, le menu contextuel de la fenêtre ou les deux.|  
|[CMDIFrameWnd::MDITile](#mditile)|Réorganise toutes les fenêtres enfants dans un format en mosaïque.|  
  
## <a name="remarks"></a>Notes  
 Pour créer une fenêtre de frame MDI utile pour votre application, dérivez une classe de `CMDIFrameWnd`. Ajoutez des variables membres à la classe dérivée pour stocker les données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.  
  
 Vous pouvez construire une fenêtre frame MDI en appelant le [créer](../../mfc/reference/cframewnd-class.md#create) ou [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) fonction membre de `CFrameWnd`.  
  
 Avant d’appeler `Create` ou `LoadFrame`, vous devez construire l’objet de fenêtre frame sur le tas à l’aide de C++ **nouveau** opérateur. Avant d’appeler `Create` vous pouvez également enregistrer une classe de fenêtre avec le [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction globale pour définir les styles d’icône et de la classe pour le frame.  
  
 Utilisez le `Create` fonction membre pour passer des paramètres de création du frame immédiats comme arguments.  
  
 `LoadFrame` nécessite moins d’arguments que `Create`et récupère à la place de la plupart de ses valeurs par défaut à partir des ressources, y compris la légende du frame, icône, table d’accélérateurs et menu. Accessible par `LoadFrame`, toutes ces ressources doivent avoir le même ID de ressource (par exemple, **IDR_MAINFRAME**).  
  
 Bien que **MDIFrameWnd** est dérivée de `CFrameWnd`, une classe de fenêtre frame dérivée de `CMDIFrameWnd` ne doivent pas être déclaré avec `DECLARE_DYNCREATE`.  
  
 Le `CMDIFrameWnd` classe hérite de son implémentation par défaut de `CFrameWnd`. Pour obtenir une liste détaillée de ces fonctionnalités, reportez-vous à la [CFrameWnd](../../mfc/reference/cframewnd-class.md) description de la classe. La `CMDIFrameWnd` classe possède les fonctionnalités supplémentaires suivantes :  
  
-   Une fenêtre frame MDI gère la **MDICLIENT** fenêtre, repositionnant conjointement avec les barres de contrôles. La fenêtre du client MDI est le parent direct des fenêtres de frame enfants MDI. Le **WS_HSCROLL** et **WS_VSCROLL** les styles de fenêtre spécifiés sur un `CMDIFrameWnd` s’appliquent à la fenêtre du client MDI plutôt qu’à la fenêtre frame principale pour l’utilisateur peut faire défiler la zone cliente MDI (comme dans les fenêtres Gestionnaire de programmes, par exemple).  
  
-   Une fenêtre frame MDI possède un menu par défaut qui est utilisé en tant que la barre de menus quand il n’existe aucune fenêtre MDI enfant active. Lorsqu’il existe un enfant MDI actif, barre de menus de la fenêtre frame MDI est automatiquement remplacée par le menu de fenêtre enfant MDI.  
  
-   Une fenêtre frame MDI fonctionne conjointement avec la fenêtre enfant MDI active, si elle existe. Par exemple, les messages de commande sont déléguées à l’enfant MDI actif avant de la fenêtre frame MDI.  
  
-   Une fenêtre frame MDI possède des gestionnaires par défaut pour les commandes de menu de fenêtre standard suivantes :  
  
    - **ID_WINDOW_TILE_VERT**  
  
    - **ID_WINDOW_TILE_HORZ**  
  
    - **ID_WINDOW_CASCADE**  
  
    - **ID_WINDOW_ARRANGE**  
  
-   Une fenêtre frame MDI possède également une implémentation de **ID_WINDOW_NEW**, ce qui crée un nouveau frame et la vue sur le document actif. Une application peut remplacer ces implémentations de commande par défaut pour personnaliser la gestion de fenêtre MDI.  
  
 N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame. Utilisez plutôt `CWnd::DestroyWindow`. Le `CFrameWnd` implémentation de `PostNcDestroy` va supprimer l’objet C++ lorsque la fenêtre est détruite. Lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut `OnClose` gestionnaire appelle `DestroyWindow`.  
  
 Pour plus d’informations sur `CMDIFrameWnd`, consultez [fenêtres Frame](../../mfc/frame-windows.md).  
  
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
 *lpCreateStruct*  
 Un pointeur long désignant un [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) structure.  
  
 *pWindowMenu*  
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
 *pClass*  
 La classe d’exécution de la fenêtre enfant doit être créé.  
  
 *nResource*  
 ID de ressources partagées associées à la fenêtre enfant.  
  
 *hMenu*  
 Menu de la fenêtre enfant.  
  
 *hAccel*  
 Accélérateur de la fenêtre enfant.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet de créer des fenêtres d’une fenêtre frame MDI enfants.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 Cet exemple est un extrait de l’article de la Base de connaissances Q201045, « comment faire : ajouter plusieurs Types de fenêtre à une application MDI Non-Document/Vue. » Articles de la Base de connaissances sont disponibles dans [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 Appelez cette fonction membre pour obtenir un handle vers le menu contextuel actif nommé « Fenêtre » (le menu contextuel avec les éléments de menu pour la gestion des fenêtres MDI).  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>Paramètres  
 *hMenuBar*  
 La barre de menus en cours.  
  
### <a name="return-value"></a>Valeur de retour  
 Le menu contextuel de fenêtre s’il existe ; dans le cas contraire **NULL**.  
  
### <a name="remarks"></a>Notes  
 Recherche de l’implémentation par défaut d’un menu contextuel contenant les commandes du menu Fenêtre standards tels que **ID_WINDOW_NEW** et **ID_WINDOW_TILE_HORZ**.  
  
 Remplacez cette fonction membre, si vous disposez d’un menu de fenêtre qui n’utilise pas l’ID de commande de menu standard.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate  
 Active la fenêtre enfant MDI différents.  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWndActivate*  
 Pointe vers la fenêtre enfant MDI à activer.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre envoie le [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) message à la fenêtre enfant en cours d’activation et de la fenêtre enfant en cours de désactivation.  
  
 Il s’agit du même message est envoyé si l’utilisateur modifie le focus à une fenêtre enfant MDI à l’aide de la souris ou le clavier.  
  
> [!NOTE]
>  Une fenêtre enfant MDI est activée indépendamment de la fenêtre frame MDI. Lorsque le frame devient actif, la fenêtre enfant qui a été activée en dernier est envoyée une [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) message pour dessiner un frame de fenêtre active et la barre de légende, mais il ne reçoit pas une autre `WM_MDIACTIVATE` message.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 Réorganise toutes les fenêtres MDI enfants dans un format en cascade.  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>Paramètres  
 *%nLes*  
 Spécifie un indicateur en cascade. Seul l’indicateur suivant peut être spécifié : `MDITILE_SKIPDISABLED`, désactivés fenêtres MDI enfants qui empêche d’être mises en cascade.  
  
### <a name="remarks"></a>Notes  
 La première version de `MDICascade`, sans paramètres, vous supprimez toutes les fenêtres enfants MDI, y compris désactivé ceux s’applique. La deuxième version est éventuellement pas des fenêtres en cascade désactivé MDI enfant si vous spécifiez `MDITILE_SKIPDISABLED` pour la `nType` paramètre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 Récupère l’active fenêtre enfant MDI active, ainsi que d’un indicateur qui signale si la fenêtre enfant est agrandie.  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbMaximized*  
 Un pointeur vers un **BOOL** valeur de retour. La valeur **TRUE** en retour si la fenêtre est agrandie ; sinon **FALSE**.  
  
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
 *pWnd*  
 Pointe vers la fenêtre à optimiser.  
  
### <a name="remarks"></a>Notes  
 Quand une fenêtre enfant est agrandie, Windows redimensionne pour le rendre sa zone cliente de remplissage de la fenêtre du client. Windows place le menu de contrôle de la fenêtre enfant dans la barre de menus du frame afin que l’utilisateur peut restaurer ou fermer la fenêtre enfant. Il ajoute également le titre de la fenêtre enfant au titre de la fenêtre frame.  
  
 Si une autre fenêtre MDI enfant est activée quand la fenêtre enfant MDI active est agrandie, Windows restaure l’enfant actuellement actif et agrandit la fenêtre enfant qui vient d’être activée.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 Active la fenêtre enfant immédiatement derrière la fenêtre enfant active et place la fenêtre enfant active derrière tous les autres fenêtres enfants.  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>Notes  
 Si la fenêtre enfant MDI active est agrandie, la fonction membre restaure l’enfant actuellement actif et optimise l’enfant qui vient d’être activée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 Active la fenêtre enfant précédente et place la fenêtre enfant actif immédiatement derrière lui.  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>Notes  
 Si la fenêtre enfant MDI active est agrandie, la fonction membre restaure l’enfant actuellement actif et optimise l’enfant qui vient d’être activée.  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 Restaure une fenêtre enfant MDI à partir de la taille agrandie ou réduite.  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
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
 *pFrameMenu*  
 Spécifie le menu du nouveau menu fenêtre frame. Si **NULL**, le menu n’est pas modifié.  
  
 *pWindowMenu*  
 Spécifie le menu de la nouvelle fenêtre, menu contextuel. Si **NULL**, le menu n’est pas modifié.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le menu de la fenêtre frame remplacé par ce message. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé `MDISetMenu`, une application doit appeler la [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) fonction membre de `CWnd` pour mettre à jour de la barre de menus.  
  
 Si cet appel remplace le menu contextuel de la fenêtre, les éléments de menu de fenêtre enfant MDI sont supprimées à partir du menu fenêtre précédent et ajoutés à la nouvelle fenêtre, menu contextuel.  
  
 Si une fenêtre enfant MDI est agrandie et que cet appel remplace le menu de la fenêtre frame MDI, les contrôles menu et de restauration de contrôle sont supprimées à partir du menu fenêtre frame précédent et ajoutés au nouveau menu.  
  
 Si vous utilisez l’infrastructure pour gérer vos fenêtres MDI enfants, n’appelez pas cette fonction membre.  
  
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
 *%nLes*  
 Spécifie un indicateur de mosaïque. Ce paramètre peut être l’un des indicateurs suivants :  
  
- `MDITILE_HORIZONTAL` Vignettes des fenêtres enfants MDI afin qu’une fenêtre s’affiche au-dessus d’un autre.  
  
- `MDITILE_SKIPDISABLED` Empêche que des fenêtres enfants MDI désactivés est affichée en mosaïque.  
  
- `MDITILE_VERTICAL` Vignettes des fenêtres enfants MDI afin qu’une fenêtre s’affiche à côté des autres.  
  
### <a name="remarks"></a>Notes  
 La première version de `MDITile`, les vignettes sans paramètres, les fenêtres verticalement sous Windows 3.1 et versions ultérieures. La deuxième version vignettes windows verticalement ou horizontalement, selon la valeur de la *%nLes* paramètre.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMDIFrameWnd::MDICascade](#mdicascade).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MDI](../../visual-cpp-samples.md)   
 [Exemple MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Exemple MFC SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd (classe)](../../mfc/reference/cframewnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)
