---
title: Traitement des messages de notification du contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: 75b19033a31d707fcc87c1b5c824acffca725c96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441966"
---
# <a name="processing-tab-control-notification-messages"></a>Traitement des messages de notification du contrôle Tab

Comme les utilisateurs cliquent sur des onglets ou des boutons, le contrôle d’onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envoie des messages de notification à sa fenêtre parente. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur clique sur un onglet, vous souhaiterez présélection des données de contrôle sur la page avant de les afficher.

Traitez les messages WM_NOTIFY à partir du contrôle d’onglet dans votre classe d’affichage ou de la boîte de dialogue. Utilisez la fenêtre Propriétés pour créer un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) fonction de gestionnaire avec une instruction switch basée sur le message de notification est géré. Pour obtenir la liste des notifications d’un contrôle onglet peut envoyer à sa fenêtre parente, consultez le **Notifications** section de [référence de contrôle d’onglet](https://msdn.microsoft.com/library/windows/desktop/bb760548) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

