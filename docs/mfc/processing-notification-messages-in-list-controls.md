---
title: Traitement des messages de notification dans les contrôles de liste
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 427abe5259334588b566656abd70acf22b923809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490088"
---
# <a name="processing-notification-messages-in-list-controls"></a>Traitement des messages de notification dans les contrôles de liste

Comme les utilisateurs cliquent sur les en-têtes de colonne, faites glisser les icônes, modifier des étiquettes et ainsi de suite, le contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) envoie des messages de notification à sa fenêtre parente. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur clique sur un en-tête de colonne, vous souhaiterez trier les éléments en fonction du contenu de cette colonne, comme dans Microsoft Outlook.

Traitez les messages WM_NOTIFY à partir du contrôle de liste dans votre classe d’affichage ou de la boîte de dialogue. Utilisez la fenêtre Propriétés pour créer un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) fonction de gestionnaire avec une instruction switch basée sur le message de notification est géré.

Pour obtenir la liste des notifications d’un contrôle de liste peut envoyer à sa fenêtre parente, consultez [référence de contrôle d’affichage liste](/windows/desktop/Controls/list-view-control-reference) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

