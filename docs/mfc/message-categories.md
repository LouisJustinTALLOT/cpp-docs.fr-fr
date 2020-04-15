---
title: Catégories de messages
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364756"
---
# <a name="message-categories"></a>Catégories de messages

Quels types de messages écrivez-vous des gestionnaires pour Il ya trois catégories principales:

1. messages Windows

   Cela comprend principalement les messages commençant par le préfixe **WM_,** à l’exception de WM_COMMAND. Les messages Windows sont traités par les fenêtres et les vues. Ces messages peuvent avoir des paramètres qui permettent de déterminer comment traiter le message.

1. Notifications de contrôle

   Cela inclut des messages de notification WM_COMMAND issus des contrôles et d'autres fenêtres enfants vers les fenêtres parents. Par exemple, un contrôle d'édition envoie à son parent un message WM_COMMAND contenant le code de contrôle notification EN_CHANGE lorsque l'utilisateur a pris une mesure qui peut avoir modifié le texte du contrôle d'édition. Le gestionnaire de la fenêtre du message répond au message de notification d'une certaine façon appropriée, comme récupérer le texte du contrôle.

   Le cadre achemine les messages de contrôle-notification comme les autres **messages WM_.** Une exception ; toutefois, concerne le message de notification de contrôle BN_CLICKED envoyé par les boutons lorsque l'utilisateur clique sur dessus. Ce message est traité en particulier en tant que message de commande et routé comme les autres commandes.

1. Messages de commande

   Cela inclut les messages de notification WM_COMMAND issus des objets d'interface utilisateur : menus, boutons de la barre d'outils et touches accélérateur. Les processus-cadres commandent différemment des autres messages, et ils peuvent être manipulés par plus de types d’objets, comme expliqué dans [Command Targets](../mfc/command-targets.md).

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Messages Windows et Messages de contrôle-notification

Les messages des catégories 1 et 2 (messages et notifications de contrôle Windows) sont traités par Windows : objets de classes dérivées de la classe `CWnd`. Cela inclut `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, et vos propres classes dérivées des classes de base. De tels objets encapsulent `HWND`, un descripteur de la fenêtre Windows.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Messages de commande

Les messages de la catégorie 3 (les commandes) peuvent être gérés par une plus grande variété d'objets : documents, modèles de document et l'objet d'application lui-même en plus des fenêtres et des vues. Lorsqu'une commande affecte directement un certain objet particulier, il est logique d'avoir ce handle d'objet de la commande. Par exemple, la commande Ouvrir dans le menu Fichier est logiquement associée à l'application : l'application ouvre un document spécifié en acceptant la commande. Donc le gestionnaire de la commande Ouvrir est une fonction membre de la classe d'application. Pour en savoir plus sur les commandes et la façon dont ils sont acheminés vers des objets, voir [Comment le cadre appelle un gestionnaire](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)
