---
description: 'En savoir plus sur : illustration du routage des commandes'
title: Illustration du routage des commandes
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: 51c5182eb1fa2a8b9666e265526e9220a9f3d4a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159958"
---
# <a name="command-routing-illustration"></a>Illustration du routage des commandes

Pour illustrer cet exemple, considérez un message de commande d’un élément de menu effacer tout dans le menu Edition d’une application MDI. Supposons que la fonction de gestionnaire pour cette commande est une fonction membre de la classe de document de l’application. Voici comment cette commande atteint son gestionnaire après que l’utilisateur a choisi l’élément de menu :

1. La fenêtre frame principale reçoit d’abord le message de commande.

1. La fenêtre frame MDI principale donne à la fenêtre enfant MDI active la possibilité de gérer la commande.

1. Le routage standard d’une fenêtre frame enfant MDI donne à sa vue une chance de la commande avant de vérifier sa propre table des messages.

1. La vue vérifie d’abord sa propre carte des messages et, en ne trouvant aucun gestionnaire, route la commande vers son document associé.

1. Le document vérifie la table des messages et trouve un gestionnaire. Cette fonction membre de document est appelée et le routage s’arrête.

Si le document n’avait pas de gestionnaire, il acheminerait ensuite la commande vers son modèle de document. Ensuite, la commande retourne à la vue, puis à la fenêtre frame. Enfin, la fenêtre frame vérifie la table des messages. En cas d’échec de cette vérification, la commande est redirigée vers la fenêtre frame MDI principale, puis vers l’objet application (la destination ultime des commandes non gérées).

## <a name="see-also"></a>Voir aussi

[Comment le Framework appelle un gestionnaire](how-the-framework-calls-a-handler.md)
