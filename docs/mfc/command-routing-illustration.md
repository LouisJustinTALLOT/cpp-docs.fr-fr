---
title: Illustration du routage des commandes
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: 3bc7c33762ab1868b29732d17e1a2e9700d11cf7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584559"
---
# <a name="command-routing-illustration"></a>Illustration du routage des commandes

Pour illustrer cela, imaginez un message de commande à partir d’un élément de menu Effacer tout dans le menu d’édition d’une application MDI. Supposons que la fonction gestionnaire pour cette commande se trouve être une fonction membre de classe de document de l’application. Voici comment la commande parvient jusqu'à son gestionnaire une fois que l’utilisateur choisit l’élément de menu :

1. La fenêtre frame principale reçoit tout d’abord le message de commande.

1. La fenêtre frame MDI principale donne une chance de traiter la commande à la fenêtre enfant MDI active.

1. Le routage standard d’une fenêtre de frame enfant MDI permet son affichage à la commande avant de vérifier sa propre table des messages.

1. La vue vérifie d’abord sa propre table des messages et ne trouver aucun gestionnaire, achemine ensuite la commande à son document associé.

1. Le document consulte sa table des messages et trouve un gestionnaire. La fonction de membre de ce document est appelée et le routage s’arrête.

Si le document n’a pas un gestionnaire, il achemine ensuite la commande à son modèle de document. Puis la commande retourne à la vue, puis la fenêtre frame. Enfin, la fenêtre frame Vérifiez sa table des messages. Si cette vérification a échoué, ainsi, la commande est acheminée vers la fenêtre frame MDI principale, puis à l’objet application — la destination finale des commandes non prises en charge.

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

