---
title: Notification de traitement des Messages dans le sélecteur de Date et heure contrôles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
dev_langs:
- C++
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 630792eb4bdd89cbe8081894c4ee026437568f3b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930762"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Traitement des messages de notification dans les contrôles de sélecteur de date et heure
Lorsque les utilisateurs interagissent avec la date et de contrôle de sélecteur de temps, le contrôle (`CDateTimeCtrl`) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de la boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur ouvre le sélecteur de date et d’heure pour afficher le contrôle month calendar incorporé, la notification DTN_DROPDOWN est envoyée.  
  
 Utilisez la fenêtre Propriétés pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous voulez implémenter.  
  
 La liste suivante décrit les différentes notifications envoyées par le contrôle de sélecteur de date et d’heure.  
  
-   DTN_DROPDOWN Notifie le parent que le contrôle month calendar incorporé est sur le point d’être affiché. Cette notification est envoyée uniquement lorsque le style DTS_UPDOWN n’a pas été défini. Pour plus d’informations sur cette notification, consultez [le contrôle Month Calendar incorporé de l’accès à](../mfc/accessing-the-embedded-month-calendar-control.md).  
  
-   DTN_CLOSEUP notifie le parent que le contrôle month calendar incorporé est sur le point d’être fermé. Cette notification est envoyée uniquement lorsque le style DTS_UPDOWN n’a pas été défini.  
  
-   DTN_DATETIMECHANGE notifie le parent a été modifiée dans le contrôle.  
  
-   DTN_FORMAT Notifie le parent que le texte est nécessaire pour être affiché dans un champ de rappel. Pour plus d’informations sur cette notification et les champs de rappel, consultez [à l’aide des champs de rappel dans une Date et d’un contrôle sélecteur d’heure](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   DTN_FORMATQUERY demande au parent de fournir la taille maximale autorisée de la chaîne qui sera affichée dans un champ de rappel. Gestion de cette notification permet le contrôle à afficher correctement la sortie à tout moment, réduire le scintillement dans l’affichage du contrôle. Pour plus d’informations sur cette notification, consultez [à l’aide des champs de rappel dans une Date et d’un contrôle sélecteur d’heure](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   DTN_USERSTRING Notifie le parent que l’utilisateur a fini de modifier le contenu du contrôle de sélecteur de date et d’heure. Cette notification est envoyée uniquement lorsque le style DTS_APPCANPARSE a été défini.  
  
-   DTN_WMKEYDOWN Notifie le parent lorsque l’utilisateur tape dans un champ de rappel. Gérer cette notification pour émuler la même réponse clavier pris en charge pour les champs non-rappel dans un contrôle de sélecteur de date et d’heure. Pour plus d’informations sur cette notification, consultez [prise en charge des champs de rappel dans un contrôle DTP](http://msdn.microsoft.com/library/windows/desktop/bb761726) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

