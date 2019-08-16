---
title: Gestion et mappage des messages
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 0321d98d8b92af0b80259bc49e84e69b987577a4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508240"
---
# <a name="message-handling-and-mapping"></a>Gestion et mappage des messages

Cette famille d’articles décrit comment les messages et les commandes sont traités par l’infrastructure MFC et comment les connecter à leurs fonctions de gestionnaire.

Dans les programmes traditionnels pour Windows, les messages Windows sont gérés dans une instruction switch volumineuse dans une procédure de fenêtre. MFC utilise plutôt des [tables de messages](../mfc/message-categories.md) pour mapper des messages directs à des fonctions membres de classe distinctes. Les tables des messages sont plus efficaces que les fonctions virtuelles à cet effet, et elles permettent aux messages d’être C++ gérés par l’objet le plus approprié (application, document, vue, etc.). Vous pouvez mapper un message unique ou une plage de messages, ID de commande ou ID de contrôle.

Les messages WM_COMMAND, généralement générés par des menus, des boutons de barre d’outils ou des accélérateurs, utilisent également le mécanisme de table des messages. MFC définit un [routage](../mfc/command-routing.md) standard des messages de commande entre l’application, la fenêtre frame, la vue et les documents actifs de votre programme. Vous pouvez remplacer ce routage si nécessaire.

Les tables des messages fournissent également un moyen de mettre à jour les objets de l’interface utilisateur (tels que les menus et les boutons de la barre d’outils), en les activant ou en les désactivant en fonction du contexte actuel.

Pour obtenir des informations générales sur les messages et les files d’attente de messages dans Windows, consultez [messages et files d’attente](/windows/win32/winmsg/messages-and-message-queues) de messages dans le SDK Windows.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

- [Comment le Framework appelle un gestionnaire de messages](../mfc/how-the-framework-calls-a-handler.md)

- [Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)

- [Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)

- [Mappage des messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)

- [Comment afficher des informations de commande dans la barre d’État](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Mise à jour dynamique des objets de l’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)

- [Guide pratique pour Créer une table des messages pour une classe de modèle](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CWnd, classe](../mfc/reference/cwnd-class.md)<br/>
[CCmdTarget, classe](../mfc/reference/ccmdtarget-class.md)
