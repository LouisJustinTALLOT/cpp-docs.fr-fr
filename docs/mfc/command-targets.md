---
title: Cibles de commande | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbcfa1042a8430c704bad93e4bc0ce5655b5921
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341295"
---
# <a name="command-targets"></a>Cibles de la commande
La figure [commandes dans le Framework](../mfc/user-interface-objects-and-command-ids.md) affiche la connexion entre un objet de l’interface utilisateur, comme un élément de menu et la fonction de gestionnaire, l’infrastructure appelle pour exécuter la commande qui en résulte quand l’objet est sélectionné.  
  
 Windows envoie les messages qui ne sont pas des messages de commande directement à une fenêtre dont le gestionnaire pour le message est ensuite appelé. Toutefois, l’infrastructure achemine les commandes à un nombre d’objets candidats, appelés « cibles de la commande » : dont appelle normalement un gestionnaire pour la commande. Les fonctions de gestionnaire fonctionnent de manière identique pour les commandes et les messages Windows standard, mais les mécanismes par lesquels ils sont appelés sont différents, comme expliqué dans [comment le Framework appelle un gestionnaire](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

