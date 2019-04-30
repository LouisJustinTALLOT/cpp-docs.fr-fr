---
title: Traitement des messages de notification dans les contrôles de sélecteur de date et heure
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: ce84863744629d30248f94b94448d776177f9841
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339568"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Traitement des messages de notification dans les contrôles de sélecteur de date et heure

Quand les utilisateurs interagissent avec la date et le contrôle de sélecteur de temps, le contrôle (`CDateTimeCtrl`) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de la boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur ouvre le sélecteur de date et d’heure pour afficher le contrôle de calendrier mensuel incorporé, la notification DTN_DROPDOWN est envoyée.

Utilisez la fenêtre Propriétés pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous voulez implémenter.

La liste suivante décrit les différentes notifications envoyées par le contrôle de sélecteur de date et d’heure.

- DTN_DROPDOWN Notifie le parent que le contrôle month calendar incorporé est sur le point d’être affiché. Cette notification est envoyée uniquement lorsque le style DTS_UPDOWN n’a pas été défini. Pour plus d’informations sur cette notification, consultez [contrôle Month Calendar incorporé de l’accès à](../mfc/accessing-the-embedded-month-calendar-control.md).

- DTN_CLOSEUP notifie le parent que le contrôle month calendar incorporé est sur le point d’être fermé. Cette notification est envoyée uniquement lorsque le style DTS_UPDOWN n’a pas été défini.

- DTN_DATETIMECHANGE notifie le parent qu’une modification a eu lieu dans le contrôle.

- DTN_FORMAT Notifie le parent que le texte est nécessaire pour être affiché dans un champ de rappel. Pour plus d’informations sur cette notification et les champs de rappel, consultez [à l’aide des champs de rappel dans une Date et d’un contrôle de sélecteur de temps](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_FORMATQUERY demande au parent de fournir la taille maximale autorisée de la chaîne qui sera affichée dans un champ de rappel. La gestion de cette notification permet le contrôle pour afficher correctement la sortie à tout moment, réduire le scintillement dans l’affichage du contrôle. Pour plus d’informations sur cette notification, consultez [à l’aide des champs de rappel dans une Date et d’un contrôle de sélecteur de temps](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING Notifie le parent que l’utilisateur a fini de modifier le contenu du contrôle de sélecteur de date et d’heure. Cette notification est envoyée uniquement lorsque le style DTS_APPCANPARSE a été défini.

- DTN_WMKEYDOWN Notifie le parent lorsque l’utilisateur tape dans un champ de rappel. Gérer cette notification pour émuler la même réponse clavier pris en charge pour les champs non rappel dans un contrôle de sélecteur de date et d’heure. Pour plus d’informations sur cette notification, consultez [prenant en charge les champs de rappel dans un contrôle DTP](/windows/desktop/Controls/date-and-time-picker-controls) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
