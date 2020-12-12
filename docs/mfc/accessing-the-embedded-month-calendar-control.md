---
description: 'En savoir plus sur : accès au contrôle de calendrier de mois incorporé'
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
ms.openlocfilehash: 35c715cdd84bd7921883db530c8cf36e8e5cf07e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169448"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Accès au contrôle Month Calendar Control incorporé

L’objet de contrôle de calendrier de mois incorporé est accessible à partir de l' `CDateTimeCtrl` objet avec un appel à la fonction membre [GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl) .

> [!NOTE]
> Le contrôle calendrier mensuel incorporé n’est utilisé que lorsque le style de sélecteur de date et d’heure n’est **DTS_UPDOWN** pas défini.

Cela est utile si vous souhaitez modifier certains attributs avant l’affichage du contrôle incorporé. Pour ce faire, gérez le **DTN_DROPDOWN** notification, récupérez le contrôle Month Calendar (à l’aide de [CDateTimeCtrl :: GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)) et apportez vos modifications. Malheureusement, le contrôle Month Calendar n’est pas persistant.

En d’autres termes, lorsque l’utilisateur demande l’affichage du contrôle Month Calendar, un nouveau contrôle Month Calendar est créé (avant la notification **DTN_DROPDOWN** ). Le contrôle est détruit (après l' **DTN_CLOSEUP** notification) quand l’utilisateur l’ignore. Cela signifie que tous les attributs que vous modifiez, avant l’affichage du contrôle incorporé, sont perdus lorsque le contrôle incorporé est fermé.

L’exemple suivant illustre cette procédure, à l’aide d’un gestionnaire pour la notification **DTN_DROPDOWN** . Le code modifie la couleur d’arrière-plan du contrôle Month Calendar, avec un appel à [SetMonthCalColor](reference/cdatetimectrl-class.md#setmonthcalcolor), en gris. Le code se présente comme suit :

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Comme indiqué précédemment, toutes les modifications apportées aux propriétés du contrôle Month Calendar sont perdues, à deux exceptions près, lorsque le contrôle incorporé est fermé. La première exception, les couleurs du contrôle Month Calendar, ont déjà été abordées. La deuxième exception correspond à la police utilisée par le contrôle Month Calendar. Vous pouvez modifier la police par défaut en effectuant un appel à [CDateTimeCtrl :: SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont), en passant le handle d’une police existante. L’exemple suivant (où `m_dtPicker` est l’objet de contrôle de date et d’heure) illustre une méthode possible :

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Une fois la police modifiée, avec un appel à `CDateTimeCtrl::SetMonthCalFont` , la nouvelle police est stockée et utilisée la prochaine fois qu’un calendrier mensuel sera affiché.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Contrôles](controls-mfc.md)
