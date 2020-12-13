---
description: En savoir plus sur les fenêtres Frame
title: Fonctionnement des fenêtres frame
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
ms.openlocfilehash: 8f70bbe55b15310133688079236fe57459679090
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142829"
---
# <a name="what-frame-windows-do"></a>Fonctionnement des fenêtres frame

Outre le simple encadrement d’une vue, les fenêtres Frame sont responsables des nombreuses tâches impliquées dans la coordination du frame avec sa vue et avec l’application. [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) héritent de [CFrameWnd](../mfc/reference/cframewnd-class.md), de sorte qu’ils possèdent des fonctionnalités, ainsi `CFrameWnd` que de nouvelles fonctionnalités qu’ils ajoutent. Les fenêtres enfants incluent des vues, des contrôles tels que des boutons et des zones de liste, ainsi que des barres de contrôles, notamment des barres d’outils, des barres d’État et des barres de boîte de dialogue.

La fenêtre frame est responsable de la gestion de la disposition de ses fenêtres enfants. Dans l’infrastructure MFC, une fenêtre frame positionne les barres de contrôles, les vues et les autres fenêtres enfants à l’intérieur de sa zone cliente.

La fenêtre frame transmet également les commandes à ses vues et peut répondre aux messages de notification à partir de fenêtres de contrôle.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Barres de contrôles (comment elles s’ajustent à la fenêtre frame)](../mfc/control-bars.md)

- [Gestion des menus, des barres de contrôles et des accélérateurs (comment ils s’ajustent à la fenêtre frame)](../mfc/managing-menus-control-bars-and-accelerators.md)

- [Routage des commandes (de la fenêtre frame à sa vue et à d’autres cibles de commande)](../mfc/command-routing.md)

- [Architecture de document/View](../mfc/document-view-architecture.md)

- [Barres de contrôle](../mfc/control-bars.md)

- [Contrôles](../mfc/controls-mfc.md)

## <a name="see-also"></a>Voir aussi

[Fenêtres Frame](../mfc/frame-windows.md)
