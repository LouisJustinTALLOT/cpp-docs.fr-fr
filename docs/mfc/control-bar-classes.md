---
title: Classes de barre de contrôle
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: 3426d84eab888a6fe78b663945776fff2fe708dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301953"
---
# <a name="control-bar-classes"></a>Classes de barre de contrôle

Barres de contrôle sont attachés à une fenêtre frame. Elles contiennent des boutons, volets d’état ou d’un modèle de boîte de dialogue. Barres de contrôles flottants, également appelés palettes d’outils, sont implémentées en les attachant à un [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) objet.

## <a name="framework-control-bars"></a>Barres de contrôles de Framework

Ces barres de contrôle font partie intégrante de l’infrastructure MFC. Elles sont plus faciles à utiliser et plus puissant que les Windows les barres de contrôle, car elles sont intégrées avec l’infrastructure. La plupart des applications MFC utilisent ces barres de contrôle, plutôt que les barres de contrôles Windows.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
La classe de base pour les barres de contrôle MFC répertoriés dans cette section. Une barre de contrôle est une fenêtre alignée sur le bord d’une fenêtre frame. La barre de contrôle contient soit `HWND`-en fonction des contrôles enfants ou des contrôles non basés sur un `HWND`, tels que des boutons de barre d’outils.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Une barre de contrôle qui est basée sur un modèle de boîte de dialogue.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Prend en charge une barre d’outils qui peut contenir des fenêtres enfants supplémentaires sous la forme de contrôles.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Les fenêtres de contrôle de barre d’outils contenant des boutons de commande de bitmap pas selon une `HWND`. La plupart des applications MFC utilisent cette classe au lieu de `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
La classe de base pour les fenêtres de contrôle de barre d’état. La plupart des applications MFC utilisent cette classe au lieu de `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Barres de contrôles Windows

Ces barres de contrôle sont des wrappers pour les contrôles Windows correspondants. Car ils ne sont pas intégrées avec l’infrastructure, ils sont plus difficiles à utiliser que les barres de contrôle répertoriés précédemment. La plupart des applications MFC utilisent les barres de contrôles répertoriés précédemment.

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implémente le contrôle interne de la `CRebar` objet.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Une fenêtre horizontale, généralement divisée en volets, dans laquelle une application peut afficher des informations d’état.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle commun de barre d'outils Windows.

## <a name="related-classes"></a>Classes connexes

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Une petite fenêtre contextuelle qui affiche une seule ligne de texte qui décrit l’objectif d’un outil dans une application.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Gère le stockage persistant de l’ancrage des données d’état pour les barres de contrôles.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
