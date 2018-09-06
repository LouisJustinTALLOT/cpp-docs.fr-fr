---
title: 'Temps écoulé : Classes d’automatisation | Microsoft Docs'
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
ms.openlocfilehash: dcde08e8ffdb30f9ebf0ae7577bf836e84513a07
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751675"
---
# <a name="elapsed-time-automation-classes"></a>Temps écoulé : Classes d’automatisation

Cette procédure montre comment calculer la différence entre deux `CTime` objets et obtenez un `CTimeSpan` résultat.

#### <a name="to-calculate-elapsed-time"></a>Pour calculer le temps écoulé

1. Créez deux `COleDateTime` objets.

2. Définissez un de la `COleDateTime` objets à l’heure actuelle.

3. Effectuer une tâche fastidieuse.

4. Définir l’autre `COleDateTime` objet à l’heure actuelle.

5. Prendre la différence entre les deux heures.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Date et heure : prise en charge d’Automation](../atl-mfc-shared/date-and-time-automation-support.md)

