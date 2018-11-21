---
title: Objets d'interface utilisateur et ID de commande
ms.date: 11/19/2018
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
ms.openlocfilehash: 75bd3a8fb562b45289107c8eb01ee3745045462d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176833"
---
# <a name="user-interface-objects-and-command-ids"></a>Objets d'interface utilisateur et ID de commande

Éléments de menu, des boutons de barre d’outils et touches accélérateur sont des « objets interface utilisateur » capables de générer des commandes. Chacun de ces objets interface utilisateur avec un ID. Vous associez un objet d’interface utilisateur une commande en affectant le même ID à l’objet et de la commande. Comme expliqué dans [Messages](../mfc/messages.md), commandes sont implémentées en tant que messages spéciaux. La figure « Commandes dans la structure » ci-dessous montre comment le framework gère les commandes. Lorsqu’un objet d’interface utilisateur génère une commande, telles que `ID_EDIT_CLEAR_ALL`, l’un des objets dans votre application gère la commande, dans la figure ci-dessous, l’objet document `OnEditClearAll` fonction est appelée par le biais de table des messages du document.

![Commandes dans le Framework](../mfc/media/vc385p1.gif "commandes dans le Framework") <br/>
Commandes dans le Framework

La figure « Commande mise à jour dans la structure » ci-dessous montre comment MFC met à jour les objets d’interface utilisateur tels que les éléments de menu et boutons de barre d’outils. Avant d’un menu déroulant, ou pendant la boucle inactive dans le cas des boutons de barre d’outils, MFC achemine une commande de mise à jour. Dans la figure ci-dessous, l’objet document appelle son gestionnaire de commandes de mise à jour, `OnUpdateEditClearAll`, pour activer ou désactiver l’objet d’interface utilisateur.

![La mise à jour dans le cadre de la commande](../mfc/media/vc385p2.png "la mise à jour dans le cadre de la commande") <br/>
La mise à jour d’une commande dans le Framework

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)
