---
title: Classes de barre de contrôle
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440964"
---
# <a name="control-bar-classes"></a>Classes de barre de contrôle

Les barres de contrôles sont attachées à une fenêtre frame. Ils contiennent des boutons, des volets d’État ou un modèle de boîte de dialogue. Les barres de contrôle flottantes libres, également appelées palettes d’outils, sont implémentées en les joignant à un objet [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Barres de contrôles du Framework

Ces barres de contrôles font partie intégrante de l’infrastructure MFC. Ils sont plus faciles à utiliser et plus puissants que les barres de contrôles Windows, car ils sont intégrés à l’infrastructure. La plupart des applications MFC utilisent ces barres de contrôles plutôt que les barres de contrôle Windows.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
Classe de base pour les barres de contrôles MFC listées dans cette section. Une barre de contrôle est une fenêtre alignée sur le bord d’une fenêtre frame. La barre de contrôle contient des contrôles enfants basés sur `HWND`ou des contrôles qui ne sont pas basés sur un `HWND`, tels que des boutons de barre d’outils.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Barre de contrôles basée sur un modèle de boîte de dialogue.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Prend en charge une barre d’outils qui peut contenir des fenêtres enfants supplémentaires sous la forme de contrôles.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Fenêtres de contrôle de barre d’outils qui contiennent des boutons de commande Bitmap non basés sur un `HWND`. La plupart des applications MFC utilisent cette classe au lieu de `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
Classe de base pour les fenêtres de contrôle de barre d’État. La plupart des applications MFC utilisent cette classe au lieu de `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Barres de contrôles Windows

Ces barres de contrôles sont des wrappers légers pour les contrôles Windows correspondants. Étant donné qu’elles ne sont pas intégrées à l’infrastructure, elles sont plus difficiles à utiliser que les barres de contrôles précédemment répertoriées. La plupart des applications MFC utilisent les barres de contrôles précédemment listées.

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implémente le contrôle interne de l’objet `CRebar`.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Fenêtre horizontale, généralement divisée en volets, dans laquelle une application peut afficher des informations d’État.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle commun de barre d'outils Windows.

## <a name="related-classes"></a>Classes connexes

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Petite fenêtre contextuelle qui affiche une seule ligne de texte décrivant l’objectif d’un outil dans une application.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Gère le stockage persistant des données d’état d’ancrage pour les barres de contrôles.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
