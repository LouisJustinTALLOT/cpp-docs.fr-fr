---
title: Classes de fenêtre frame (architecture)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441255"
---
# <a name="frame-window-classes-architecture"></a>Classes de fenêtre frame (architecture)

Dans l’architecture document/vue, les fenêtres Frame sont des fenêtres qui contiennent une fenêtre d’affichage. Ils prennent également en charge l’attachement de barres de contrôle.

Dans les applications d’interface multidocument (MDI, multiple document interface), la fenêtre principale est dérivée de `CMDIFrameWnd`. Il contient indirectement les frames de documents, qui sont des objets `CMDIChildWnd`. Les objets `CMDIChildWnd`, à leur tour, contiennent les vues des documents.

Dans les applications SDI (single document interface), la fenêtre principale, dérivée de `CFrameWnd`, contient la vue du document actif.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Classe de base pour la fenêtre frame principale d’une application SDI. Il s’agit également de la classe de base pour toutes les autres classes de fenêtre frame.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Classe de base pour la fenêtre frame principale d’une application MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Classe de base pour les fenêtres frame de document d’une application MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est modifié sur place.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
