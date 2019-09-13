---
title: Traitement des messages de notification dans les contrôles de calendrier mensuel
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908079"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Traitement des messages de notification dans les contrôles de calendrier mensuel

Quand les utilisateurs interagissent avec le contrôle Month Calendar (en sélectionnant des dates et/ou en affichant un mois`CMonthCalCtrl`différent), le contrôle () envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur sélectionne un nouveau mois à afficher, vous pouvez fournir un ensemble de dates à mettre en évidence.

Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous souhaitez implémenter.

La liste suivante décrit les différentes notifications envoyées par le contrôle Month Calendar.

- MCN_GETDAYSTATE demande des informations sur les jours qui doivent s’afficher en gras. Pour plus d’informations sur la gestion de cette notification, consultez [définition de l’état du jour d’un contrôle Month Calendar](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- MCN_SELCHANGE avertit le parent que la date ou la plage sélectionnée de la date a changé.

- MCN_SELECT avertit le parent qu’une sélection de date explicite a été effectuée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
