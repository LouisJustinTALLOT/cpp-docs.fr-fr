---
title: Que faire les fenêtres Frame | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], about frame widows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ed903238a812188d73093211265c9c8c028b0ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382565"
---
# <a name="what-frame-windows-do"></a>Fonctionnement des fenêtres frame
Outre l’encadrement simplement d’une vue, fenêtres frame sont responsables de plusieurs tâches de coordination entre le frame avec sa vue et l’application. [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) hériter [CFrameWnd](../mfc/reference/cframewnd-class.md), afin qu’ils puissent `CFrameWnd` fonctionnalités ainsi que des nouvelles fonctionnalités qu’ils ajouter. Exemples de fenêtres enfants incluent les vues, les contrôles tels que des boutons et des zones de liste et des barres de contrôles, y compris les barres d’outils, barres d’état et des barres de boîte de dialogue.  
  
 La fenêtre frame est chargée de gérer la disposition de ses fenêtres enfants. Dans l’infrastructure MFC, une fenêtre frame positionne les barres de contrôles, des vues et des autres fenêtres enfants à l’intérieur de sa zone cliente.  
  
 La fenêtre frame envoie également des commandes à ses vues et peut répondre aux messages de notification des fenêtres de contrôle.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Barres de contrôles (leur place dans la fenêtre frame)](../mfc/control-bars.md)  
  
-   [Gestion des menus, barres de contrôle et accélérateurs (leur place dans la fenêtre frame)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [Routage des commandes (à partir de la fenêtre frame à sa vue et autres cibles de commande)](../mfc/command-routing.md)  
  
-   [Architecture de /View de document](../mfc/document-view-architecture.md)  
  
-   [Barres de contrôles](../mfc/control-bars.md)  
  
-   [Contrôles](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres frame](../mfc/frame-windows.md)

