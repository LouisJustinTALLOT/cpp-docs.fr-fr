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
ms.openlocfilehash: 3dbf50080bea59c4df4a9c92a135a65b093f7674
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511928"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Traitement des messages de notification dans les contrôles de calendrier mensuel

Quand les utilisateurs interagissent avec le contrôle month calendar (sélection des dates et/ou affichant un autre mois), le contrôle (`CMonthCalCtrl`) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de la boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur sélectionne un nouveau mois à afficher, vous pouvez fournir un ensemble de dates doit être mis en évidence.

Utilisez la fenêtre Propriétés pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous voulez implémenter.

La liste suivante décrit les différentes notifications envoyées par le contrôle month calendar.

- MCN_GETDAYSTATE demande des informations sur les jours doivent être affichés en gras. Pour plus d’informations sur la gestion de cette notification, consultez [définissant l’état du jour d’un contrôle Month Calendar](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- MCN_SELCHANGE notifie le parent que la date sélectionnée ou la plage de la date a été modifié.

- MCN_SELECT Notifie le parent qu’une sélection de date explicite a été effectuée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

