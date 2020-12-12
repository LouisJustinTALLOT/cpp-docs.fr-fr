---
description: 'En savoir plus sur : objets User-Interface et ID de commande'
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
ms.openlocfilehash: 142b72956e0a1b9e60ef48c7db325cd0ac822444
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263619"
---
# <a name="user-interface-objects-and-command-ids"></a>Objets d'interface utilisateur et ID de commande

Les éléments de menu, les boutons de barre d’outils et les touches d’accès rapide sont des « objets interface utilisateur » qui peuvent générer des commandes. Chaque objet d’interface utilisateur de ce type a un ID. Vous associez un objet d’interface utilisateur à une commande en affectant le même ID à l’objet et à la commande. Comme expliqué dans la rubrique [messages](../mfc/messages.md), les commandes sont implémentées en tant que messages spéciaux. La figure « commandes dans le Framework » ci-dessous montre comment l’infrastructure gère les commandes. Lorsqu’un objet d’interface utilisateur génère une commande, telle que `ID_EDIT_CLEAR_ALL` , l’un des objets de votre application gère la commande. dans la figure ci-dessous, la fonction de l’objet document `OnEditClearAll` est appelée via la table des messages du document.

![Commandes dans le Framework](../mfc/media/vc385p1.gif "Commandes dans le Framework") <br/>
Commandes dans le Framework

La figure « mise à jour de la commande dans le Framework » ci-dessous montre comment MFC met à jour les objets d’interface utilisateur tels que les éléments de menu et les boutons de la barre d’outils. Avant qu’un menu ne descende, ou pendant la boucle inactive dans le cas de boutons de barre d’outils, MFC achemine une commande de mise à jour. Dans la figure ci-dessous, l’objet document appelle son gestionnaire de commandes Update, `OnUpdateEditClearAll` , pour activer ou désactiver l’objet interface utilisateur.

![Mise à jour des commandes dans le Framework](../mfc/media/vc385p2.png "Mise à jour des commandes dans le Framework") <br/>
Mise à jour des commandes dans le Framework

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)
