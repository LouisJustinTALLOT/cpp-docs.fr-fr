---
title: Utilisation de CHotKeyCtrl
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: bf6ad9c8ea1b1a66f5a8abbf61f78c942ffda2fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483770"
---
# <a name="using-chotkeyctrl"></a>Utilisation de CHotKeyCtrl

Un contrôle hot key, représenté par la classe [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), est une fenêtre qui affiche une représentation textuelle de la combinaison de touches que l’utilisateur tape dans celui-ci, telles que CTRL + MAJ + Q. Il maintient également une représentation interne de cette clé sous la forme d’un code de touche virtuelle et un jeu d’indicateurs qui représentent l’état du décalage. Le contrôle de touche d’accès rapide ne définit pas la touche d’accès rapide, ce qui revient à votre programme. (Pour une liste des codes de touches virtuelles, consultez Winuser.h.)

Utilisez un contrôle de touche d’accès rapide pour obtenir une entrée utilisateur touche d’accès rapide à associer à une fenêtre ou d’un thread. Contrôles Hot key sont souvent utilisés dans les boîtes de dialogue, telles que vous pouvez afficher lors de la demande de l’utilisateur pour affecter une touche d’accès rapide. Il incombe de votre programme pour récupérer les valeurs décrivant la touche d’accès rapide à partir du contrôle de clé à chaud et à appeler les fonctions appropriées pour associer la touche d’accès rapide avec une fenêtre ou d’un thread.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Utilisation d’un contrôle de touche d’accès rapide](../mfc/using-a-hot-key-control.md)

- [Définition d’une touche d’accès rapide](../mfc/setting-a-hot-key.md)

- [Touches globales d’accès rapide](../mfc/global-hot-keys.md)

- [Touches d’accès rapide propres aux threads](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)

