---
title: Envoi et réception de messages
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 95a54f3a518be19c7ae6f001e3096b825e64c0c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447396"
---
# <a name="message-sending-and-receiving"></a>Envoi et réception de messages

Prendre en compte la partie émettrice du processus et la façon dont le framework répond.

La plupart des messages résultent de l’interaction utilisateur avec le programme. Commandes sont générées par des clics de souris dans les éléments de menu ou des boutons de barre d’outils ou en séquences de touches accélérateur. L’utilisateur génère également des messages Windows, par exemple, de déplacement ou redimensionnement d’une fenêtre. Autres messages Windows sont envoyés lorsque des événements tels que le démarrage du programme ou l’arrêt se produisent, comme windows Obtient ou perdent le focus et ainsi de suite. Messages de notification de contrôle sont générés par les clics de souris ou d’autres interactions utilisateur avec un contrôle, tel qu’un contrôle de bouton ou zone de liste dans une boîte de dialogue.

Le `Run` fonction membre de classe `CWinApp` récupère les messages et les envoie à la fenêtre appropriée. La plupart des messages de commande sont envoyés à la fenêtre frame principale de l’application. Le `WindowProc` prédéfinis par l’obtient de bibliothèque de classe les messages et les route différemment, selon la catégorie du message reçu.

Considérons maintenant la partie réceptrice du processus.

Le récepteur initial d’un message doit être un objet de fenêtre. Les messages Windows sont généralement gérés directement par cet objet de fenêtre. Messages de commande, provenant généralement de fenêtre frame principale de l’application, seront acheminés vers la chaîne de la cible de commande décrite dans [routage des commandes](../mfc/command-routing.md).

Chaque objet capable de recevoir des messages ou des commandes possède son propre message mapper qui associe un message ou une commande avec le nom de son gestionnaire.

Lorsqu’un objet cible de commande reçoit un message ou une commande, il recherche une correspondance sa table des messages. S’il trouve un gestionnaire pour le message, il appelle le gestionnaire. Pour plus d’informations sur la façon dont les tables des messages sont recherchés, consultez [comment le Framework recherches tables des messages](../mfc/how-the-framework-searches-message-maps.md). Reportez-vous à nouveau à la figure [commandes dans le Framework](../mfc/user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

