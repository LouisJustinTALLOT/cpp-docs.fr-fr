---
title: Envoi et réception de messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7ded8dd0c818b95d6f45a722bd7b8516d48ff1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347176"
---
# <a name="message-sending-and-receiving"></a>Envoi et réception de messages
Prendre en compte la partie envoi du processus et la manière dont l’infrastructure répond.  
  
 La plupart des messages résultent de l’interaction de l’utilisateur avec le programme. Commandes sont générées par des clics de souris dans les éléments de menu ou des boutons de barre d’outils ou par les séquences de touches accélérateur. L’utilisateur génère également des messages Windows, par exemple, de déplacement ou redimensionnement d’une fenêtre. Autres messages Windows sont envoyés lorsque des événements tels que le démarrage du programme ou l’arrêt se produisent, comme windows Obtient ou perdent le focus et ainsi de suite. Messages de notification de contrôle sont générés par des clics de souris ou d’autres interactions de l’utilisateur avec un contrôle, par exemple un contrôle de bouton ou la zone de liste dans une boîte de dialogue.  
  
 Le **exécuter** fonction membre de classe `CWinApp` récupère les messages et les envoie à la fenêtre appropriée. La plupart des messages de commande sont envoyés à la fenêtre frame principale de l’application. Le `WindowProc` prédéfinie, par l’Obtient de bibliothèque de classe, les messages et les route différemment, en fonction de la catégorie du message reçu.  
  
 Examinons à présent la partie réception du processus.  
  
 Le récepteur initial d’un message doit être un objet window. Messages Windows sont généralement gérés directement par l’objet fenêtre. Messages de commande, généralement d’origine dans la fenêtre frame principale de l’application, seront acheminés vers la chaîne de la cible de commande décrite dans [routage des commandes](../mfc/command-routing.md).  
  
 Chaque objet capable de recevoir des messages ou des commandes possède son propre message mapper qui associe un message ou une commande avec le nom de son gestionnaire.  
  
 Lorsqu’un objet cible de commande reçoit un message ou une commande, il recherche une correspondance sa table des messages. S’il trouve un gestionnaire pour le message, il appelle le gestionnaire. Pour plus d’informations sur la façon dont les tables des messages sont recherchés, consultez [comment le Framework recherche tables des messages](../mfc/how-the-framework-searches-message-maps.md). Reportez-vous à nouveau à la figure [commandes dans le Framework](../mfc/user-interface-objects-and-command-ids.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

