---
title: Traitement des messages de notification dans les contrôles de liste
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 92111e3e0a4869ca06b89d2d18d38aab9f10ab7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908093"
---
# <a name="processing-notification-messages-in-list-controls"></a>Traitement des messages de notification dans les contrôles de liste

Quand les utilisateurs cliquent sur des en-têtes de colonnes, glissent des icônes, modifient des étiquettes, etc., le contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) envoie des messages de notification à sa fenêtre parente. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur clique sur un en-tête de colonne, vous souhaiterez peut-être trier les éléments en fonction du contenu de la colonne sur laquelle vous avez cliqué, comme dans Microsoft Outlook.

Traitez les messages WM_NOTIFY à partir du contrôle de liste dans votre classe d’affichage ou de boîte de dialogue. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour créer une fonction gestionnaire [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) avec une instruction switch basée sur le message de notification géré.

Pour obtenir la liste des notifications qu’un contrôle de liste peut envoyer à sa fenêtre parente, consultez [Référence du contrôle List View](/windows/win32/Controls/list-view-control-reference) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
