---
title: Illustration du routage de commande | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a12a5cd19177761dfbf484c64f528d8def194ca5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341134"
---
# <a name="command-routing-illustration"></a>Illustration du routage des commandes
Pour illustrer cela, envisagez d’un message de commande à partir d’un élément de menu Effacer tout dans le menu Edition d’une application MDI. Supposons que la fonction de gestionnaire pour cette commande est une fonction membre de classe de document de l’application. Voici comment la commande parvient jusqu'à son gestionnaire d’une fois que l’utilisateur choisit l’élément de menu :  
  
1.  La fenêtre frame principale reçoit d’abord le message de commande.  
  
2.  La fenêtre frame MDI principale donne une chance de traiter la commande à la fenêtre enfant MDI active.  
  
3.  Le routage standard d’une fenêtre de frame enfant MDI permet sa vue de la commande avant de vérifier sa propre table des messages.  
  
4.  La vue vérifie d’abord sa propre table des messages et ne trouver aucun gestionnaire, route la commande vers son document associé.  
  
5.  Le document consulte sa table des messages et recherche un gestionnaire. La fonction de membre de ce document est appelée et le routage s’arrête.  
  
 Si le document ne comporte pas d’un gestionnaire, il est ensuite routée la commande à son modèle de document. Ensuite, la commande retourne à la vue, puis la fenêtre frame. Enfin, la fenêtre frame Vérifiez sa table des messages. Si cette vérification a échoué ainsi, la commande est acheminée vers la fenêtre frame MDI principale, puis à l’objet d’application — la destination finale des commandes non traitées.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

