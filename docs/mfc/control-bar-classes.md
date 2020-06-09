---
title: Classes de barre de contrôle
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: f89770683edb1f4268b4f19adb74e5c08aa5f109
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620524"
---
# <a name="control-bar-classes"></a>Classes de barre de contrôle

Les barres de contrôles sont attachées à une fenêtre frame. Ils contiennent des boutons, des volets d’État ou un modèle de boîte de dialogue. Les barres de contrôle flottantes libres, également appelées palettes d’outils, sont implémentées en les joignant à un objet [CMiniFrameWnd](reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Barres de contrôles du Framework

Ces barres de contrôles font partie intégrante de l’infrastructure MFC. Ils sont plus faciles à utiliser et plus puissants que les barres de contrôles Windows, car ils sont intégrés à l’infrastructure. La plupart des applications MFC utilisent ces barres de contrôles plutôt que les barres de contrôle Windows.

[CControlBar](reference/ccontrolbar-class.md)<br/>
Classe de base pour les barres de contrôles MFC listées dans cette section. Une barre de contrôle est une fenêtre alignée sur le bord d’une fenêtre frame. La barre de contrôle contient `HWND` des contrôles enfants de base ou des contrôles qui ne sont pas basés sur un `HWND` , tels que des boutons de barre d’outils.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Barre de contrôles basée sur un modèle de boîte de dialogue.

[CReBar](reference/crebar-class.md)<br/>
Prend en charge une barre d’outils qui peut contenir des fenêtres enfants supplémentaires sous la forme de contrôles.

[CToolBar](reference/ctoolbar-class.md)<br/>
Fenêtres de contrôle de barre d’outils qui contiennent des boutons de commande Bitmap non basés sur un `HWND` . La plupart des applications MFC utilisent cette classe plutôt que `CToolBarCtrl` .

[CStatusBar](reference/cstatusbar-class.md)<br/>
Classe de base pour les fenêtres de contrôle de barre d’État. La plupart des applications MFC utilisent cette classe plutôt que `CStatusBarCtrl` .

## <a name="windows-control-bars"></a>Barres de contrôles Windows

Ces barres de contrôles sont des wrappers légers pour les contrôles Windows correspondants. Étant donné qu’elles ne sont pas intégrées à l’infrastructure, elles sont plus difficiles à utiliser que les barres de contrôles précédemment répertoriées. La plupart des applications MFC utilisent les barres de contrôles précédemment listées.

[CRebarCtrl](reference/crebarctrl-class.md)<br/>
Implémente le contrôle interne de l' `CRebar` objet.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Fenêtre horizontale, généralement divisée en volets, dans laquelle une application peut afficher des informations d’État.

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle commun de barre d'outils Windows.

## <a name="related-classes"></a>Classes connexes

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Petite fenêtre contextuelle qui affiche une seule ligne de texte décrivant l’objectif d’un outil dans une application.

[CDockState](reference/cdockstate-class.md)<br/>
Gère le stockage persistant des données d’état d’ancrage pour les barres de contrôles.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
