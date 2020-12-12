---
description: 'En savoir plus sur : utilisation de CHotKeyCtrl'
title: Utilisation de CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: 7f17063a4fb3732a9b121e2b93f5d55e51d5654a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271679"
---
# <a name="using-chotkeyctrl"></a>Utilisation de CHotKeyCtrl

Un contrôle de touche d’accès rapide, représenté par la classe [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), est une fenêtre qui affiche une représentation textuelle de la combinaison de touches dans laquelle l’utilisateur tape, par exemple Ctrl + Maj + Q. Il gère également une représentation interne de cette clé sous la forme d’un code de touche virtuelle et d’un jeu d’indicateurs qui représentent l’état du décalage. Le contrôle de touche d’accès rapide ne définit pas réellement la touche d’accès rapide, ce qui revient à votre programme. (Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h.)

Utilisez un contrôle de touche d’accès rapide pour obtenir l’entrée d’un utilisateur pour laquelle la touche d’accès rapide doit être associée à une fenêtre ou un thread. Les contrôles de touche d’accès rapide sont souvent utilisés dans les boîtes de dialogue, par exemple lorsque vous demandez à l’utilisateur d’affecter une touche d’accès rapide. Il incombe à votre programme de récupérer les valeurs décrivant la touche d’accès rapide du contrôle de touche d’accès rapide et d’appeler les fonctions appropriées pour associer la touche d’accès rapide à une fenêtre ou un thread.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Utilisation d’un contrôle de touche d’accès rapide](../mfc/using-a-hot-key-control.md)

- [Définition d’une touche d’accès rapide](../mfc/setting-a-hot-key.md)

- [Touches d’accès rapide globales](../mfc/global-hot-keys.md)

- [Touches d’accès rapide spécifiques aux threads](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)
