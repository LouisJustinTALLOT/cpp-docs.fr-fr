---
title: Classes de fenêtre frame (Fenêtres)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 1c0a1e1e93433e0fbe07c11eb350216173e74d84
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625853"
---
# <a name="frame-window-classes-windows"></a>Classes de fenêtre frame (Fenêtres)

Les fenêtres Frame sont des fenêtres qui encadrent une application ou une partie d’une application. Les fenêtres Frame contiennent généralement d’autres fenêtres, telles que des affichages, des barres d’outils et des barres d’État. Dans le cas de `CMDIFrameWnd` , ils peuvent contenir des `CMDIChildWnd` objets indirectement.

[CFrameWnd](reference/cframewnd-class.md)<br/>
Classe de base pour la fenêtre frame principale d’une application SDI. Il s’agit également de la classe de base pour toutes les autres classes de fenêtre frame.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Classe de base pour la fenêtre frame principale d’une application MDI.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Classe de base pour les fenêtres frame de document d’une application MDI.

[CMiniFrameWnd](reference/cminiframewnd-class.md)<br/>
Fenêtre frame de demi-hauteur généralement visible autour des barres d’outils flottantes.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est modifié sur place.

## <a name="related-class"></a>Classe associée

La classe `CMenu` fournit une interface par le biais de laquelle accéder aux menus de votre application. Il est utile pour manipuler des menus de manière dynamique au moment de l’exécution. par exemple, lors de l’ajout ou de la suppression d’éléments de menu en fonction du contexte. Bien que les menus soient souvent utilisés avec les fenêtres frames, ils peuvent également être utilisés avec des boîtes de dialogue et d’autres fenêtres non enfants.

[CMenu](reference/cmenu-class.md)<br/>
Encapsule un `HMENU` handle vers la barre de menus et les menus contextuels de l’application.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
