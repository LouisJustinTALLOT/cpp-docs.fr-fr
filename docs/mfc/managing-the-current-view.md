---
title: Gestion de l’affichage actuel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09d29f4bc0b62e5824209759d45e63c1d9e2daa6
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928738"
---
# <a name="managing-the-current-view"></a>Gestion de l'affichage actuel
Dans le cadre de l’implémentation par défaut des fenêtres frame, une fenêtre frame effectue le suivi d’une vue actuellement active. Si la fenêtre frame contient plusieurs vues, comme par exemple dans une fenêtre fractionnée, la vue actuelle est la vue la plus récente en cours d’utilisation. La vue active est indépendante de la fenêtre active de Windows ou le focus d’entrée actuel.  
  
 Lorsque la vue active change, le framework informe l’affichage actuel en appelant son [OnActivateView](../mfc/reference/cview-class.md#onactivateview) fonction membre. Vous pouvez indiquer si la vue est activée ou désactivée en examinant `OnActivateView`de *bActivate* paramètre. Par défaut, `OnActivateView` définit le focus sur l’affichage actuel sur l’activation. Vous pouvez substituer `OnActivateView` pour effectuer un traitement spécial lors de la vue est activée ou désactivée. Par exemple, vous souhaiterez fournissent des signaux visuels spéciaux pour distinguer la vue active à partir d’autres vues.  
  
 Une fenêtre frame transfère des commandes pour son affichage actuel (actif), comme décrit dans [routage des commandes](../mfc/command-routing.md), en tant que partie du routage des commandes standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

