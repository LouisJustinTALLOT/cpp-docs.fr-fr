---
title: Cdockingmanager, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
dev_langs:
- C++
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c17b280d658eb615d314526f4fd241bf57c2eed1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074733"
---
# <a name="cdockingmanager-class"></a>Cdockingmanager, classe

Implémente la fonctionnalité principale qui contrôle la disposition d'ancrage dans une fenêtre frame principale.

## <a name="syntax"></a>Syntaxe

```
class CDockingManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|Crée un volet d’ancrage et l’ajoute à la liste des barres de contrôles.|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Ajoute un handle à une barre de volet à la liste des masqué MDI avec onglets des volets de barre.|
|[CDockingManager::AddMiniFrame](#addminiframe)|Ajoute un frame à la liste d’images mini-vidages.|
|[CDockingManager::AddPane](#addpane)|Inscrit un volet avec le Gestionnaire d’ancrage.|
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Recalcule et ajuste la disposition de tous les volets dans une fenêtre frame.|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Entraîne la WM_NCCALCSIZE du message à envoyer à tous les volets et `CPaneFrameWnd` windows.|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Ajuste l’alignement d’un rectangle.|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Redimensionne un volet d’ancrage en mode de masquage automatique afin qu’il prend toute la largeur ou hauteur de la zone cliente du frame entourée d’ancrer les sites.|
|[CDockingManager::AutoHidePane](#autohidepane)|Crée une barre d’outils de masquage automatique.|
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Affiche les barres ancrées qui ont l’alignement spécifié vers le haut.|
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Ajoute les noms des barres d’outils et des volets d’ancrage à un menu.|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcule le rectangle attendu d’une fenêtre ancrée.|
|[CDockingManager::Create](#create)|Crée un gestionnaire d’ancrage.|
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Détermine le volet qui contient un point donné et son état d’ancrage.|
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Active ou désactive le chargement de la mise en page d’accueil à partir du Registre.|
|[CDockingManager::DockPane](#dockpane)|Ancre un volet à un autre volet ou à une fenêtre frame.|
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Ancre un volet à gauche d'un autre volet.|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Permet d’ancrage du volet vers le frame principal, crée un volet d’ancrage et l’ajoute à la liste des barres de contrôles.|
|[CDockingManager::EnableDocking](#enabledocking)|Crée un volet d’ancrage et permet d’ancrage du volet vers le frame principal.|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Affiche un bouton supplémentaire qui ouvre un menu contextuel sur les légendes de tous les volets d’ancrage.|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Indique à la bibliothèque pour afficher un menu de contexte spécial qui contient une liste de barres d’outils de l’application et les volets d’ancrage lorsque l’utilisateur clique sur le bouton droit de la souris et de la bibliothèque traite le message WM_CONTEXTMENU.|
|[CDockingManager::FindDockSite](#finddocksite)|Récupère la barre de volet qui est à la position spécifiée et qui a l’alignement spécifié.|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Retourne la barre de volet qui a l’id du volet barre cible.|
|[CDockingManager::FindPaneByID](#findpanebyid)|Recherche un volet par l’ID de contrôle spécifié.|
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Valide toutes les positions de barre d’outils actuelles aux rectangles virtuels.|
|[CDockingManager::FrameFromPoint](#framefrompoint)|Retourne le frame qui contient le point donné.|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Obtient le rectangle qui contient les limites de la zone cliente.|
|[CDockingManager::GetDockingMode](#getdockingmode)|Retourne le mode d’ancrage actuels.|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Obtient un pointeur vers le frame de fenêtre parente.|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Retourne l’alignement est activée, des volets.|
|[CDockingManager::GetMiniFrames](#getminiframes)|Obtient une liste de miniframes.|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Obtient un rectangle qui contient les bords externes de la trame.|
|[CDockingManager::GetPaneList](#getpanelist)|Retourne une liste de volets qui appartiennent au gestionnaire d’ancrage. Cela inclut tous les volets flottants.|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Récupère un pointeur vers le Gestionnaire d’ancrage intelligent.|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Récupère un pointeur vers le Gestionnaire d’ancrage intelligent.|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Retourne les paramètres d’ancrage intelligents pour le Gestionnaire d’ancrage.|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Une méthode statique qui retourne un thème utilisé pour afficher les marqueurs d’ancrage intelligents.|
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Masque un volet qui est en mode de masquage automatique.|
|[CDockingManager::InsertDockSite](#insertdocksite)|Crée un volet d’ancrage et l’insère dans la liste des barres de contrôles.|
|[CDockingManager::InsertPane](#insertpane)|Insère un volet de contrôle dans la liste des barres de contrôles.|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Spécifie si un menu contextuel s’affiche sur les légendes de tous les volets.|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Détermine si les dispositions de tous les volets sont ajustées.|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Spécifie si le Gestionnaire d’ancrage est en mode de conteneur OLE.|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Détermine si un point spécifié se trouve près le site d’ancrage.|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Détermine si le mode Aperçu avant impression est défini.|
|[CDockingManager::LoadState](#loadstate)|Charge l’ancrage l’état du gestionnaire à partir du Registre.|
|[CDockingManager::LockUpdate](#lockupdate)|Verrouille la fenêtre donnée.|
|[CDockingManager::OnActivateFrame](#onactivateframe)|Appelé par le framework lorsque la fenêtre frame devient active ou est désactivée.|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Appelée par l’infrastructure quand un menu contextuel actif traite un message WM_DESTROY.|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Appelé par l’infrastructure pour déplacer une fenêtre mini-frame.|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Appelé par l’infrastructure lorsqu’il génère un menu qui contient une liste de volets.|
|[CDockingManager::PaneFromPoint](#panefrompoint)|Retourne le volet qui contient le point donné.|
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Appelé par l’infrastructure pour sélectionner ou pour effacer une case à cocher pour la commande spécifiée et recalculer la disposition d’un volet indiqué.|
|[CDockingManager::RecalcLayout](#recalclayout)|Recalcule la disposition interne des contrôles présents dans la liste des contrôles.|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Libère les conteneurs de volet vide.|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Enlève la masqué barre volet.|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Supprime un intervalle spécifié dans la liste d’images mini-vidages.|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Annule l’inscription d’un volet et le supprime de la liste dans le Gestionnaire d’ancrage.|
|[CDockingManager::ReplacePane](#replacepane)|Remplace un volet par un autre.|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Les images dans la liste des frames mini-vidages est analysée.|
|[CDockingManager::SaveState](#savestate)|Enregistre l’état du Gestionnaire d’ancrage dans le Registre.|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Envoie le message spécifié à tous les frames mini-vidages.|
|[CDockingManager::Serialize](#serialize)|Écrit le Gestionnaire d’ancrage dans une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Définit la taille, la largeur et la hauteur des barres de contrôles et le volet spécifié.|
|[CDockingManager::SetDockingMode](#setdockingmode)|Définit le mode d’ancrage.|
|[CDockingManager::SetDockState](#setdockstate)|Définit l’état d’ancrage de barres de contrôles, les frames mini-vidages et les barres de masquage automatique.|
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Définit le mode Aperçu avant impression des barres qui sont affichés dans l’aperçu avant impression.|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Définit les paramètres qui définissent le comportement d’ancrage actif.|
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Affiche ou masque les fenêtres frames mini.|
|[CDockingManager::ShowPanes](#showpanes)|Affiche ou masque les volets des barres de contrôle et de masquage automatique.|
|[CDockingManager::StartSDocking](#startsdocking)|Démarre l’ancrage actif de la fenêtre spécifiée en fonction de l’alignement du Gestionnaire d’ancrage intelligent.|
|[CDockingManager::StopSDocking](#stopsdocking)|S’arrête intelligente d’ancrage.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Spécifie si le Gestionnaire d’ancrage masque les volets en mode de conteneur OLE.|
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Spécifie le mode d’ancrage global.|
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Spécifie la sensibilité d’ancrage.|
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Spécifie l’heure, en millisecondes, avant un volet d’ancrage est ancré dans le mode d’ancrage immédiat.|
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Spécifie l’heure, en millisecondes, avant une barre d’outils est ancrée à la fenêtre frame principale.|

## <a name="remarks"></a>Notes

La fenêtre frame principale crée et initialise automatiquement de cette classe.

L’objet du Gestionnaire d’ancrage conserve une liste de tous les volets qui se trouvent dans la disposition d’ancrage et également une liste de tous les [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) windows qui appartiennent à la fenêtre frame principale.

Le `CDockingManager` classe implémente certains services que vous pouvez utiliser pour rechercher un volet ou un `CPaneFrameWnd` fenêtre. Vous généralement n’appelez pas ces services directement, car ils sont encapsulés dans l’objet de fenêtre frame principale. Pour plus d’informations, consultez [cpaneframewnd, classe](../../mfc/reference/cpaneframewnd-class.md).

## <a name="customization-tips"></a>Conseils de personnalisation

Les conseils suivants s’appliquent à `CDockingManager` objets :

- [Cdockingmanager, classe](../../mfc/reference/cdockingmanager-class.md) prend en charge ces modes d’accueil :

    - `AFX_DOCK_TYPE::DT_IMMEDIATE`

    - `AFX_DOCK_TYPE::DT_STANDARD`

    - `AFX_DOCK_TYPE::DT_SMART`

   Ces modes d’ancrage sont définis par [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) et sont définies en appelant [CDockingManager::SetDockingMode](#setdockingmode).

- Si vous souhaitez créer un volet non flottante, non redimensionnable, appelez le [CDockingManager::AddPane](#addpane) (méthode). Cette méthode inscrit le volet avec le Gestionnaire d’ancrage, ce qui est responsable de la disposition du volet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la `CDockingManager` classe permettant de configurer un `CDockingManager` objet. L’exemple montre comment afficher un bouton supplémentaire qui ouvre un menu contextuel sur les légendes de tous les volets d’ancrage et comment définir le mode d’ancrage de l’objet. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxDockingManager.h

##  <a name="adddocksite"></a>  CDockingManager::AddDockSite

Crée un volet d’ancrage et l’ajoute à la liste des barres de contrôles.

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Paramètres

*Info*<br/>
[in] Une référence à une structure d’informations contienne alignement du volet d’ancrage.

*ppDockBar*<br/>
[out] Un pointeur vers un pointeur vers le nouveau volet d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet d’ancrage a été créé avec succès ; FALSE sinon.

##  <a name="addhiddenmditabbedbar"></a>  CDockingManager::AddHiddenMDITabbedBar

Ajoute un handle à une barre de volet à la liste des masqué MDI avec onglets des volets de barre.

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Un pointeur vers une barre de volet

##  <a name="addpane"></a>  CDockingManager::AddPane

Inscrit un volet avec le Gestionnaire d’ancrage.

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in, out] Spécifie le volet à ajouter au gestionnaire d’ancrage.

*bTail*<br/>
[in] TRUE pour ajouter le volet à la fin de la liste des volets pour le Gestionnaire d’ancrage ; Sinon, FALSE.

*bAutoHide*<br/>
[in] Pour un usage interne uniquement. Utilisez toujours la valeur par défaut FALSE.

*bInsertForOuterEdge*<br/>
[in] Pour un usage interne uniquement. Utilisez toujours la valeur par défaut FALSE.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été correctement inscrit auprès du Gestionnaire d’ancrage ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour inscrire des volets non redimensionnables, non flottante auprès du Gestionnaire d’ancrage. Si vous n’enregistrez pas les volets, ils n’apparaissent pas lorsque le Gestionnaire d’ancrage est disposé.

##  <a name="adjustdockinglayout"></a>  CDockingManager::AdjustDockingLayout

Recalcule et ajuste la disposition de tous les volets dans une fenêtre frame.

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>Paramètres

*hdwp*<br/>
[in] Spécifie la structure de position de fenêtre différée. Pour plus d'informations, consultez [Types de données Windows](/windows/desktop/WinProg/windows-data-types).

### <a name="remarks"></a>Notes

##  <a name="addminiframe"></a>  CDockingManager::AddMiniFrame

Ajoute un frame à la liste d’images mini-vidages.

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Pointeur vers un frame.

### <a name="return-value"></a>Valeur de retour

TRUE si le frame n’est pas dans la liste des frames mini-vidages et a été ajouté avec succès ; FALSE sinon.

##  <a name="adjustpaneframes"></a>  CDockingManager::AdjustPaneFrames

Entraîne la WM_NCCALCSIZE du message à envoyer à tous les volets et `CPaneFrameWnd` windows.

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Notes

##  <a name="adjustrecttoclientarea"></a>  CDockingManager::AdjustRectToClientArea

Ajuste l’alignement d’un rectangle.

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

*rectResult*<br/>
[in] Une référence à un `CRect` objet

*dwAlignment*<br/>
[in] L’alignement de la `CRect` objet

### <a name="return-value"></a>Valeur de retour

TRUE si l’alignement de la `CRect` objet a été ajusté ; FALSE sinon.

### <a name="remarks"></a>Notes

Le *dwAlignment* paramètre peut avoir l’une des valeurs suivantes :

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

##  <a name="alignautohidepane"></a>  CDockingManager::AlignAutoHidePane

Redimensionne un volet d’ancrage en mode de masquage automatique afin qu’il prend toute la largeur ou hauteur de la zone cliente du frame entourée d’ancrer les sites.

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>Paramètres

*pDefaultSlider*<br/>
[in] Le volet d’ancrage du curseur.

*bIsVisible*<br/>
[in] TRUE si le volet d’ancrage est visible ; FALSE sinon.

##  <a name="autohidepane"></a>  CDockingManager::AutoHidePane

Crée une barre d’outils de masquage automatique.

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Un pointeur vers la barre de volet.

*pCurrAutoHideToolBar*<br/>
[in] Pointeur vers une barre d’outils de masquage automatique.

### <a name="return-value"></a>Valeur de retour

NULL si la barre d’outils de masquage automatique n’a pas été créé ; Sinon, un pointeur vers la nouvelle barre d’outils.

##  <a name="bringbarstotop"></a>  CDockingManager::BringBarsToTop

Affiche les barres ancrées qui ont l’alignement spécifié vers le haut.

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>Paramètres

*dwAlignment*<br/>
[in] L’alignement des barres d’ancrage qui sont importées vers le haut d’autres fenêtres.

*bExcludeDockedBars*<br/>
[in] TRUE pour exclure les barres ancrés d’être située en haut ; Sinon, FALSE.

##  <a name="buildpanesmenu"></a>  CDockingManager::BuildPanesMenu

Ajoute les noms des barres d’outils et des volets d’ancrage à un menu.

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>Paramètres

*Menu*<br/>
[in] Un menu pour ajouter les noms d’ancrage des volets et des barres d’outils.

*bToolbarsOnly*<br/>
[in] TRUE pour ajouter des noms de la barre d’outils uniquement dans le menu ; FALSE sinon.

##  <a name="calcexpecteddockedrect"></a>  CDockingManager::CalcExpectedDockedRect

Calcule le rectangle attendu d’une fenêtre ancrée.

```
void CalcExpectedDockedRect(
    CWnd* pWnd,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Pointeur vers la fenêtre à ancrer.

*ptMouse*<br/>
[in] L’emplacement de la souris.

*rectResult*<br/>
[out] Rectangle calculé.

*bDrawTab*<br/>
[in] True pour dessiner un onglet ; Sinon, FALSE.

*ppTargetBar*<br/>
[out] Pointeur vers un pointeur vers le volet cible.

### <a name="remarks"></a>Notes

Cette méthode calcule le rectangle une fenêtre occuperait si un utilisateur fait glisser la fenêtre au point spécifié par *ptMouse* et il ancré il.

##  <a name="create"></a>  CDockingManager::Create

Crée un gestionnaire d’ancrage.

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[in] Pointeur vers le frame parent du Gestionnaire d’ancrage. Cette valeur ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Toujours TRUE.

##  <a name="determinepaneandstatus"></a>  CDockingManager::DeterminePaneAndStatus

Détermine le volet qui contient un point donné et son état d’ancrage.

```
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,
    int nSensitivity,
    DWORD dwEnabledAlignment,
    CBasePane** ppTargetBar,
    const CBasePane* pBarToIgnore,
    const CBasePane* pBarToDock);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
[in] L’emplacement du volet à vérifier.

*nSensitivity*<br/>
[in] La valeur pour augmenter le rectangle de la fenêtre de chaque volet activé. Un volet satisfait les critères de recherche si le point donné se trouve dans cette région accrue.

*dwEnabledAlignment*<br/>
[in] L’alignement du volet d’ancrage.

*ppTargetBar*<br/>
[out] Pointeur vers un pointeur vers le volet cible.

*pBarToIgnore*<br/>
[in] Le volet de la méthode ignore.

*pBarToDock*<br/>
[in] Le volet est ancré.

### <a name="return-value"></a>Valeur de retour

L’état d’ancrage.

### <a name="remarks"></a>Notes

L’état d’ancrage peut prendre la valeur de l’une des valeurs suivantes :

|Valeur AFX_CS_STATUS|Signification|
|---------------------------|-------------|
|CS_NOTHING|Le pointeur ne se trouve pas sur un site d’ancrage. Par conséquent, conserver le volet flottant.|
|CS_DOCK_IMMEDIATELY|Le pointeur est sur le site d’ancrage dans le mode immédiat (style DT_IMMEDIATE est activé), donc le volet doit être ancré immédiatement.|
|CS_DELAY_DOCK|Le pointeur se trouve sur un site d’ancrage qui est un autre volet d’ancrage soit un bord du frame principal.|
|CS_DELAY_DOCK_TO_TAB|Le pointeur se trouve sur un site d’ancrage qui provoque le volet ancré dans une fenêtre à onglets. Cela se produit lorsque la souris est sur une légende d’un autre volet d’ancrage ou sur une zone d’onglet d’un volet à onglets.|

##  <a name="disablerestoredockstate"></a>  CDockingManager::DisableRestoreDockState

Active ou désactive le chargement de la mise en page d’accueil à partir du Registre.

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bDésactiver*<br/>
[in] True pour désactiver le chargement de la mise en page d’accueil à partir du Registre ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode lorsque vous devez conserver la disposition actuelle de volets d’ancrage et de barres d’outils lors du chargement de l’état de l’application.

##  <a name="dockpane"></a>  CDockingManager::DockPane

Ancre un volet à un autre volet ou à une fenêtre frame.

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Un pointeur vers une barre de volet pour ancrer dans.

*nDockBarID*<br/>
[in] L’id de la barre d’ancrage.

*lpRect*<br/>
[in] Le rectangle de destination.

##  <a name="dockpaneleftof"></a>  CDockingManager::DockPaneLeftOf

Ancre un volet à gauche d'un autre volet.

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Paramètres

*pBarToDock*<br/>
[in] Un pointeur vers le volet pour être ancré à gauche de *pTargetBar*.

*pTargetBar*<br/>
[in] Pointeur vers le volet cible.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été ancré avec succès ; Sinon, FALSE.

##  <a name="enableautohidepanes"></a>  CDockingManager::EnableAutoHidePanes

Permet d’ancrage du volet vers le frame principal, crée un volet d’ancrage et l’ajoute à la liste des barres de contrôles.

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
[in] L’alignement d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet d’ancrage a été créé avec succès ; FALSE sinon.

##  <a name="enabledocking"></a>  CDockingManager::EnableDocking

Crée un volet d’ancrage et permet d’ancrage du volet vers le frame principal.

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
[in] L’alignement d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet d’ancrage a été créé avec succès ; FALSE sinon.

##  <a name="enabledocksitemenu"></a>  CDockingManager::EnableDockSiteMenu

Affiche un bouton supplémentaire qui ouvre un menu contextuel sur les légendes de tous les volets d’ancrage.

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bActivez*<br/>
[in] TRUE pour activer le menu site d’ancrage ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Le menu d’ancrage site affiche les options suivantes pour modifier l’état d’ancrage du volet :

- `Floating` -Fait flotter un volet

- `Docking` -Ancre un volet à l’image principale à l’emplacement où le volet a été dernière ancré

- `AutoHide` -Bascule le volet en mode de masquage automatique

- `Hide` -Masque un volet

Par défaut, ce menu n’est pas affiché.

##  <a name="enablepanecontextmenu"></a>  CDockingManager::EnablePaneContextMenu

Indique à la bibliothèque pour afficher un menu de contexte spécial qui contient une liste de barres d’outils de l’application et les volets d’ancrage lorsque l’utilisateur clique sur le bouton droit de la souris et de la bibliothèque traite le message WM_CONTEXTMENU.

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>Paramètres

*bActivez*<br/>
[in] Si la valeur est TRUE, la bibliothèque Active la prise en charge pour le menu contextuel automatique ; Si la valeur FALSE la bibliothèque désactive la prise en charge pour le menu contextuel automatique.

*uiCustomizeCmd*<br/>
[in] Un id de commande pour le **personnaliser** élément dans le menu.

*strCustomizeText*<br/>
[in] Le texte de la **personnaliser** élément.

*bToolbarsOnly*<br/>
[in] Si la valeur est TRUE, le menu affiche uniquement une liste des barres d’outils de l’application ; Si la valeur est FALSE, la bibliothèque ajoute des volets d’ancrage d’application à cette liste.

##  <a name="finddocksite"></a>  CDockingManager::FindDockSite

Récupère la barre de volet qui est à la position spécifiée et qui a l’alignement spécifié.

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>Paramètres

*dwAlignment*<br/>
[in] L’alignement de la barre de volet.

*bOuter*<br/>
[in] Si la valeur est TRUE, extraire la barre à la position principale dans la liste de barres de contrôles. Récupérer dans le cas contraire, la barre à la position de fin dans la liste de barres de contrôles.

### <a name="return-value"></a>Valeur de retour

Le volet d’ancrage qui a l’alignement spécifié ; Sinon, NULL.

##  <a name="findpanebyid"></a>  CDockingManager::FindPaneByID

Recherche un volet par l’ID de contrôle spécifié.

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>Paramètres

*uBarID*<br/>
[in] Spécifie l’ID de contrôle du volet à rechercher.

*bSearchMiniFrames*<br/>
[in] TRUE pour inclure des volets flottants tout dans la recherche. FALSE pour inclure uniquement les volets ancrés.

### <a name="return-value"></a>Valeur de retour

Le [CBasePane](../../mfc/reference/cbasepane-class.md) objet qui a le contrôle spécifié ID, ou NULL si le volet spécifié est introuvable.

### <a name="remarks"></a>Notes

##  <a name="finddocksitebypane"></a>  CDockingManager::FindDockSiteByPane

Retourne la barre de volet qui a l’id du volet barre cible.

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>Paramètres

*pTargetBar*<br/>
[in] Pointeur vers le volet de barre cible.

### <a name="return-value"></a>Valeur de retour

La barre de volet qui a l’id du volet barre cible ; NULL si ce type ne barre volet existe.

##  <a name="fixupvirtualrects"></a>  CDockingManager::FixupVirtualRects

Valide toutes les positions de barre d’outils actuelles aux rectangles virtuels.

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur commence à faire glisser une barre d’outils, l’application souvienne de sa position d’origine dans le *rectangle virtuel*. Lorsque l’utilisateur déplace une barre d’outils sur son site d’ancrage, la barre d’outils peuvent se déplacer d’autres barres d’outils. Les positions d’origine des autres barres d’outils sont stockées dans les rectangles virtuels correspondants.

##  <a name="framefrompoint"></a>  CDockingManager::FrameFromPoint

Retourne le frame qui contient le point donné.

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
[in] Spécifie le point, en coordonnées d’écran, à vérifier.

*pFrameToExclude*<br/>
[in] Pointeur vers un frame à exclure.

*bFloatMultiOnly*<br/>
[in] True pour exclure les trames qui ne sont pas des instances de `CMultiPaneFrameWnd`; FALSE sinon.

### <a name="return-value"></a>Valeur de retour

Le frame qui contient le point donné ; Sinon, NULL.

##  <a name="getclientareabounds"></a>  CDockingManager::GetClientAreaBounds

Obtient le rectangle qui contient les limites de la zone cliente.

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>Paramètres

*rcClient*<br/>
[out] Une référence vers le rectangle qui contient les limites de la zone cliente.

### <a name="return-value"></a>Valeur de retour

Le rectangle qui contient les limites de la zone cliente.

##  <a name="getdockingmode"></a>  CDockingManager::GetDockingMode

Retourne le mode d’ancrage actuels.

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>Valeur de retour

Une valeur d’énumérateur qui représente le mode d’ancrage actuels. Il peut prendre l’une des valeurs suivantes :

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>Notes

Pour définir le mode d’ancrage, appelez [CDockingManager::SetDockingMode](#setdockingmode).

##  <a name="getdocksiteframewnd"></a>  CDockingManager::GetDockSiteFrameWnd

Obtient un pointeur vers le frame de fenêtre parente.

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le frame de fenêtre parente.

##  <a name="getenabledautohidealignment"></a>  CDockingManager::GetEnabledAutoHideAlignment

Retourne l’alignement est activée, des volets.

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>Valeur de retour

Une combinaison au niveau du bit des indicateurs CBRS_ALIGN_, ou 0 si les volets de masquage automatique ne sont pas activées. Pour plus d’informations, consultez [CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).

### <a name="remarks"></a>Notes

La méthode retourne l’alignement est activée pour les barres de contrôle de masquage automatique. Pour activer les barres de masquage automatique, appelez [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).

##  <a name="getminiframes"></a>  CDockingManager::GetMiniFrames

Obtient une liste de miniframes.

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>Valeur de retour

Une liste de miniframes qui contiennent les barres de contrôle qui appartiennent au gestionnaire d’ancrage.

##  <a name="getouteredgebounds"></a>  CDockingManager::GetOuterEdgeBounds

Obtient un rectangle qui contient les bords externes de la trame.

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>Valeur de retour

Un rectangle qui contient les bords externes de la trame.

##  <a name="getpanelist"></a>  CDockingManager::GetPaneList

Retourne une liste de volets qui appartiennent au gestionnaire d’ancrage. Cela inclut tous les volets flottants.

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>Paramètres

*lstBars*<br/>
[in, out] Contient tous les volets du Gestionnaire d’ancrage actuels.

*bIncludeAutohide*<br/>
[in] TRUE pour inclure les volets qui sont en mode de masquage automatique ; Sinon, FALSE.

*pRTCFilter*<br/>
[in] Si non NULL, la liste retournée contient les volets uniquement de la classe runtime spécifié.

*bIncludeTabs*<br/>
[in] TRUE pour inclure des onglets ; Sinon, FALSE.

### <a name="remarks"></a>Notes

S’il existe des volets à onglets dans le Gestionnaire d’ancrage, la méthode retourne des pointeurs vers [cbasetabbedpane, classe](../../mfc/reference/cbasetabbedpane-class.md) objets et vous devez énumérer les onglets explicitement.

Utilisez *pRTCFilter* pour obtenir une classe particulière de volets. Par exemple, vous pouvez obtenir uniquement les barres d’outils en définissant cette valeur en conséquence.

##  <a name="getsmartdockingmanager"></a>  CDockingManager::GetSmartDockingManager

Récupère un pointeur vers le Gestionnaire d’ancrage intelligent.

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le Gestionnaire d’ancrage intelligent.

##  <a name="getsmartdockingmanagerpermanent"></a>  CDockingManager::GetSmartDockingManagerPermanent

Récupère un pointeur vers le Gestionnaire d’ancrage intelligent.

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le Gestionnaire d’ancrage intelligent.

##  <a name="getsmartdockingparams"></a>  CDockingManager::GetSmartDockingParams

Retourne les paramètres d’ancrage intelligents pour le Gestionnaire d’ancrage.

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>Valeur de retour

La classe qui contient les paramètres d’ancrage intelligents pour le Gestionnaire d’ancrage en cours. Pour plus d’informations, consultez [csmartdockinginfo, classe](../../mfc/reference/csmartdockinginfo-class.md).

### <a name="remarks"></a>Notes

##  <a name="hideautohidepanes"></a>  CDockingManager::HideAutoHidePanes

Masque un volet qui est en mode de masquage automatique.

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>Paramètres

*pBarToExclude*<br/>
[in] Pointeur vers une barre à exclure de masquage.

*bImmediately*<br/>
[in] TRUE pour masquer le volet immédiatement ; FALSE pour masquer le volet de l’effet de masquage automatique.

##  <a name="insertdocksite"></a>  CDockingManager::InsertDockSite

Crée un volet d’ancrage et l’insère dans la liste des barres de contrôles.

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Paramètres

*Info*<br/>
[in] Structure qui contient les informations d’alignement sur le volet d’ancrage.

*dwAlignToInsertAfter*<br/>
[in] Alignement du volet d’ancrage.

*ppDockBar*<br/>
[out] Pointeur vers un pointeur vers un volet d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet d’ancrage a été créé avec succès ; FALSE sinon.

##  <a name="insertpane"></a>  CDockingManager::InsertPane

Insère un volet de contrôle dans la liste des barres de contrôles.

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>Paramètres

*pControlBar*<br/>
[in] Pointeur vers un volet de contrôle.

*pTarget*<br/>
[in] Pointeur vers un volet de la cible.

*exécuteront-ils*<br/>
[in] TRUE pour insérer le volet après la position du volet cible. FALSE sinon.

### <a name="return-value"></a>Valeur de retour

TRUE si le panneau de contrôle est ajouté avec succès à la liste des barres de contrôles ; FALSE sinon.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur false si le panneau de contrôle est déjà dans la liste des barres de contrôle ou si le volet cible n’existe pas dans la liste des barres de contrôles.

##  <a name="isdocksitemenu"></a>  CDockingManager::IsDockSiteMenu

Spécifie si un menu contextuel s’affiche sur les légendes de tous les volets.

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>Valeur de retour

TRUE si un menu de site d’ancrage s’affiche dans les légendes de tous les volets d’ancrage ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Vous pouvez activer le menu de site d’ancrage en appelant [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).

##  <a name="isinadjustlayout"></a>  CDockingManager::IsInAdjustLayout

Détermine si les dispositions de tous les volets sont ajustées.

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si les dispositions de tous les volets sont ajustées. FALSE sinon.

##  <a name="isolecontainermode"></a>  CDockingManager::IsOLEContainerMode

Spécifie si le Gestionnaire d’ancrage est en mode de conteneur OLE.

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le Gestionnaire d’ancrage est en mode de conteneur OLE ; Sinon, FALSE.

### <a name="remarks"></a>Notes

En mode de conteneur OLE, tous les volets d’ancrage et les barres d’outils de l’application sont masqués. Les volets sont également masqués dans ce mode si vous avez défini [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) sur TRUE.

##  <a name="ispointneardocksite"></a>  CDockingManager::IsPointNearDockSite

Détermine si un point spécifié se trouve près le site d’ancrage.

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Le point spécifié.

*dwBarAlignment*<br/>
[out] Spécifie le bord le point est proche. Les valeurs possibles sont CBRS_ALIGN_LEFT, CBRS_ALIGN_RIGHT, CBRS_ALIGN_TOP et CBRS_ALIGN_BOTTOM.

*bOuterEdge*<br/>
[out] TRUE si le point est proche de la bordure externe du site d’ancrage ; FALSE sinon.

### <a name="return-value"></a>Valeur de retour

TRUE si le point est proche du site d’ancrage ; Sinon, FALSE.

##  <a name="isprintpreviewvalid"></a>  CDockingManager::IsPrintPreviewValid

Détermine si le mode Aperçu avant impression est défini.

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le mode Aperçu avant impression est défini ; FALSE sinon.

##  <a name="loadstate"></a>  CDockingManager::LoadState

Charge l’ancrage l’état du gestionnaire à partir du Registre.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Nom du profil.

*uiID*<br/>
[in] L’id du Gestionnaire d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si l’état du Gestionnaire d’ancrage a été chargé avec succès ; Sinon, FALSE.

##  <a name="lockupdate"></a>  CDockingManager::LockUpdate

Verrouille la fenêtre donnée.

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>Paramètres

*Bloc*<br/>
[in] TRUE si la fenêtre est verrouillée ; FALSE sinon.

### <a name="remarks"></a>Notes

Quand une fenêtre est verrouillée, il ne peut pas être déplacé et qu’il ne peut pas être redessiné.

##  <a name="m_bhidedockingbarsincontainermode"></a>  CDockingManager::m_bHideDockingBarsInContainerMode

Spécifie si le Gestionnaire d’ancrage masque les volets en mode de conteneur OLE.

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>Notes

Définissez cette valeur sur FALSE si vous souhaitez conserver tous les volets ancrés au frame principal visible lorsque l’application est en mode de conteneur OLE. Par défaut, cette valeur est TRUE.

##  <a name="m_dockmodeglobal"></a>  CDockingManager::m_dockModeGlobal

Spécifie le mode d’ancrage global.

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>Notes

Par défaut, chaque volet d’ancrage utilise ce mode d’ancrage. Pour plus d’informations sur les valeurs de ce champ peut être défini sur, consultez [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

##  <a name="m_ndocksensitivity"></a>  CDockingManager::m_nDockSensitivity

Spécifie la sensibilité d’ancrage.

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>Notes

La sensibilité d’ancrage définit comment fermer flottante volet peut permettre d’approcher un volet d’ancrage, site d’ancrage ou un autre volet avant du framework modifie son état en ancré.

##  <a name="m_ntimeoutbeforedockingbardock"></a>  CDockingManager::m_nTimeOutBeforeDockingBarDock

Spécifie l’heure, en millisecondes, avant un volet d’ancrage est ancré dans le mode d’ancrage immédiat.

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>Notes

Avant un volet est ancré, le framework attend pendant la durée spécifiée. Cela empêche le volet ancré accidentellement à un emplacement pendant que l’utilisateur est toujours en le faisant glisser.

##  <a name="m_ntimeoutbeforetoolbardock"></a>  CDockingManager::m_nTimeOutBeforeToolBarDock

Spécifie l’heure, en millisecondes, avant une barre d’outils est ancrée à la fenêtre frame principale.

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>Notes

Avant une barre d’outils est ancrée, le framework attend pendant la durée spécifiée. Cela empêche la barre d’outils d’ancrage accidentellement à un emplacement pendant que l’utilisateur est toujours en le faisant glisser.

##  <a name="onactivateframe"></a>  CDockingManager::OnActivateFrame

Appelé par le framework lorsque la fenêtre frame devient active ou est désactivée.

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate*<br/>
[in] Si la valeur est TRUE, la fenêtre frame est activée ; Si la valeur est FALSE, la fenêtre frame est désactivée.

##  <a name="onclosepopupmenu"></a>  CDockingManager::OnClosePopupMenu

Appelée par l’infrastructure quand un menu contextuel actif traite un message WM_DESTROY.

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>Notes

Le framework envoie un message WM_DESTROY lorsqu’il est sur le point de fermer la fenêtre principale actuelle. Substituez cette méthode pour gérer les notifications à partir de `CMFCPopupMenu` objets qui appartiennent à la fenêtre frame lorsqu’un `CMFCPopupMenu` objet traite un message WM_DESTROY.

##  <a name="onmoveminiframe"></a>  CDockingManager::OnMoveMiniFrame

Appelé par l’infrastructure pour déplacer une fenêtre mini-frame.

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>Paramètres

*pFrame*<br/>
[in] Pointeur vers une fenêtre mini-frame.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode réussit ; Sinon, FALSE.

##  <a name="onpanecontextmenu"></a>  CDockingManager::OnPaneContextMenu

Appelé par l’infrastructure lorsqu’il génère un menu qui contient une liste de volets.

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Spécifie l’emplacement du menu.

##  <a name="panefrompoint"></a>  CDockingManager::PaneFromPoint

Retourne le volet qui contient le point donné.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar = false,
    CRuntimeClass* pRTCBarType = NULL,
    BOOL bCheckVisibility = FALSE,
    const CBasePane* pBarToIgnore = NULL) const;

virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType = NULL,
    const CBasePane* pBarToIgnore = NULL) const;
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Spécifie le point, en coordonnées d’écran, à vérifier.

*nSensitivity*<br/>
[in] La valeur augmentation le rectangle de la fenêtre de chaque volet activé. Un volet satisfait les critères de recherche si le point donné se trouve dans cette région exagérée.

*bExactBar*<br/>
[in] TRUE pour ignorer le *nSensitivity* paramètre ; sinon, FALSE.

*pRTCBarType*<br/>
[in] Si non NULL, la méthode recherche uniquement les volets du type spécifié.

*bCheckVisibility*<br/>
[in] TRUE pour ne vérifier que les volets visibles ; Sinon, FALSE.

*dwAlignment*<br/>
[out] Si un volet se trouve au point spécifié, ce paramètre contient le côté du volet qui a été le plus proche du point spécifié. Pour plus d'informations, consultez la section Remarques.

*pBarToIgnore*<br/>
[in] Si non NULL, la méthode ignore les volets spécifiées par ce paramètre.

### <a name="return-value"></a>Valeur de retour

Le [CBasePane](../../mfc/reference/cbasepane-class.md)-objet dérivé qui contient le point donné, ou NULL si aucun volet a été trouvée.

### <a name="remarks"></a>Notes

Lorsque la fonction retourne et un volet a été trouvé, *dwAlignment* contient l’alignement du point spécifié. Par exemple, si le point est la plus proche du haut du volet, *dwAlignment* CBRS_ALIGN_TOP a la valeur.

##  <a name="processpanecontextmenucommand"></a>  CDockingManager::ProcessPaneContextMenuCommand

Appelé par l’infrastructure pour sélectionner ou pour effacer une case à cocher pour la commande spécifiée et recalculer la disposition d’un volet indiqué.

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[in] L’id d’une barre de contrôle dans le menu.

*nCode*<br/>
[in] Le code de notification de commande.

*pExtra*<br/>
[in] Un pointeur vers void qui est converti en un pointeur vers `CCmdUI` si *nCode* est CN_UPDATE_COMMAND_UI.

*pHandlerInfo*<br/>
[in] Pointeur vers une structure d’informations. Ce paramètre n'est pas utilisé.

### <a name="return-value"></a>Valeur de retour

TRUE si *pEXtra* n’est pas NULL et *nCode* est égal à CN_UPDATE_COMMAND_UI, ou s’il existe une barre de contrôle avec la valeur *nID*.

##  <a name="recalclayout"></a>  CDockingManager::RecalcLayout

Recalcule la disposition interne des contrôles présents dans la liste des contrôles.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

*bNotify*<br/>
[in] Ce paramètre n’est pas utilisé.

##  <a name="releaseemptypanecontainers"></a>  CDockingManager::ReleaseEmptyPaneContainers

Libère les conteneurs de volet vide.

```
void ReleaseEmptyPaneContainers();
```

##  <a name="removehiddenmditabbedbar"></a>  CDockingManager::RemoveHiddenMDITabbedBar

Enlève la masqué barre volet.

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in] Un pointeur vers une barre de volet à supprimer.

##  <a name="removeminiframe"></a>  CDockingManager::RemoveMiniFrame

Supprime un intervalle spécifié dans la liste d’images mini-vidages.

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Pointeur vers une image à supprimer.

### <a name="return-value"></a>Valeur de retour

TRUE si le frame spécifié est supprimé ; FALSE sinon.

##  <a name="removepanefromdockmanager"></a>  CDockingManager::RemovePaneFromDockManager

Annule l’inscription d’un volet et le supprime de la liste dans le Gestionnaire d’ancrage.

```
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Pointeur vers un volet à supprimer.

*bDestroy*<br/>
[in] Si la valeur est TRUE, le volet supprimé est détruit.

*bAdjustLayout*<br/>
[in] Si la valeur est TRUE, ajuster la disposition d’ancrage immédiatement.

*bAutoHide*<br/>
[in] Si la valeur est TRUE, le volet est supprimé de la liste des barres de masquage automatique. Si la valeur est FALSE, le volet est supprimé dans la liste des volets régulières.

*pBarReplacement*<br/>
[in] Pointeur vers un volet qui remplace le volet supprimé.

##  <a name="replacepane"></a>  CDockingManager::ReplacePane

Remplace un volet par un autre.

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>Paramètres

*pOriginalBar*<br/>
[in] Pointeur vers le volet d’origine.

*pNewBar*<br/>
[in] Pointeur vers le volet qui remplace le volet d’origine.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet est remplacé avec succès ; FALSE sinon.

##  <a name="resortminiframesforzorder"></a>  CDockingManager::ResortMiniFramesForZOrder

Les images dans la liste des frames mini-vidages est analysée.

```
void ResortMiniFramesForZOrder();
```

##  <a name="savestate"></a>  CDockingManager::SaveState

Enregistre l’état du Gestionnaire d’ancrage dans le Registre.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Un chemin d’accès à une clé de Registre.

*uiID*<br/>
[in] L’ID du Gestionnaire d’ancrage.

### <a name="return-value"></a>Valeur de retour

TRUE si l’état a été enregistré avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

État du Gestionnaire d’ancrage dans le Registre d’enregistrement implique l’enregistrement des États des barres de contrôles, les États des barres de masquage automatique et les États des frames mini-vidages présents dans le Gestionnaire d’ancrage.

##  <a name="sendmessagetominiframes"></a>  CDockingManager::SendMessageToMiniFrames

Envoie le message spécifié à tous les frames mini-vidages.

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>Paramètres

*uMessage*<br/>
[in] Le message à envoyer.

*wParam*<br/>
[in] Dépendants des informations supplémentaires.

*lParam*<br/>
[in] Dépendants des informations supplémentaires.

### <a name="return-value"></a>Valeur de retour

Toujours TRUE.

##  <a name="serialize"></a>  CDockingManager::Serialize

Écrit le Gestionnaire d’ancrage dans une archive.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
[in] Une référence à un objet de l’archive.

### <a name="remarks"></a>Notes

Écriture du Gestionnaire d’ancrage dans une archive implique de déterminer le nombre d’ancrage des curseurs et barres de contrôle, et l’écriture des barres de contrôles, les frames mini-vidages, les barres de masquage automatique et les barres avec onglet MDI à l’archive.

##  <a name="setautohidezorder"></a>  CDockingManager::SetAutohideZOrder

Définit la taille, la largeur et la hauteur des barres de contrôles et le volet spécifié.

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>Paramètres

*pAHDockingBar*<br/>
[in] Pointeur vers un volet Ancrable.

##  <a name="setdockingmode"></a>  CDockingManager::SetDockingMode

Définit le mode d’ancrage.

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>Paramètres

*dockMode*<br/>
Spécifie le nouveau mode d’ancrage. Pour plus d'informations, consultez la section Remarques.

*Thème*<br/>
Spécifie le thème à utiliser pour les marqueurs d’ancrage intelligents. Il peut être une des valeurs énumérées suivantes : AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Notes

Appelez cette méthode statique pour définir le mode d’ancrage.

*dockMode* peut prendre l’une des valeurs suivantes :

- DT_STANDARD - mode d’ancrage Standard comme implémenté dans Visual Studio .NET 2003. Volets sont glissées sans un contexte de glissement.

- DT_IMMEDIATE - mode d’ancrage immédiat comme implémenté dans Microsoft Visio. Volets sont déplacés avec un contexte de glissement, mais aucun marqueur n’est affichées.

- DT_SMART - le mode d’ancrage intelligent comme implémenté dans Visual Studio 2005. Volets sont déplacés avec un contexte de glissement et affichage des marqueurs intelligents qui indiquent où le volet peut être ancré.

##  <a name="setdockstate"></a>  CDockingManager::SetDockState

Définit l’état d’ancrage de barres de contrôles, les frames mini-vidages et les barres de masquage automatique.

```
virtual void SetDockState();
```

##  <a name="setprintpreviewmode"></a>  CDockingManager::SetPrintPreviewMode

Définit le mode Aperçu avant impression des barres qui sont affichés dans l’aperçu avant impression.

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Paramètres

*bPreview*<br/>
[in] TRUE si le mode Aperçu avant impression est défini ; FALSE sinon.

*pState*<br/>
[in] Pointeur vers un état d’aperçu. Ce paramètre n'est pas utilisé.

##  <a name="setsmartdockingparams"></a>  CDockingManager::SetSmartDockingParams

Définit les paramètres qui définissent le comportement d’ancrage actif.

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Paramètres

*params*<br/>
[in, out] Définit les paramètres d’ancrage actif.

### <a name="remarks"></a>Notes

Appelez cette méthode si vous souhaitez personnaliser l’apparence, la couleur ou la forme des marqueurs d’ancrage intelligents.

Pour utiliser l’apparence par défaut pour les marqueurs d’ancrage intelligents, passez une instance non initialisée de [csmartdockinginfo, classe](../../mfc/reference/csmartdockinginfo-class.md) à *params*.

##  <a name="showdelayshowminiframes"></a>  CDockingManager::ShowDelayShowMiniFrames

Affiche ou masque les fenêtres frames mini.

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
[in] TRUE pour activer la fenêtre de l’image affichée ; FALSE pour masquer la fenêtre de l’image.

##  <a name="showpanes"></a>  CDockingManager::ShowPanes

Affiche ou masque les volets des barres de contrôle et de masquage automatique.

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
[in] TRUE pour afficher les volets ; FALSE pour masquer les volets.

### <a name="return-value"></a>Valeur de retour

Toujours la valeur FALSE.

##  <a name="startsdocking"></a>  CDockingManager::StartSDocking

Démarre l’ancrage actif de la fenêtre spécifiée en fonction de l’alignement du Gestionnaire d’ancrage intelligent.

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>Paramètres

*pDockingWnd*<br/>
[in] Pointeur vers une fenêtre pour l’ancrer.

##  <a name="stopsdocking"></a>  CDockingManager::StopSDocking

S’arrête intelligente d’ancrage.

```
void StopSDocking();
```

##  <a name="getsmartdockingtheme"></a>  CDockingManager::GetSmartDockingTheme

Une méthode statique qui retourne un thème utilisé pour afficher les marqueurs d’ancrage intelligents.

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>Valeur de retour

Retourne une des valeurs énumérées suivantes : AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx, classe](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd, classe](../../mfc/reference/cpaneframewnd-class.md)
