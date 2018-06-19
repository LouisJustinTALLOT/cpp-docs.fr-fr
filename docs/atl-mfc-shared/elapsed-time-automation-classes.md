---
title: 'Temps écoulé : Classes Automation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1abf6274137ae67b159ad43612d24020a0d14e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354966"
---
# <a name="elapsed-time-automation-classes"></a>Temps écoulé : Les Classes Automation
Cette procédure montre comment calculer la différence entre deux `CTime` objets et obtenir un `CTimeSpan` résultat.  
  
#### <a name="to-calculate-elapsed-time"></a>Pour calculer le temps écoulé  
  
1.  Créez deux `COleDateTime` objets.  
  
2.  Définissez l’une de le `COleDateTime` objets à l’heure actuelle.  
  
3.  Exécution d’une tâche de longue durée.  
  
4.  Définir les autres `COleDateTime` objet à l’heure actuelle.  
  
5.  Prendre la différence entre les deux heures.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure : prise en charge d’Automation](../atl-mfc-shared/date-and-time-automation-support.md)

