---
title: Traitement des Messages de Notification dans les mois les contrôles de calendrier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce9906a738ed6c577f46d2919a5cdac80b877110
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930987"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Traitement des messages de notification dans les contrôles de calendrier mensuel
Lorsque les utilisateurs interagissent avec le contrôle month calendar (en sélectionnant des dates et/ou affichant un autre mois), le contrôle (`CMonthCalCtrl`) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de la boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur sélectionne un nouveau mois à afficher, vous pouvez fournir un ensemble de dates doit être mis en évidence.  
  
 Utilisez la fenêtre Propriétés pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous voulez implémenter.  
  
 La liste suivante décrit les différentes notifications envoyées par le contrôle month calendar.  
  
-   MCN_GETDAYSTATE demande des informations sur les jours doivent être affichés en gras. Pour plus d’informations sur la gestion de cette notification, consultez [définir l’état de jour d’un contrôle Month Calendar](../mfc/setting-the-day-state-of-a-month-calendar-control.md).  
  
-   MCN_SELCHANGE notifie le parent que la date sélectionnée ou la plage de la date a changé.  
  
-   MCN_SELECT Notifie le parent qu’une sélection de date explicite a été effectuée.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

