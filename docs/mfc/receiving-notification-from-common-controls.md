---
title: Réception des notifications de contrôles communs
ms.date: 11/04/2016
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
ms.openlocfilehash: 73315d4a1107204bc6adc885729fdeeaeb7f98d0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298972"
---
# <a name="receiving-notification-from-common-controls"></a>Réception des notifications de contrôles communs

Les contrôles communs sont des fenêtres enfants qui envoient des messages de notification à la fenêtre parente lorsque des événements, tels que l’entrée de l’utilisateur, se produisent dans le contrôle.

L’application s’appuie sur ces messages de notification pour déterminer l’action que l’utilisateur souhaite effectuer. La plupart des contrôles courants envoient des messages de notification en tant que messages WM_NOTIFY. Les contrôles Windows envoient la plupart des messages de notification en tant que messages WM_COMMAND. [CWnd :: OnNotify](../mfc/reference/cwnd-class.md#onnotify) est le gestionnaire du message WM_NOTIFY. Comme avec `CWnd::OnCommand`, l’implémentation de `OnNotify` distribue le message de notification à `OnCmdMsg` à des fins de gestion dans les tables des messages. L’entrée de la table des messages pour gérer les notifications est ON_NOTIFY. Pour plus d’informations, consultez [Technical Note 61 : ON_NOTIFY et WM_NOTIFY messages](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Une classe dérivée peut également gérer ses propres messages de notification à l’aide de la « réflexion de message ». Pour plus d’informations, consultez la [note technique 62 : réflexion de message pour les contrôles Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Récupération de la position du curseur dans un message de notification

Il est parfois utile de déterminer la position actuelle du curseur lorsque certains messages de notification sont reçus par un contrôle commun. Par exemple, il serait utile de déterminer l’emplacement actuel du curseur lorsqu’un contrôle commun reçoit un message de notification NM_RCLICK.

Pour ce faire, il existe un moyen simple d’appeler `CWnd::GetCurrentMessage`. Toutefois, cette méthode récupère uniquement la position du curseur au moment où le message a été envoyé. Étant donné que le curseur a peut-être été déplacé depuis que le message a été envoyé, vous devez appeler `CWnd::GetCursorPos` pour obtenir la position actuelle du curseur.

> [!NOTE]
>  `CWnd::GetCurrentMessage` doit être appelé uniquement dans un gestionnaire de messages.

Ajoutez le code suivant au corps du gestionnaire de messages de notification (dans cet exemple, NM_RCLICK) :

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

À ce stade, l’emplacement du curseur de la souris est stocké dans l’objet `cursorPos`.

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
