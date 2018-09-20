---
title: Gestion de l’affichage actuel | Microsoft Docs
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
ms.openlocfilehash: ca9738f9b6083ef88c2f72e1608121f849f8e909
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425363"
---
# <a name="managing-the-current-view"></a>Gestion de l'affichage actuel

Dans le cadre de l’implémentation par défaut des fenêtres frame, une fenêtre frame des conserve une vue actuellement active. Si la fenêtre frame contient plusieurs vues, comme par exemple dans une fenêtre fractionnée, la vue actuelle est la vue la plus récente en cours d’utilisation. La vue active est indépendante de la fenêtre active dans Windows ou le focus d’entrée actuel.

Lorsque la vue active change, le framework informe l’affichage actuel en appelant son [OnActivateView](../mfc/reference/cview-class.md#onactivateview) fonction membre. Vous pouvez indiquer si la vue est activée ou désactivée en examinant `OnActivateView`de *bActivate* paramètre. Par défaut, `OnActivateView` définit le focus à la vue actuelle sur l’activation. Vous pouvez remplacer `OnActivateView` pour effectuer un traitement spécial lors de la vue est activée ou désactivée. Par exemple, vous pouvez souhaiter fournir des aides visuelles spéciaux pour distinguer la vue active d’autres vues.

Une fenêtre frame transfère des commandes pour son affichage actuel (actif), comme décrit dans [routage des commandes](../mfc/command-routing.md), en tant que partie du routage des commandes standard.

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

