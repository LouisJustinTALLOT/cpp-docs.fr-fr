---
description: 'En savoir plus sur : gestion de l’affichage actuel'
title: Gestion de l'affichage actuel
ms.date: 11/04/2016
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
ms.openlocfilehash: 9c9acd315636ea33c52fbe63374b5afacef95247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283340"
---
# <a name="managing-the-current-view"></a>Gestion de l'affichage actuel

Dans le cadre de l’implémentation par défaut des fenêtres Frame, une fenêtre frame effectue le suivi d’une vue actuellement active. Si la fenêtre frame contient plusieurs vues, comme par exemple dans une fenêtre fractionnée, la vue actuelle est la vue la plus récente en cours d’utilisation. La vue active est indépendante de la fenêtre active dans Windows ou du focus d’entrée actuel.

Lorsque la vue active change, l’infrastructure notifie la vue actuelle en appelant sa fonction membre [OnActivateView](reference/cview-class.md#onactivateview) . Vous pouvez déterminer si la vue est activée ou désactivée en examinant le `OnActivateView` paramètre *bActivate* . Par défaut, `OnActivateView` définit le focus sur la vue actuelle lors de l’activation. Vous pouvez remplacer `OnActivateView` pour effectuer un traitement spécial lorsque la vue est désactivée ou réactivée. Par exemple, vous souhaiterez peut-être fournir des signaux visuels spéciaux pour distinguer la vue active des autres vues inactives.

Une fenêtre frame transfère les commandes à sa vue actuelle (active), comme décrit dans [routage](command-routing.md)des commandes, dans le cadre du routage des commandes standard.

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
