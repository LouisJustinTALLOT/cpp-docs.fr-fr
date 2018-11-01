---
title: OnCmdMsg, gestionnaire
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 37b3d5ffa3e6492c8c00b8b22eba58d09fad51f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643168"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg, gestionnaire

Pour effectuer le routage des commandes, chaque cible de commande appelle le `OnCmdMsg` fonction membre de la cible de la commande suivante dans la séquence. Utilisation de cibles de commandes `OnCmdMsg` pour déterminer si elles peuvent traiter une commande et à acheminer vers une autre cible de commande si elles ne peuvent pas le gérer.

Chaque classe de cible de commande peut remplacer le `OnCmdMsg` fonction membre. Les remplacements permettent à chaque classe router les commandes vers une cible suivante particulière. Une fenêtre frame, par exemple, toujours achemine les commandes à sa fenêtre enfant Active ou la vue, comme indiqué dans le tableau [itinéraire de commande Standard](../mfc/command-routing.md).

La valeur par défaut `CCmdTarget` implémentation de `OnCmdMsg` utilise la table des messages de la classe cible de commande pour rechercher une fonction gestionnaire pour chaque message de commande qu’elle reçoit, de la même façon que les messages standard sont recherchés. S’il trouve une correspondance, il appelle le gestionnaire. Recherche de la table des messages est expliquée dans [comment le Framework recherches tables des messages](../mfc/how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

