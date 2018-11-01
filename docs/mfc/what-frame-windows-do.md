---
title: Fonctionnement des fenêtres frame
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
ms.openlocfilehash: ea35b98e5234c10a10143bad1d35fdd1b4510ced
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508769"
---
# <a name="what-frame-windows-do"></a>Fonctionnement des fenêtres frame

Outre le tramage simplement une vue, fenêtres frame sont responsables de nombreuses tâches de coordination entre le frame avec sa vue et l’application. [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) héritent [CFrameWnd](../mfc/reference/cframewnd-class.md), afin qu’ils aient `CFrameWnd` fonctionnalités ainsi que les nouvelles fonctionnalités qu’ils ajouter. Exemples de fenêtres enfants incluent les vues, les contrôles tels que des boutons et des zones de liste et des barres de contrôle, y compris les barres d’outils, des barres d’état et des barres de boîte de dialogue.

La fenêtre frame est chargée de gérer la disposition de ses fenêtres enfants. Dans l’infrastructure MFC, une fenêtre frame positionne les barres de contrôles, des vues et des autres fenêtres enfants à l’intérieur de sa zone cliente.

La fenêtre frame envoie également des commandes à ses vues et peut répondre aux messages de notification à partir de windows de contrôle.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Barres de contrôles (leur place dans la fenêtre frame)](../mfc/control-bars.md)

- [Gestion des menus, barres de contrôle et accélérateurs (leur place dans la fenêtre frame)](../mfc/managing-menus-control-bars-and-accelerators.md)

- [Routage de commande (à partir de la fenêtre frame à sa vue et d’autres cibles de commande)](../mfc/command-routing.md)

- [Document /View Architecture](../mfc/document-view-architecture.md)

- [Barres de contrôles](../mfc/control-bars.md)

- [Contrôles](../mfc/controls-mfc.md)

## <a name="see-also"></a>Voir aussi

[Fenêtres frame](../mfc/frame-windows.md)

