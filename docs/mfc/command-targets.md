---
title: Cibles de la commande
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 59ba197174e95e42cd237c875f39f07801cb3dbe
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619310"
---
# <a name="command-targets"></a>Cibles de la commande

Les [commandes de figure dans le Framework](user-interface-objects-and-command-ids.md) illustrent la connexion entre un objet d’interface utilisateur, tel qu’un élément de menu, et la fonction de gestionnaire que l’infrastructure appelle pour exécuter la commande résultante lorsque l’utilisateur clique sur l’objet.

Windows envoie des messages qui ne sont pas des messages de commande directement à une fenêtre dont le gestionnaire du message est ensuite appelé. Toutefois, l’infrastructure achemine les commandes vers un certain nombre d’objets candidats, appelés « cibles de commande », dont l’un appelle normalement un gestionnaire pour la commande. Les fonctions du gestionnaire fonctionnent de la même façon pour les commandes et les messages Windows standard, mais les mécanismes par lesquels elles sont appelées sont différents, comme expliqué dans la [manière dont l’infrastructure appelle un gestionnaire](how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](messages-and-commands-in-the-framework.md)
