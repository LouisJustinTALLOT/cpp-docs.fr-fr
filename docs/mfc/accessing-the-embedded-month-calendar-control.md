---
title: Accès au contrôle Month Calendar Control incorporé
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354184"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Accès au contrôle Month Calendar Control incorporé

L’objet de contrôle de calendrier `CDateTimeCtrl` de mois intégré peut être consulté à partir de l’objet avec un appel à la fonction membre [GetMonthCalCtrl.](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)

> [!NOTE]
> Le contrôle du calendrier des mois intégré n’est utilisé que lorsque le contrôle du cueilleur de dates et d’heure n’a pas **l’ensemble de** style DTS_UPDOWN.

Ceci est utile si vous souhaitez modifier certains attributs avant que le contrôle intégré ne soit affiché. Pour ce faire, gérez la notification **DTN_DROPDOWN,** récupérez le contrôle du calendrier du mois (à l’aide [de CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)), et effectuez vos modifications. Malheureusement, le contrôle du calendrier des mois n’est pas persistant.

En d’autres termes, lorsque l’utilisateur demande l’affichage du contrôle du calendrier du mois, un nouveau contrôle de calendrier de mois est créé (avant la notification **DTN_DROPDOWN).** Le contrôle est détruit (après la notification **DTN_CLOSEUP)** lorsqu’il est rejeté par l’utilisateur. Cela signifie que tous les attributs que vous modifiez, avant que le contrôle intégré est affiché, sont perdus lorsque le contrôle intégré est rejeté.

L’exemple suivant montre cette procédure, à l’aide d’un gestionnaire pour la **notification DTN_DROPDOWN.** Le code modifie la couleur de fond du contrôle du calendrier du mois, avec un appel à [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), en gris. Le code est le suivant :

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Comme indiqué précédemment, toutes les modifications apportées aux propriétés du contrôle du calendrier du mois sont perdues, à deux exceptions près, lorsque le contrôle intégré est rejeté. La première exception, les couleurs du contrôle du calendrier du mois, a déjà été discutée. La deuxième exception est la police utilisée par le contrôle du calendrier du mois. Vous pouvez modifier la police par défaut en effectuant un appel à [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), en passant la poignée d’une police existante. L’exemple suivant `m_dtPicker` (où est l’objet de contrôle de la date et de l’heure) montre une méthode possible :

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Une fois que la police a `CDateTimeCtrl::SetMonthCalFont`été modifiée, avec un appel à , la nouvelle police est stockée et utilisée la prochaine fois qu’un calendrier de mois doit être affiché.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
