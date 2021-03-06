---
description: 'En savoir plus sur : classes de fenêtres frames (architecture)'
title: Classes de fenêtre frame (architecture)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: 045108cd1e45325cf6069b5d8259ffab9abb0c2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155031"
---
# <a name="frame-window-classes-architecture"></a>Classes de fenêtre frame (architecture)

Dans l’architecture document/vue, les fenêtres Frame sont des fenêtres qui contiennent une fenêtre d’affichage. Ils prennent également en charge l’attachement de barres de contrôle.

Dans les applications d’interface multidocument (MDI, multiple document interface), la fenêtre principale est dérivée de `CMDIFrameWnd` . Il contient indirectement les frames de documents, qui sont des `CMDIChildWnd` objets. Les `CMDIChildWnd` objets contiennent à leur tour les vues des documents.

Dans les applications SDI (single document interface), la fenêtre principale, dérivée de `CFrameWnd` , contient la vue du document actif.

[CFrameWnd](reference/cframewnd-class.md)<br/>
Classe de base pour la fenêtre frame principale d’une application SDI. Il s’agit également de la classe de base pour toutes les autres classes de fenêtre frame.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Classe de base pour la fenêtre frame principale d’une application MDI.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Classe de base pour les fenêtres frame de document d’une application MDI.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est modifié sur place.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
