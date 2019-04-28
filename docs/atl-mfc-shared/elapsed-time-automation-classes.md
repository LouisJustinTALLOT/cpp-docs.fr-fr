---
title: 'Temps écoulé : Classes Automation'
ms.date: 11/04/2016
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
ms.openlocfilehash: d6a77d57a88166354fcb222c0da09690426108e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235785"
---
# <a name="elapsed-time-automation-classes"></a>Temps écoulé : Classes Automation

Cette procédure montre comment calculer la différence entre deux `CTime` objets et obtenez un `CTimeSpan` résultat.

## <a name="to-calculate-elapsed-time"></a>Pour calculer le temps écoulé

1. Créez deux `COleDateTime` objets.

1. Définissez un de la `COleDateTime` objets à l’heure actuelle.

1. Effectuer une tâche fastidieuse.

1. Définir l’autre `COleDateTime` objet à l’heure actuelle.

1. Prendre la différence entre les deux heures.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Date et heure : Prise en charge d’Automation](../atl-mfc-shared/date-and-time-automation-support.md)
