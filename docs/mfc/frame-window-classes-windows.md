---
title: Classes de fenêtre frame (Fenêtres)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 3e56bd0f449992118db75a44c39b6e0e15cb0d86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392791"
---
# <a name="frame-window-classes-windows"></a>Classes de fenêtre frame (Fenêtres)

Fenêtres frame sont des fenêtres qui encadrent une application ou une partie d’une application. Fenêtres frame contiennent généralement des autres fenêtres, telles que les vues, les barres d’outils et les barres d’état. Dans le cas de `CMDIFrameWnd`, elles peuvent contenir des `CMDIChildWnd` objets indirectement.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
La classe de base pour la fenêtre frame principale d’une application SDI. Également la classe de base pour toutes les autres classes de fenêtre frame.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
La classe de base pour la fenêtre frame principale d’une application MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
La classe de base pour les fenêtres frame de document d’une application MDI.

[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)<br/>
Une fenêtre frame de demi-hauteur généralement visible autour de barres d’outils flottantes.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est en cours de modification en place.

## <a name="related-class"></a>Classe connexe

Classe `CMenu` fournit une interface par le biais duquel accéder aux menus de votre application. Il est utile pour la manipulation des menus dynamiquement au moment de l’exécution ; par exemple, lors de l’ajout ou la suppression d’éléments de menu en fonction du contexte. Bien que les menus sont souvent utilisées avec des fenêtres frame, ils peuvent également servir avec les boîtes de dialogue et les autres fenêtres non-enfant.

[CMenu](../mfc/reference/cmenu-class.md)<br/>
Encapsule une `HMENU` handle vers la barre de menus et les menus contextuels de l’application.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
