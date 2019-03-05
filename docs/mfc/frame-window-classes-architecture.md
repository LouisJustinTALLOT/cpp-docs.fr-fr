---
title: Classes de fenêtre frame (architecture)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: affa217f481cc6d9e125d526f1b97be9120e0990
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298007"
---
# <a name="frame-window-classes-architecture"></a>Classes de fenêtre frame (architecture)

Dans l’architecture document/vue, fenêtres frame sont des fenêtres qui contiennent une fenêtre d’affichage. Ils prennent également en charge ayant contrôler barres qui leur sont attachées.

Dans plusieurs applications d’interface (multidocument MDI) document, la fenêtre principale est dérivée de `CMDIFrameWnd`. Il contient indirectement des cadres des documents qui sont `CMDIChildWnd` objets. Le `CMDIChildWnd` objets, à son tour, affichent des documents.

Dans les applications SDI (interface) de document unique, la fenêtre principale, dérivé de `CFrameWnd`, contient la vue du document actif.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
La classe de base pour la fenêtre frame principale d’une application SDI. Également la classe de base pour toutes les autres classes de fenêtre frame.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
La classe de base pour la fenêtre frame principale d’une application MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
La classe de base pour les fenêtres frame de document d’une application MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est en cours de modification en place.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
