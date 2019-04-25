---
title: Illustration du routage des commandes
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: 56d131151f2284f12a3b46a9acd3cfbd3c8b0f47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164876"
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
