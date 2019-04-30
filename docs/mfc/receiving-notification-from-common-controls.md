---
title: Réception des notifications de contrôles communs
ms.date: 11/04/2016
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
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
ms.openlocfilehash: fb923374866aa8348f9b895c9b97915817564883
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399861"
---
# <a name="receiving-notification-from-common-controls"></a>Réception des notifications de contrôles communs

Contrôles communs sont des fenêtres enfants qui envoient des messages de notification à la fenêtre parente lorsque des événements, tels que les entrées de l’utilisateur, qui se produisent dans le contrôle.

L’application s’appuie sur ces messages de notification pour déterminer quelle action l’utilisateur souhaite effectuer. Contrôles les plus courants envoient des messages de notification en tant que messages WM_NOTIFY. Les contrôles de Windows envoient la plupart des messages de notification en tant que messages WM_COMMAND. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) est le gestionnaire pour le message WM_NOTIFY. Comme avec `CWnd::OnCommand`, l’implémentation de `OnNotify` distribue le message de notification à `OnCmdMsg` pour une gestion dans les tables des messages. L’entrée de table des messages pour la gestion des notifications est ON_NOTIFY. Pour plus d’informations, consultez [Technical Note 61 : Messages ON_NOTIFY et WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Ou bien, une classe dérivée peut gérer ses propres messages de notification à l’aide de « réflexion de message ». Pour plus d’informations, consultez [Technical Note 62 : Message de réflexion pour les contrôles Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Récupération de la Position du curseur dans un Message de Notification

Parfois, il est utile déterminer la position actuelle du curseur lorsque certains messages de notification sont reçus par un contrôle commun. Par exemple, il serait utile de déterminer l’emplacement du curseur lorsqu’un contrôle commun reçoit un message de notification NM_RCLICK.

Il existe un moyen simple pour effectuer cette opération en appelant `CWnd::GetCurrentMessage`. Toutefois, cette méthode extrait uniquement la position du curseur au moment où que le message a été envoyé. Étant donné que le curseur a peut-être été déplacé dans la mesure où le message a été envoyé, vous devez appeler `CWnd::GetCursorPos` pour obtenir la position actuelle du curseur.

> [!NOTE]
>  `CWnd::GetCurrentMessage` doit uniquement être appelée dans un gestionnaire de messages.

Ajoutez le code suivant au corps du Gestionnaire de messages de notification (dans cet exemple, il s’agit de NM_RCLICK) :

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

À ce stade, l’emplacement du curseur de la souris est stocké dans le `cursorPos` objet.

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
