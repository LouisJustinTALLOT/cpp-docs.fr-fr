---
title: 'Temps écoulé : Les Classes à usage général | Documents Microsoft'
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
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff7ef11bb20124a05e2e85c408ce27de8f982546
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354264"
---
# <a name="elapsed-time-general-purpose-classes"></a>Temps écoulé : Les Classes à usage général
La procédure suivante montre comment calculer la différence entre deux `CTime` objets et obtenir un `CTimeSpan` résultat.  
  
#### <a name="to-calculate-elapsed-time"></a>Pour calculer le temps écoulé  
  
1.  Utilisez le `CTime` et `CTimeSpan` objets pour calculer le temps écoulé, comme suit :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     Une fois que vous avez calculée `elapsedTime`, vous pouvez utiliser les fonctions membres de `CTimeSpan` pour extraire les composants de la valeur de temps écoulé.  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure : classes à usage général](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

