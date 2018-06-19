---
title: Contrôle de calendrier mensuel incorporé de l’accès à | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfbc9ce7b99efc1f8d99f5735c16c252ff613c59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332125"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Accès au contrôle Month Calendar Control incorporé
L’objet de contrôle de calendrier mensuel incorporé est accessible à partir de la `CDateTimeCtrl` objet avec un appel à la [fonction membre GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) fonction membre.  
  
> [!NOTE]
>  Le contrôle month calendar incorporé est uniquement utilisé lorsque le contrôle de sélecteur de date et heure n’a pas la **DTS_UPDOWN** ensemble de style.  
  
 Cela est utile si vous souhaitez modifier certains attributs avant l’affichage de contrôle incorporé. Pour ce faire, vous devez gérer le **DTN_DROPDOWN** notification, récupérer le contrôle month calendar (à l’aide de [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) et apportez vos modifications. Malheureusement, le contrôle month calendar n’est pas persistant.  
  
 En d’autres termes, lorsque l’utilisateur demande l’affichage du contrôle month calendar, un nouveau contrôle est créé (avant la **DTN_DROPDOWN** notification). Le contrôle est détruit (après la **DTN_CLOSEUP** notification) lorsque ignoré par l’utilisateur. Cela signifie que tous les attributs que vous modifiez, avant l’affichage de contrôle incorporé, sont perdues lorsque le contrôle incorporé est ignoré.  
  
 L’exemple suivant illustre cette procédure, à l’aide d’un gestionnaire pour le **DTN_DROPDOWN** notification. Le code modifie la couleur d’arrière-plan du contrôle month calendar, avec un appel à [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), gris. Le code est comme suit :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 Comme indiqué précédemment, toutes les modifications apportées aux propriétés du contrôle month calendar sont perdues, à deux exceptions près, lorsque le contrôle incorporé est ignoré. La première exception, les couleurs du contrôle month calendar a déjà été traitée. La seconde exception est la police utilisée par le contrôle month calendar. Vous pouvez modifier la police par défaut en effectuant un appel à [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), en passant le handle d’une police existante. L’exemple suivant (où `m_dtPicker` est l’objet de contrôle de date et heure) illustre une méthode possible :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 Une fois que la police a été modifiée par un appel à `CDateTimeCtrl::SetMonthCalFont`, la nouvelle police est stockée et utilisée de la prochaine fois qu’un calendrier du mois doit être affichée.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

