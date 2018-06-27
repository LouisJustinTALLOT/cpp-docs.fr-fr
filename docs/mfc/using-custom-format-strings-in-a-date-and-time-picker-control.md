---
title: À l’aide de chaînes de Format personnalisées dans une Date Time Picker contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aeb6c02041a4ba90f9721f23a1397e17a4cdf81
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955756"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Utilisation de chaînes de format personnalisées dans un contrôle de sélecteur de date et heure
Par défaut, les contrôles date time picker fournissent que trois types (chaque format correspondant à un style unique) de format pour l’affichage de la date actuelle ou l’heure :  
  
-   **DTS_LONGDATEFORMAT** affiche la date au format long, sortie similaire à « Mercredi 3 janvier 2000 ».  
  
-   **DTS_SHORTDATEFORMAT** affiche la date au format court, sortie similaire à « 3/1/00 ».  
  
-   **DTS_TIMEFORMAT** affiche l’heure au format long, sortie similaire à « 5:31:42 PM ».  
  
 Toutefois, vous pouvez personnaliser l’apparence de la date ou l’heure à l’aide d’une chaîne de format personnalisée. La chaîne personnalisée est constituée de caractères de format existant, autres caractères ou une combinaison des deux. Une fois que la chaîne personnalisée est construite, effectuez un appel à [CDateTimeCtrl::SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) en passant votre chaîne personnalisée. Le contrôle de sélecteur de date et d’heure affiche ensuite la valeur actuelle à l’aide de votre chaîne de format personnalisée.  
  
 L’exemple de code suivant (où *m_dtPicker* est la `CDateTimeCtrl` objet) illustre une solution possible :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 En plus des chaînes de format personnalisées, date time picker contrôle également la prise en charge [champs de rappel](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

