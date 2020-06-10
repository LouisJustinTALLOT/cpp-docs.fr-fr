---
title: Illustration du routage des commandes
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: d362cfe54a9b5a562237c7bb9632edae6e58228b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622910"
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

[Méthode d’appel d’un gestionnaire par le Framework](how-the-framework-calls-a-handler.md)
