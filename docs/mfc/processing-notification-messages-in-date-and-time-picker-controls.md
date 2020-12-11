---
description: 'En savoir plus sur : traitement des messages de notification dans les contrôles de sélecteur de date et heure'
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
ms.openlocfilehash: 07ac9c4c8ba58c833591409b1f5ab405cd05ebc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154823"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Traitement des messages de notification dans les contrôles de sélecteur de date et heure

Quand les utilisateurs interagissent avec le contrôle de sélecteur de date et heure, le contrôle ( `CDateTimeCtrl` ) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur ouvre le sélecteur de date et heure pour afficher le contrôle de calendrier de mois incorporé, la notification de DTN_DROPDOWN est envoyée.

Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous souhaitez implémenter.

La liste suivante décrit les différentes notifications envoyées par le contrôle de sélecteur de date et d’heure.

- DTN_DROPDOWN avertit le parent que le contrôle de calendrier mensuel incorporé va être affiché. Cette notification est envoyée uniquement lorsque le style de DTS_UPDOWN n’a pas été défini. Pour plus d’informations sur cette notification, consultez [accès au contrôle de calendrier de mois incorporé](accessing-the-embedded-month-calendar-control.md).

- DTN_CLOSEUP avertit le parent que le contrôle de calendrier mensuel incorporé va être fermé. Cette notification est envoyée uniquement lorsque le style de DTS_UPDOWN n’a pas été défini.

- DTN_DATETIMECHANGE avertit le parent qu’une modification s’est produite dans le contrôle.

- DTN_FORMAT avertit le parent que du texte est nécessaire pour être affiché dans un champ de rappel. Pour plus d’informations sur les champs de notification et de rappel, consultez [utilisation des champs de rappel dans un contrôle de sélecteur de date et d’heure](using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_FORMATQUERY demande au parent de fournir la taille maximale autorisée de la chaîne qui s’affichera dans un champ de rappel. La gestion de cette notification permet au contrôle d’afficher correctement la sortie à tout moment, ce qui réduit le scintillement au sein de l’affichage du contrôle. Pour plus d’informations sur cette notification, consultez [utilisation des champs de rappel dans un contrôle de sélecteur de date et d’heure](using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING avertit le parent que l’utilisateur a fini de modifier le contenu du contrôle de sélecteur de date et d’heure. Cette notification est envoyée uniquement lorsque le style de DTS_APPCANPARSE a été défini.

- DTN_WMKEYDOWN Notifie le parent lorsque l’utilisateur tape un champ de rappel. Gérez cette notification pour émuler la même réponse de clavier prise en charge pour les champs de non-rappel dans un contrôle de sélecteur de date et d’heure. Pour plus d’informations sur cette notification, consultez [prise en charge des champs de rappel dans un contrôle de PAO](/windows/win32/Controls/date-and-time-picker-controls) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Contrôles](controls-mfc.md)
