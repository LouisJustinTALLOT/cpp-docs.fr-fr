---
title: Cibles de la commande
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 3f3305e7b67f4c001861c79c76c3b43a0c5a8ef0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506877"
---
# <a name="command-targets"></a>Cibles de la commande

La figure [commandes dans le Framework](../mfc/user-interface-objects-and-command-ids.md) montre la connexion entre un objet de l’interface utilisateur, comme un élément de menu et la fonction de gestionnaire, l’infrastructure appelle pour exécuter la commande qui en résulte un clic sur l’objet.

Windows envoie des messages qui ne sont pas des messages de commande directement à une fenêtre dont le gestionnaire pour le message est ensuite appelé. Toutefois, l’infrastructure achemine les commandes à un nombre d’objets candidats, appelée « cibles de la commande » — d'entre eux appelle normalement un gestionnaire pour la commande. Les fonctions du gestionnaire fonctionnent de manière identique pour les commandes et les messages Windows standard, mais les mécanismes par lesquels elles sont appelées sont différentes, comme expliqué dans [comment le Framework appelle un gestionnaire](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

