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
ms.openlocfilehash: 4da2fce68c1b6fd3827bc8b5d2a40dea5e5f117c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626171"
---
# <a name="message-sending-and-receiving"></a>Envoi et réception de messages

Considérez la partie envoi du processus et la manière dont le Framework répond.

La plupart des messages résultent de l’interaction de l’utilisateur avec le programme. Les commandes sont générées par des clics de souris dans des éléments de menu ou des boutons de barre d’outils ou par touches d’accélérateur. L’utilisateur génère également des messages Windows, par exemple, en déplaçant ou en redimensionnant une fenêtre. D’autres messages Windows sont envoyés lorsque des événements tels que le démarrage ou l’arrêt du programme se produisent, lorsque Windows obtient ou perd le focus, et ainsi de suite. Les messages de notification de contrôle sont générés par des clics de souris ou d’autres interactions de l’utilisateur avec un contrôle, tel qu’un bouton ou un contrôle de zone de liste dans une boîte de dialogue.

La `Run` fonction membre de la classe `CWinApp` récupère les messages et les distribue à la fenêtre appropriée. La plupart des messages de commande sont envoyés à la fenêtre frame principale de l’application. Le `WindowProc` prédéfini par la bibliothèque de classes obtient les messages et les achemine différemment, en fonction de la catégorie de message reçue.

Considérons maintenant la partie réception du processus.

Le destinataire initial d’un message doit être un objet Window. Les messages Windows sont généralement gérés directement par cet objet Window. Les messages de commande, généralement en provenance de la fenêtre frame principale de l’application, sont acheminés vers la chaîne de la cible de commande décrite dans [routage des commandes](command-routing.md).

Chaque objet capable de recevoir des messages ou des commandes possède sa propre table des messages qui associe un message ou une commande au nom de son gestionnaire.

Lorsqu’un objet cible de commande reçoit un message ou une commande, il recherche une correspondance dans la table des messages. S’il trouve un gestionnaire pour le message, il appelle le gestionnaire. Pour plus d’informations sur la recherche de tables de messages, consultez [la rubrique Comment le Framework recherche les tables des messages](how-the-framework-searches-message-maps.md). Reportez-vous aux [commandes de figure dans le Framework](user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](how-the-framework-calls-a-handler.md)
