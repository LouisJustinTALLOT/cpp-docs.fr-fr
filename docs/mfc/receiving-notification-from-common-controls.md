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
ms.openlocfilehash: 9205facb5ec4e2491308020d9667a27ab8deb96b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371783"
---
# <a name="receiving-notification-from-common-controls"></a>Réception des notifications de contrôles communs

Les contrôles courants sont les fenêtres des enfants qui envoient des messages de notification à la fenêtre parente lorsque des événements, tels que l’entrée de l’utilisateur, se produisent dans le contrôle.

L’application s’appuie sur ces messages de notification pour déterminer quelle action l’utilisateur veut qu’il prenne. La plupart des contrôles courants envoient des messages de notification comme WM_NOTIFY messages. Les contrôles Windows envoient la plupart des messages de notification sous forme de messages WM_COMMAND. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) est le gestionnaire pour le message WM_NOTIFY. Comme `CWnd::OnCommand`avec , `OnNotify` la mise en `OnCmdMsg` œuvre des envois du message de notification pour le traitement dans les cartes de messages. L’entrée de carte de message pour le traitement des notifications est ON_NOTIFY. Pour plus d’informations, voir [Note technique 61: ON_NOTIFY et WM_NOTIFY Messages](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Alternativement, une classe dérivée peut gérer ses propres messages de notification à l’aide de « réflexion de message ». Pour plus d’informations, voir [Note technique 62: Réflexion de message pour les contrôles Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Récupération de la position du curseur dans un message de notification

À l’occasion, il est utile de déterminer la position actuelle du curseur lorsque certains messages de notification sont reçus par un contrôle commun. Par exemple, il serait utile de déterminer l’emplacement actuel du curseur lorsqu’un contrôle commun reçoit un message de notification NM_RCLICK.

Il ya un moyen simple `CWnd::GetCurrentMessage`d’y parvenir en appelant . Cependant, cette méthode ne récupère la position du curseur qu’au moment de l’envoi du message. Parce que le curseur peut avoir été déplacé `CWnd::GetCursorPos` depuis que le message a été envoyé, vous devez appeler pour obtenir la position de curseur actuel.

> [!NOTE]
> `CWnd::GetCurrentMessage`ne doit être appelé qu’à l’intérieur d’un gestionnaire de message.

Ajoutez le code suivant à l’organe du gestionnaire de message de notification (dans cet exemple, NM_RCLICK) :

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

À ce stade, l’emplacement du curseur de souris est stocké dans l’objet. `cursorPos`

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
