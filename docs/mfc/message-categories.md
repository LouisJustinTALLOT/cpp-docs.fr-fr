---
title: Catégories de message | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d0e4710c74c12bf62cd19df6a053aea9ac35eaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348447"
---
# <a name="message-categories"></a>Catégories de messages
Quels types de messages écrivez-vous des gestionnaires pour il existe trois catégories principales :  
  
1.  messages Windows  
  
     Cela inclut principalement des messages commençant par le **WM_** préfixe, à l’exception de **WM_COMMAND**. Les messages Windows sont traités par les fenêtres et les vues. Ces messages peuvent avoir des paramètres qui permettent de déterminer comment traiter le message.  
  
2.  Notifications de contrôle  
  
     Cela inclut les **WM_COMMAND** des messages de notification à partir de contrôles et autres fenêtres enfants vers les fenêtres parents. Par exemple, un contrôle d’édition envoie à son parent un **WM_COMMAND** message contenant le **EN_CHANGE** code de notification de contrôle lorsque l’utilisateur a effectué une action qui peut avoir modifié le texte du contrôle d’édition. Le gestionnaire de la fenêtre du message répond au message de notification d'une certaine façon appropriée, comme récupérer le texte du contrôle.  
  
     Le framework achemine les messages de notification de contrôle comme les autres **WM_** messages. Une exception, toutefois, est la **BN_CLICKED** message de notification de contrôle envoyé par les boutons lorsque l’utilisateur clique dessus. Ce message est traité en particulier en tant que message de commande et routé comme les autres commandes.  
  
3.  Messages de commande  
  
     Cela inclut les **WM_COMMAND** des messages de notification à partir des objets d’interface utilisateur : menus, boutons de barre d’outils et touches accélérateur. Le framework traite les commandes différemment des autres messages, et elles peuvent être gérées par des types d’objets, comme expliqué dans [cibles de la commande](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Messages Windows et les Messages de Notification de contrôle  
 Les messages des catégories 1 et 2 (messages et notifications de contrôle Windows) sont traités par Windows : objets de classes dérivées de la classe `CWnd`. Cela inclut `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, et vos propres classes dérivées des classes de base. De tels objets encapsulent `HWND`, un descripteur de la fenêtre Windows.  
  
##  <a name="_core_command_messages"></a> Messages de commande  
 Les messages de la catégorie 3 (les commandes) peuvent être gérés par une plus grande variété d'objets : documents, modèles de document et l'objet d'application lui-même en plus des fenêtres et des vues. Lorsqu'une commande affecte directement un certain objet particulier, il est logique d'avoir ce handle d'objet de la commande. Par exemple, la commande Ouvrir dans le menu Fichier est logiquement associée à l'application : l'application ouvre un document spécifié en acceptant la commande. Donc le gestionnaire de la commande Ouvrir est une fonction membre de la classe d'application. Pour plus d’informations sur les commandes et comment ils sont acheminés vers les objets, consultez [comment le Framework appelle un gestionnaire](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

